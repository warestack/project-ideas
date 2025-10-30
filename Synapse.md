### Synapse: Redis for LLM Memory

**Inspiration**

A company deploys an AI customer support agent system.

It has:

- `Agent A`: Intake agent → reads customer messages, classifies intent.
- `Agent B`: Knowledge agent → searches company docs for answers.
- `Agent C`: Resolution agent → drafts replies and tracks follow-ups.

They handle thousands of tickets daily, often from returning customers. Each agent is stateless, they don’t “remember” what happened yesterday.

**Reality**

Each agent call is isolated. There’s no shared state beyond a central database of tickets.

**Example**

```tex
Customer: "I still haven't received my refund."
```

1. `Agent A` classifies it: `refund inquiry`. But it doesn’t remember that this same customer already had 3 refund interactions last week.

2. `Agent B` fetches refund policy docs again (re-runs the same search). That's costly and redundant, thousands of similar lookups happen daily.

3. `Agent C` writes: `Please provide your order number`, because it can’t recall that the user already sent it in a previous thread. 

**Solution**

Now we plug in a semantic memory layer shared across agents. Each agent reads/writes facts into this store in near-real-time.

1. `Agent A` writes semantic memory into the `SynapseDB`.

```python
memory.write("user:4321", {
  "content": "Refund requested for order #1458 last week",
  "salience": 0.9,
  "ts": "2025-10-24T10:00:00Z"
})
```

2. `Agent B` reuses past reasoning. When `Agent B` receives the new query:

```python
context = memory.query("user:4321 refund status")
```

Memory returns semantically similar entries:

```python
[
  "Customer refund for order #1458 initiated on 10/20",
  "Refund confirmation email sent 10/21"
]
```

`Agent B` immediately concludes: `Refund already processed → customer following up.`

No need to re-run search over documentation or ask for order details.

3. `Agent C` adds an update. After resolving, it appends:

```python
memory.append("user:4321", "Refund confirmed delivered on 10/28.")
```

4. Next time the customer says:

```
Why is my refund taking so long?”
```

All agents can instantly “remember” past interactions, without re-querying databases or rerunning prompts.

| Before                               | After                                                |
| ------------------------------------ | ---------------------------------------------------- |
| Agents forgot user context           | Agents recall prior summaries instantly              |
| Repeated LLM calls for the same info | Cached semantic context → 70–90% fewer LLM tokens    |
| Fragmented reasoning                 | Shared, real-time semantic memory graph              |
| No auditability                      | Memory log shows exactly what each agent knew & when |
| Poor UX                              | Feels like one coherent, continuous assistant        |

![memento](assets/memento.jpg)

🎬 From [*Memento*](https://www.imdb.com/title/tt0209144/).

**Solution**

A low-latency, in-memory semantic state store purpose-built for LLM/agent workloads:

- Hybrid data model: `KV/JSON` for facts, `VECTOR` for embeddings, and `STREAM` for temporal events, all namespaced per agent/team/tenant.
- Semantic retrieval: HNSW-based ANN with metadata filters + optional reranking—query by meaning, not just keys.
- Temporal versioning: Time-travel reads (e.g., `memory as of 2025-10-24T10:00Z`) and append-only event streams per entity/session.
- Semantic eviction: Forget using *salience* (recency × access × downstream impact), not only TTL/LRU.
- Observability: Memory lineage + OpenTelemetry traces show which memories influenced which answers.
- Clustered & safe: Raft replication, shard-local leaders, mTLS, per-tenant quotas.

#### Minimal tech plan / stack

- Runtime & API: `FastAPI` + `uvicorn` (`asyncio` / `uvloop`) — async HTTP JSON service exposing `kv`, `vector`, `stream`, `hybrid` endpoints.
- Storage: In-memory Python dicts for hot data + [`aiosqlite`](https://github.com/omnilib/aiosqlite) (WAL mode) for durable snapshots.
- Vector Search: [`hnswlib`](https://github.com/nmslib/hnswlib) (cosine ANN) + lightweight Python metadata filters; caller provides embeddings.
- Eviction & Policy: Background `asyncio` task computes semantic score (α·recency + β·freq + γ·salience); supports pinned keys and namespace quotas.
- Observability & Ops: [`prometheus_client`](https://github.com/prometheus/client_python) metrics, basic `OpenTelemetry` tracing, `/healthz` and `/metrics` routes, single Docker container deploy.

All libraries are open source (Apache 2.0 / MIT) and run locally with no proprietary dependencies.

#### Goal

Ship an MVP that lets any LLM agent:

1. Write & read structured memory and semantic entries for queries.
2. Append & replay temporal streams per user/session and read memory “as of” a timestamp.
3. Run hybrid semantic queries with metadata filters and return ranked, deduped memories.
4. Provide lineage & traces so teams can debug *why* an answer happened given the memory at that moment.
