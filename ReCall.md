### Project idea — ReCall: Time travel to bugs

**Inspiration**

This idea came from the pain of debugging issues that can’t be reproduced. 

When systems run in distributed environments, a single transient bug can crash a service without leaving enough evidence. I’ve often wished I could just “pause” a container at the exact moment of failure and replay it later like a video.

The idea uses Linux’s [CRIU (Checkpoint/Restore in Userspace)](https://criu.org/Main_Page) to bring that concept to modern containers. It’s a way to time-travel into the exact runtime state of a failing process or microservice, without losing its memory, sockets, or environment.

![back-to-the-future](assets/back-to-the-future.gif)

🎬 [*Back to the Future* (1985)](https://www.imdb.com/title/tt0088763/), starring Michael J. Fox and Christopher Lloyd. 

**Reality**

In containerized systems, restarts are cheap but context is lost. Logs and traces show *what* happened, not *why*. Developers rely on logging or observability tools, but none can truly reproduce the runtime state that caused a failure.

CRIU already supports process checkpointing, but it’s mostly used for live migration — not debugging or replaying bugs. What if we could integrate it with Docker or Kubernetes, store snapshots, and replay them in a sandboxed cluster? That would make it possible to reproduce and study a bug exactly as it occurred.

**Problem**

Most distributed bugs are non-deterministic, they depend on timing, open sockets, memory layouts, or kernel states that can’t be easily simulated. Once a container restarts, that state is gone. Even chaos testing tools can’t recreate the *precise moment* of failure.  This makes debugging in production nearly impossible, especially for microservices that interact asynchronously.

Did you hear about the recent [AWS control-plane incident](https://aws.amazon.com/message/101925/)?

The incident centers on a latent race condition in the DNS-enactor system, where one component applied an older plan and deleted the active one, a timing and state-consistency bug. It’s the kind of failure that this tool could help capture and replay, revealing the precise runtime state that triggered the outage.

**Solution**

The tool introduces a checkpointing layer for containers that uses CRIU to capture and restore complete runtime states. It acts as a lightweight *time-travel debugger* for distributed systems. When a service crashes, you can restore it to the exact moment before failure, replay the same input, and observe its internal state.

It combines:

- A sidecar agent that triggers CRIU snapshots for specific pods.
- A coordinator that stores and indexes snapshots with metadata.
- A sandbox runner that can replay the snapshots safely in isolation.

The result: reproducible debugging, deterministic testing, and fault-tolerant analysis — all without modifying your application code.

#### Example scenario

You deploy a payments API that crashes intermittently. The tool detects the failure, checkpoints the container, and stores its state. Later, you restore the snapshot in a sandbox, replay the same HTTP request, and observe the exact race condition in memory that caused the crash. Instead of guessing, you debug the *real runtime* as it existed in production.

#### Minimal tech plan / stack

- Coordinator API: FastAPI + PostgreSQL (or SQLite) for metadata and task queue (asyncio or Celery).
- Agent: Python wrapper calling CRIU with subprocess, handles dump/restore and uploads via boto3 to S3/MinIO.
- Snapshot store: zipped CRIU image folders stored in S3, indexed with JSON metadata (pod, pid, timestamp, etc.).
- Replay sandbox: local container or pod launched using docker-py / kubernetes SDK; restores snapshot and replays inputs.
- Observability: collect logs, syscalls, and memory data using psutil and tracemalloc; compare runs with difflib.
- Dashboard: Streamlit web UI to browse snapshots, trigger restore, and visualize diffs.

  Security: HMAC-signed snapshot URLs + optional Fernet encryption for archived images.

#### Goal

Ship an MVP that lets any LLM agent:

1. Trigger `criu dump` / `criu restore` for a local containerized process via FastAPI.
2. Persist metadata and upload snapshot archives to S3/MinIO.
3. Restore snapshots on demand and replay input requests.
4. Visualize snapshots and diffs via Streamlit.
