### ClassMate: Ask your course repo

**Inspiration**

Students learn faster when answers are close to the source: the slides, labs, and notes their lecturer already wrote. I wanted a simple way for a class to ask questions in natural language and get answers grounded in the course repo—not random web results.

**Reality**

Course material lives in a GitHub repository (Markdown, PDFs, notebooks). Students ask on Teams or by email. Replies repeat or arrive late. There’s no single place to search *exactly what the course says*.

**Problem**

- Students can’t quickly find the right answer in a technical question.
- TAs and lecturers answer the same questions many times.
- Generic chatbots hallucinate or quote sources that are not part of the course.

**Solution**

Build a small app that reads material from a GitHub course repository, indexes the content, and answers questions using an LLM that is restricted to the repo.

Students ask; the app retrieves the most relevant passages and returns a short answer with citations to file + section.

![school-of-rock](assets/school-of-rock.webp)

*🎬 From [School of Rock](https://www.imdb.com/title/tt0332379/), starring Jack Black.*

**Key behaviors**

- Pull and parse files from a GitHub repo (Markdown, PDFs, TXT, notebooks).
- Chunk and index content as a 7–10 sentence “knowledge blocks”.
- Retrieve top matches per question and cite the exact files/sections.
- If an answer is not inside the repo; suggest where to look instead.
- Optional “Instructions” repo: house rules, grading policy, lab etiquette used in answers.
- Simple admin refresh to re-index after material updates.

#### Example (better — auth key generation)

**Student asks:**

> “How do I set up Lab 2 on Windows with Python 3.11?”

**Answer (grounded):**

- Install Python 3.11 from the link in `labs/lab-02/setup.md`.
- Run `python -m venv .venv` and activate it (Windows steps shown).
- Install requirements using `pip install -r requirements.txt`.
- Launch the tests with `pytest -k lab02`.

**References:** `[1] labs/lab-02/setup.md — Windows steps`, `[2] labs/lab-02/requirements.txt`

**Student asks:**

> “When is the deadline for assignment 1?”

**Answer (grounded):**

- Assignment 1 (30%) deadline is on 12/12/2025. Please double check the moodle submission space.

**References:** `[1] moodle.bbk.ac.uk/acc/assigment-1`

#### Minimal tech plan / stack

- Data: GitHub API (repo content), simple cron/trigger for refresh.
- Storage: Lightweight vector index (e.g., FAISS) + small metadata store.
- Model: LLM for responses with retrieval (embeddings + top-k context).
- Backend: Python service exposing /ask and /refresh.
- Frontend: Streamlit app with Q&A box, citations, and a “Sources” view.
- Safeguards: “Answer only from provided context”; show sources; log unanswered topics.

#### Goal

Ship a minimal MVP that:

1. Connects to a GitHub course repo and builds a searchable index.
2. Answers student questions using only that material, with clear citations.
3. Gives staff a one-click refresh after pushing new content.
4. Reduces repeat questions and keeps learning aligned with the course.