# From Data Engineer to AI Engineer — 8-Week Sprint

> **Dismas Mike · Nairobi · ~720 hours over 8 weeks**
> Compressed roadmap for 12 hr/day intensive study.
> Three production projects shipped. Job applications open by Week 7.

---

## Reality check before you start

This pace works because you have **strong DE foundations already**. You're not learning Python, SQL, pipelines, or cloud — you're learning the AI layer that sits on top. If you didn't have that, 2 months would be a fantasy.

**The compression hurts in three places:**

1. **Concept consolidation.** Sleep and time turn knowledge into intuition. You'll have less of both. Compensate by writing — every concept gets a 200-word explanation in your own words by end of day.
2. **Project iteration.** Real projects improve when you sit with them. You'll ship faster but rougher versions. That's fine for a portfolio, harder in interviews.
3. **Network depth.** You won't have months of community presence. Compensate by writing publicly from Week 1 — blog posts and LinkedIn posts as you go.

**Three rules that must not bend:**

- **One rest day per week.** Sundays. Walk, sleep, see people, no screens.
- **Sleep 7+ hours.** This plan dies if sleep dies.
- **Ship every Saturday.** Each week ends with something pushed to GitHub. No exceptions.

---

## Daily rhythm (the 12-hour template)

| Block | Time | Focus |
|---|---|---|
| **Block A — Theory** | 06:00–10:00 (4hr) | Courses, papers, reading. Best brain hours. |
| Break + walk | 10:00–11:00 | Outside. No phone. |
| **Block B — Build** | 11:00–15:00 (4hr) | Current project. Code only. |
| Lunch + nap | 15:00–16:00 | Real food. Real nap if possible. |
| **Block C — Practice** | 16:00–19:00 (3hr) | Experiments, exercises, debugging. |
| Dinner + off | 19:00–20:30 | Off screens. |
| **Block D — Write** | 20:30–21:30 (1hr) | Blog post, daily notes, tomorrow's plan. |
| Sleep | 22:30 | Hard cutoff. |

**Saturday = ship day.** Skip Block A. Use the full day to finish whatever ships that week. Push to GitHub before sleeping.

**Sunday = off.** Fully off. The plan depends on this.

---

## The eight weeks at a glance

| Week | Theme | Capstone |
|---|---|---|
| 1 | LLM API foundations + prompt engineering | Project 1: Geospatial Q&A CLI |
| 2 | RAG fundamentals | Project 2 (kickoff) |
| 3 | RAG production-grade | Project 2 (shipped) |
| 4 | Agents + deployment | Project 3 (kickoff) |
| 5 | Agents shipped + evals retrofit | Project 3 (shipped) + eval suites |
| 6 | ML/DL fundamentals + transformers | Karpathy GPT-from-scratch built |
| 7 | Fine-tuning + positioning + applications open | Fine-tuned model + resume + 3 blog posts |
| 8 | Interview prep + apply hard + polish | 30+ applications out, system design fluent |

---

# Week 1 — LLM API Foundations

**Goal:** Master the Anthropic and OpenAI APIs at the SDK level. No frameworks. Ship a working tool-using app by Saturday.

## Setup (Monday, first 4 hours)

- [ ] Get API keys: Anthropic, OpenAI, Groq, Cohere, Voyage
- [ ] Hugging Face account
- [ ] Create GitHub repo: `ai-engineer-journey` (umbrella repo with sub-projects)
- [ ] Install: Python 3.11+, `uv`, Cursor (or VS Code + Continue/Cline), Docker Desktop
- [ ] Subscribe: Latent Space, The Batch, Ahead of AI
- [ ] Set up Anthropic Workbench account, OpenAI Playground access
- [ ] Watch Karpathy "Intro to LLMs" (1hr) — twice if needed

## Daily targets

**Mon:** Setup + Karpathy video + Anthropic API hello-world. Read first 3 chapters of Anthropic Prompt Engineering Tutorial.
**Tue:** Tutorial chapters 4–6. Build 5 tiny scripts: chat, streaming, system prompts, multi-turn, JSON output.
**Wed:** Tutorial chapters 7–9. Tool use deep dive. Build a tool that hits a real API (weather + SQL).
**Thu:** Read Anthropic "Building Effective Agents" twice. Implement chaining, routing, parallelization patterns as separate scripts.
**Fri:** Token economics — tiktoken, prompt caching, batch API. Cost-estimate every script you wrote.
**Sat (ship day):** Build and ship Project 1.

## Project 1 — Geospatial Q&A CLI

**Stack:** Python · Anthropic SDK · psycopg · your existing Africa Power Atlas Postgres data

A CLI tool: user asks a natural language question about Africa's power infrastructure. Claude has one tool — `execute_sql` — against your existing dataset. Returns conversational answers with cited numbers.

**Must include:**
- Tool definition with proper schema
- Multi-turn conversation, state preserved
- Streaming output
- Cost logging per query (tokens in/out, $)
- Refuses dangerous SQL (no DROP, DELETE, etc.)
- README with architecture diagram + 5 example queries
- Demo GIF

## Resources

- [Anthropic Prompt Engineering Tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial) — do every chapter
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) — copy-modify-learn
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) — read 3x
- [OpenAI Cookbook](https://cookbook.openai.com/) — same idea, OpenAI flavor
- [DAIR.AI Prompting Guide](https://www.promptingguide.ai/) — reference
- Karpathy "Intro to LLMs": `https://www.youtube.com/watch?v=zjkBMFhNj_g`

---

# Week 2 — RAG Fundamentals

**Goal:** Understand embeddings, vector search, chunking, and hybrid retrieval. Stand up a working RAG prototype by Saturday.

## Daily targets

**Mon:** Embeddings theory. Cosine vs dot product. Generate embeddings with OpenAI `text-embedding-3-small`, Voyage, and BGE. Compare. Read MTEB leaderboard.
**Tue:** pgvector deep dive. Install, build a small vector store, HNSW vs IVFFlat indexes, query performance with `EXPLAIN ANALYZE`.
**Wed:** Chunking. Watch Greg Kamradt's "5 Levels of Text Splitting" twice. Implement all 5 levels on the same document. Measure retrieval quality difference.
**Thu:** Hybrid retrieval. BM25 with Postgres FTS + vector search. Build a reranker stage with Cohere Rerank.
**Fri:** Query transformations. HyDE, multi-query, query decomposition, step-back. Implement each. Note when each helps.
**Sat (ship day):** RAG prototype scaffolded — your Africa Power Atlas + 5–10 IEA / IRENA reports indexed and queryable.

## Resources

- [RAG from Scratch — Lance Martin](https://github.com/langchain-ai/rag-from-scratch) — 14 short videos, do all
- [Pinecone Learning Center](https://www.pinecone.io/learn/) — concepts done well
- [pgvector docs](https://github.com/pgvector/pgvector)
- [Anyscale RAG production guide](https://www.anyscale.com/blog/a-comprehensive-guide-for-building-rag-based-llm-applications-part-1)
- [5 Levels of Text Splitting — Greg Kamradt](https://www.youtube.com/watch?v=8OJC21T2SL4)
- [MTEB Leaderboard](https://huggingface.co/spaces/mteb/leaderboard)

---

# Week 3 — RAG Production-Grade (Project 2 shipped)

**Goal:** Take the prototype and make it production-grade. Deploy live. Write a blog post.

## Daily targets

**Mon:** Build the ingestion pipeline as an Airflow DAG. Incremental updates, idempotent embeds, monitoring. Use your DE strength here — this is your differentiator.
**Tue:** FastAPI backend. Streaming endpoints. Pydantic models for request/response. Citation handling.
**Wed:** Streamlit (or Next.js if you prefer) frontend. Source citations with links. Chat history.
**Thu:** Deploy to Railway or Modal with Postgres. Set up auth (basic). Test end-to-end.
**Fri:** Polish — error handling, cost guards, README with architecture diagram, demo video.
**Sat (ship day):** Project 2 live. Write blog post #1 ("Building a production RAG over Africa's power infrastructure"). Post to LinkedIn and Hashnode.

## Project 2 — Africa Energy Intelligence

**Stack:** Airflow · pgvector · FastAPI · Streamlit · Cohere Rerank · Modal/Railway

Production RAG over Africa Power Atlas + IEA/IRENA reports. Users ask policy and infrastructure questions, get answers with citations.

**Must include:**
- Airflow DAG for incremental ingestion + embedding (idempotent, monitored)
- pgvector with HNSW index
- Hybrid retrieval (vector + Postgres FTS) with Cohere reranker
- FastAPI backend, Streamlit frontend, citations with source links
- Deployed live, accessible URL
- README with architecture diagram, retrieval evaluation table, demo video
- Blog post on Hashnode/Medium

---

# Week 4 — Agents + Production Deployment

**Goal:** Understand agent design patterns. Build the multi-tool agent (Project 3 starts). Deploy with confidence.

## Daily targets

**Mon:** Re-read "Building Effective Agents." Implement each pattern as a standalone script: prompt chaining, routing, parallelization, orchestrator-workers, evaluator-optimizer.
**Tue:** Choose orchestration: LangGraph or PydanticAI. Build a non-trivial agent in your chosen tool. State machine with retries.
**Wed:** MCP (Model Context Protocol) — read the spec, build a tiny MCP server that exposes your Postgres geo data. This is forward-looking.
**Thu:** FastAPI for agents — async, streaming progress to UI via SSE, background tasks for long-running work.
**Fri:** Docker multi-stage builds. Deploy to Modal. Cost ceilings, max-iteration guards, observability hooks.
**Sat (ship day):** Project 3 scaffolded — agent runs end-to-end, even if rough.

## Resources

- [Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents) — your bible
- [LangGraph docs](https://langchain-ai.github.io/langgraph/) — most-used
- [PydanticAI docs](https://ai.pydantic.dev/) — cleaner type-safe alternative
- [Model Context Protocol](https://modelcontextprotocol.io/) — Anthropic's standard
- [FastAPI](https://fastapi.tiangolo.com/) — your new web framework
- [Modal](https://modal.com/) — best AI deployment platform, generous free tier

---

# Week 5 — Agents Shipped + Evals Retrofit

**Goal:** Ship Project 3 by Wednesday. Then go deep on evals — retrofit eval suites onto Projects 2 and 3. **This week is your moat.**

## Daily targets

**Mon:** Polish Project 3. All 5 tools work. State machine handles errors gracefully.
**Tue:** Streaming progress UI. Generates downloadable PDF report. Auth. Deploy.
**Wed (ship day, mid-week):** Project 3 live. Demo video. README. Blog post #2.
**Thu:** Evals theory. Read Hamel Husain "Your AI Product Needs Evals" twice. Then Eugene Yan's "Evals for LLM Systems."
**Fri:** Build a 50-pair golden dataset by hand for Project 2. LLM-as-judge with Claude grading vs your hand-grades. Calibrate.
**Sat (ship day):** Eval suite for Project 2 + retrieval metrics (Precision@k, Recall@k, MRR). Wire into GitHub Actions. Same for Project 3 (lighter version, agent-specific). Blog post #3 — "Evals are how you go from demo to product."

## Project 3 — Urban Planning Research Agent

**Stack:** LangGraph (or PydanticAI) · MCP · FastAPI · Modal

Given a location, the agent autonomously: fetches geospatial data, queries demographic APIs, retrieves policy documents, runs spatial analysis, produces a structured site assessment PDF. Leverages your **actual urban planning expertise** — most AI engineers cannot build this.

**Must include:**
- ≥5 tools (geo query, web search, doc retrieval, spatial analysis, report generation)
- State machine with retry, cost ceiling, max-iteration guard
- Streaming progress to UI via SSE
- Generates downloadable PDF report
- Deployed live, with auth
- 3-min demo video
- Blog post

## Eval resources

- [Your AI Product Needs Evals — Hamel Husain](https://hamel.dev/blog/posts/evals/) — single most important essay
- [Evals for LLM Systems — Eugene Yan](https://eugeneyan.com/writing/evals/)
- [Langfuse](https://langfuse.com/) — open-source observability
- [Braintrust](https://www.braintrust.dev/) — eval-first platform, generous free tier
- [Parlance Labs Workshops](https://parlance-labs.com/education/) — Hamel Husain's workshop recordings, free
- [Evaluating & Debugging GenAI](https://learn.deeplearning.ai/courses/evaluating-and-debugging-generative-ai) — DeepLearning.AI short course, free

---

# Week 6 — ML/DL Fundamentals + Transformers

**Goal:** Build a transformer from scratch with Karpathy. Understand the architecture deeply enough that paper abstracts make sense and interviewers can't bluff you.

## Daily targets

**Mon:** PyTorch basics. Tensors, autograd, training loop. Build a tiny MLP classifier on MNIST.
**Tue–Thu:** Karpathy "Let's build GPT" + the rest of his Zero to Hero series. **Code along, don't just watch.** Build it line by line.
**Fri:** Hugging Face NLP course — chapters 1–4. Tokenizers, AutoModel, AutoTokenizer, the `transformers` library.
**Sat (ship day):** Push your built-from-scratch GPT to GitHub with a README walkthrough. Blog post #4 ("What I learned building a transformer from scratch in a week").

## Reading list (skim, don't drown)

Read each at the level of: "I can explain the contribution and key result in 3 sentences." Don't try to rederive the math.

- [Attention Is All You Need](https://arxiv.org/abs/1706.03762) — the transformer paper
- [GPT-3 Paper](https://arxiv.org/abs/2005.14165) — emergence and few-shot
- [InstructGPT / RLHF](https://arxiv.org/abs/2203.02155) — alignment
- [The Illustrated Transformer — Jay Alammar](https://jalammar.github.io/illustrated-transformer/) — companion read, do this first
- [Llama 3 paper](https://arxiv.org/abs/2407.21783) or DeepSeek-V3 — for vibes on what's current

## Resources

- [Karpathy Zero to Hero](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ) — the full playlist, ~10hr
- [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course)
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)

---

# Week 7 — Fine-Tuning + Positioning + Applications Open

**Goal:** Fine-tune a real model. Rewrite resume. Open the job hunt.

## Daily targets

**Mon:** Read LoRA paper. Read QLoRA paper. Hugging Face PEFT docs. Plan your fine-tune task.
**Tue:** Fine-tune a 7B model (Llama 3.1 8B or Qwen 2.5 7B) on a real task — e.g. extracting structured data from urban planning documents you have. Use Unsloth or HF PEFT. Rent GPU on Modal or RunPod (~$10–30 total).
**Wed:** Quantization basics. Run quantized model locally with Ollama. Push your fine-tuned adapter to HF Hub.
**Thu:** Resume rewrite. Headline: "Data + AI Engineer · Geospatial Specialist." LinkedIn About section rewrite. Blog post #5 — fine-tuning writeup.
**Fri:** Polish all three projects' READMEs. Architecture diagrams in every one. Pin top 4 repos on GitHub (the umbrella + the 3 projects).
**Sat (ship day):** Build target list of 30 companies. First 10 applications out. Connect on LinkedIn with hiring managers / engineers at each.
**Mon (Week 8 prep) Sunday off as usual.**

## Resources

- [LoRA Paper](https://arxiv.org/abs/2106.09685) — short and clear
- [QLoRA Paper](https://arxiv.org/abs/2305.14314)
- [HF PEFT](https://huggingface.co/docs/peft/index)
- [Unsloth](https://github.com/unslothai/unsloth) — fastest way to fine-tune
- [Ollama](https://ollama.com/) — run quantized models locally

## Target company list (starter)

**African AI:** Lelapa AI · InstaDeep · Aerobotics · Apollo Agriculture · Andela · Sand Technologies
**Remote-friendly globals:** Hugging Face · Replicate · Modal · LangChain · Anthropic · OpenAI · Mistral · Together AI · Anyscale
**Climate / geospatial AI (your wedge):** ClimateAI · Planet Labs · Pachama · One Concern · Cervest · Atlas AI · Regrid

---

# Week 8 — Interview Prep + Apply Hard + Polish

**Goal:** Get fluent in AI system design interviews. Push 30+ applications. Polish every public surface.

## Daily targets

**Mon:** AI system design — read Aman Chadha's primers. Practice: "Design a RAG system over 10M docs." "Design a multi-tenant agent platform." Whiteboard each.
**Tue:** Practice more system designs: "Design ChatGPT," "Design a code review bot." Time yourself — 45 min each.
**Wed:** Coding interviews — refresh on data-structures-y problems with an AI flavor. Embedding similarity search, top-k, batching, async patterns.
**Thu:** Behavioral prep. Pick 6 stories from your projects covering: technical depth, tradeoff decisions, failure recovery, cross-functional work, ambiguity handling, leadership.
**Fri:** Push the next 20 applications. Personalize every cold message. Reach out to 5 engineers per day on LinkedIn for warm conversations.
**Sat:** Clean sweep — every blog post polished, every README polished, every demo video accessible. Update LinkedIn with all projects. Apply to Deep Learning Indaba and the next Zindi competition.
**Sun:** **Off.** You earned it.

## Resources

- [aman.ai AI Primers](https://aman.ai/primers/ai/) — encyclopedic reference
- [Chip Huyen ML Interviews Book](https://huyenchip.com/ml-interviews-book/) — free online
- [Latent Space jobs](https://www.latent.space/) — AI-specific job board
- [AI Engineer Foundation](https://aiengineer.foundation/)
- [Deep Learning Indaba](https://deeplearningindaba.com/)
- [Zindi](https://zindi.africa/) — Africa-focused ML competitions
- [Lablab.ai](https://lablab.ai/) — fast hackathons for portfolio fuel

---

## What you'll have at the end of Week 8

- **3 production AI projects** deployed live with demo videos
- **5 blog posts** demonstrating depth (Hashnode + LinkedIn)
- **A fine-tuned model** on Hugging Face Hub
- **Eval suites** running in CI on two of the projects
- **A built-from-scratch transformer** as a learning artifact
- **30+ applications** out, with at least 5 warm intros
- **A rewritten resume** that says "Data + AI Engineer · Geospatial Specialist" — a positioning almost no one else has

That portfolio alone gets you interviews. The geospatial wedge gets you remembered.

---

## Anti-patterns that will kill this plan

1. **Skipping rest day.** Burnout is silent until it isn't. Take Sunday off.
2. **Tutorial hell.** If you've watched a course for 3hr without writing your own code, stop and build.
3. **Framework worship.** Raw API first. LangChain only when you understand what it abstracts.
4. **Skipping evals.** Week 5 is non-negotiable. Evals are your moat.
5. **Building without shipping.** Every Saturday: pushed, deployed, demo'd. No exceptions.
6. **Hoarding learning.** Write publicly from Week 1. Cheap teaching = cheap network.
7. **Chasing every new model.** Pick your stack and stick with it. Anthropic + OpenAI + one open model. That's it.
8. **Cold applications only.** Cold apps die in stacks of 1000. Warm intros convert 10x.

---

## Budget

| Item | Cost |
|---|---|
| API credits (Anthropic + OpenAI + Cohere) | ~$50/month × 2 = $100 |
| GPU rental for Week 7 fine-tuning | ~$30 once |
| Domain + hosting (Vercel free + Modal free tier) | $0 |
| **Total** | **~$130** |

Apply for Anthropic build credits at `console.anthropic.com` — free credits available for builders. OpenAI similar.

---

## Daily template (copy this to a journal)

```
DATE: ____   WEEK: ____   DAY: ____

Block A (Theory, 4hr):
  - Topic: ___________________________
  - Resource: ________________________
  - One key insight: _________________

Block B (Build, 4hr):
  - Project: _________________________
  - Goal today: ______________________
  - Result: __________________________
  - Stuck on: ________________________

Block C (Practice, 3hr):
  - Exercise / experiment: ___________
  - Output: __________________________

Block D (Write, 1hr):
  - 200-word explanation of one concept
  - Tomorrow's first task: ____________

Sleep target: 22:30
```

---

## When you start

Save this file. Open it every morning before Block A. Check off completed items. Update the template. The act of writing is the practice.

The first day matters most. **Make Monday undeniable.**

— End of plan —
