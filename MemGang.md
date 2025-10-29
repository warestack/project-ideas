### MemGang: Agents sharing memory

**Inspiration**

AI agents are beginning to collaborate, retrieving data, summarizing text, writing reports. Yet most still act alone, repeating the same work in isolation.

What if a *gang* of agents could share what they know in real time?

Each agent keeps its own role, but all contribute to one shared memory, a living knowledge mesh.

**Reality**

Today, when multiple agents run in parallel, they each fetch the same files, re-call the same LLM, and forget what others already found. If one agent summarizes a document, another agent that needs the same section starts from zero. There’s no shared memory between them, only separate conversations.

**Problem**

- Agents waste time reprocessing the same data.
- Outputs are not shared, so other agents can’t build on them.
- Each agent forgets what the others already learned.

**Solution**

Build a simple system where agents can read and write to shared in-memory storage.

Each agent stores its results as “memory objects” that others can access by ID. Instead of sending full data between agents, they just share references. Together, the agents act like one collective brain, faster, cheaper, and more coordinated.

![inception](assets/inception.png)

*🎬 From [Inception](https://www.imdb.com/title/tt1375666/).*

**Key behaviors**

- Each agent has a different job, for example, one might read data, another summarize it, another combine results.
- All agents share the same memory space, so they can see and reuse each other’s notes instantly.
- When one agent finishes a task, it saves what it learned in memory instead of keeping it private.
- Other agents can read that memory instead of repeating the same work.
- Together, they behave like a gang of bots that think as one, each adding to a common pool of knowledge.

#### The MapReduce example

> MapReduce is a way to split a big task into smaller pieces that can run in parallel — and then combine the results at the end.

Consider the following example: 

1. Map: Each agent summarizes one part of a long report and saves its notes in shared memory.

2. Shuffle: Another agent reads all summaries by ID — no new downloads, just instant access.
3. Reduce: A final agent merges the shared summaries into one overall report.

Everything happens in memory, the agents move together like a flock that remembers what it has already seen.

#### Minimal tech plan / stack

- Data: Redis, Plasma etc. for shared in-memory objects and metadata.
- Scheduler: Python with asyncio or simple worker pool.
- Model: OpenAI API or local LLM for text processing.
- Dashboard: Streamlit app to show active agents, memory objects, and usage.
- Safeguards: Expire old memory automatically, log all agent writes and reads.

#### Goal

Ship a minimal MVP that:

1. Runs several agents that share one memory space.
2. Shows how sharing memory reduces repeated work.
3. Demonstrates parallel “map, shuffle, reduce” steps using Redis.
4. Define performance metrics and report optimizaiton.
5. Visualizes a flock of agents thinking together — fast, cooperative, and efficient.