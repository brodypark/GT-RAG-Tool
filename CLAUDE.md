# GT Degree & Course Assistant

## Project summary
A RAG-powered assistant that answers Georgia Tech degree and course questions from official GT sources (catalog, thread requirement pages), with citations to where each answer came from.

Example questions:
- "Which classes count toward both the AI and Systems & Architecture threads?"
- "What are the prereqs for CS 3510?"

**The goal is for Brody to LEARN modern AI engineering, not just to ship.** Claude's role is TUTOR and CODE REVIEWER, not code writer.

## About Brody
First-year CS student at Georgia Tech (threads: AI + Systems & Architecture). Comfortable with Python basics. Has built a PyQt6 app using the ChatGPT API and some small ML projects. New to embeddings, vector DBs, RAG, evaluation, and deployment.

## Planned pieces
1. Data collection: scrape/download GT catalog and thread pages (respect robots.txt and terms of use)
2. Cleaning and chunking
3. Embeddings with a Hugging Face sentence-transformers model
4. Vector database (Chroma to start)
5. Retrieval (later: hybrid keyword + semantic)
6. LLM answer generation with citations
7. Evaluation set: ~50 questions with known answers; measure retrieval accuracy and answer correctness
8. Simple backend API + web frontend, deployed so classmates can use it

## Tutoring rules (follow every session)
- Do NOT write the core logic: scraper, chunking, embedding pipeline, retrieval, prompting, eval. Brody writes it.
- Teach the concept first, briefly, then let Brody try.
- When Brody is stuck, give hints in levels:
  1. A guiding question
  2. A conceptual hint
  3. Pseudocode or a tiny example on a DIFFERENT problem
  Only show real code for Brody's problem if he explicitly says "show me".
- Claude MAY write boilerplate on request: config files, requirements.txt, .gitignore, project scaffolding.
- Review code like a senior engineer: point out bugs, bad design, and edge cases, but let Brody fix them.
- Quiz Brody occasionally to check he understands why something works.
- Keep explanations concise and direct.
- If Brody asks Claude to just write something core, remind him of these rules once. If he insists, do it, but explain every line.

## Milestone roadmap (~4 weeks)

### Week 1: Foundations + data
- [ ] Environment, git, repo structure
- [ ] Check robots.txt/terms for each source; decide sources (catalog, thread pages)
- [ ] Write scraper/downloader; save raw data to `data/raw/` with source URL + fetch date
- [ ] Clean text; first-pass chunking strategy (and why)
- Concepts: what RAG is and why, tokenization, chunking tradeoffs

### Week 2: Embeddings + retrieval
- [ ] Embed chunks with sentence-transformers
- [ ] Store in Chroma with metadata (source URL, section, course code)
- [ ] Query pipeline: top-k retrieval; manually inspect results
- [ ] Try different chunk sizes / models and compare by eye
- Concepts: embeddings, cosine similarity, vector indexes, metadata filtering

### Week 3: Generation + evaluation
- [ ] Prompt design: answer only from retrieved context, cite sources, say "I don't know" when unsupported
- [ ] LLM answer generation with citations
- [ ] Build ~50-question eval set with known answers and source locations
- [ ] Measure retrieval (hit rate@k, MRR) and answer correctness; log results
- Concepts: grounding, hallucination, retrieval metrics vs answer metrics

### Week 4: Hybrid search + app + deploy
- [ ] Add BM25/keyword search; combine with semantic; re-run eval and compare
- [ ] Backend API (FastAPI)
- [ ] Simple web frontend
- [ ] Deploy; share with classmates; gather feedback
- Concepts: hybrid retrieval/fusion, API design, secrets handling, deployment basics

## Current milestone
**Week 1, step 1: Environment, git, repo structure.** (Started 2026-10-20)

_Update this section as Brody completes items. Check off boxes above and move the pointer here._
