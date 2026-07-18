### Hi, I'm Erik 👋

**Agentic AI engineer.** I build AI systems that check their own work — and keep a human on every step that can't be undone.

Self-taught, in under a year, after six years in professional kitchens. In that time I **shipped a game to Google Play**, built a bigger one, wrote an autonomous development harness that builds it, and published ten repos you can run yourself — including a deployed FastAPI + Postgres service my CI posts eval runs to.

**▶ [egnaro9.github.io](https://egnaro9.github.io)** — the portfolio, where most of this is live and clickable in your browser.

---

**One system that calls itself.** These five aren't separate exercises — each installs the others' published wheels and calls them. Every one runs offline with deterministic mock backends, so the tests pass without a single API key.

| Repo | What it is |
| --- | --- |
| 🕸️ **[agent-graph](https://github.com/egnaro9/agent-graph)** | A **LangGraph** ReAct agent — multi-step tool-calling with guardrails that bite (a safe evaluator, a step budget), both tested. Runs real LangGraph in your browser tab. `LangGraph` `WebAssembly` |
| 🚪 **[llm-gateway](https://github.com/egnaro9/llm-gateway)** | A multi-provider LLM gateway on **FastAPI**: auth, per-key rate limiting, caching, retries, per-model cost accounting behind one endpoint. `FastAPI` `observability` |
| 🔍 **[rag-eval-lab](https://github.com/egnaro9/rag-eval-lab)** | A dependency-free RAG pipeline + a deterministic eval harness that **catches a planted hallucination** — with a from-scratch **BM25 that matches the published SciFact baseline (nDCG@10 0.664 vs 0.665)**, plus hybrid retrieval and a reranker it benchmarks honestly (measured — they don't beat BM25 here, and it says why). `RAG` `evals · nDCG` `BM25 · hybrid` |
| 📊 **[eval-dashboard](https://github.com/egnaro9/eval-dashboard)** | A **Next.js 15 + strict TypeScript** dashboard that turns an eval run into metric cards and flags hallucinations in red. Reads live from eval-history. `Next.js` `TypeScript` |
| 🗄️ **[eval-history](https://github.com/egnaro9/eval-history)** | The full-stack one: **FastAPI + SQLAlchemy 2.0 + Postgres** on Neon, deployed on Render, CI against Postgres 16 **and** 18. Alembic migrations with a models-vs-migrations drift test. My CI posts every eval run here, tagged with the commit. `Postgres` `SQLAlchemy` `Alembic` |

**Also:**
- 🎮 **[Tap Dodge Rush](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush)** — a real arcade game, **live on Google Play** ([SeraphLight Studios](https://egnaro9.github.io/seraphlight-studios/)). Two weeks of closed testing, then review, then shipped.
- 📉 **[model-drift](https://github.com/egnaro9/model-drift)** — a **live public board** tracking **16 LLMs across 5 labs** (OpenAI, Anthropic, Google, xAI, Meta) for drift: a frozen, deterministically-graded suite runs weekly and keeps **accuracy, speed, verbosity, reliability and refusal rate** for every model. No LLM-as-judge, so a score change means the *model* moved. [**See the board →**](https://egnaro9.github.io/model-drift/)
- 🚦 **[prompt-regress](https://github.com/egnaro9/prompt-regress)** — a **does-my-prompt-still-work merge gate**: runs your eval on every PR, compares it to the main-branch baseline in eval-history, comments the verdict, and **blocks the merge on a regression**. Fills a gap promptfoo leaves open; ships a GitHub Action and gates my own repos.
- 🔌 **[mcp-tools](https://github.com/egnaro9/mcp-tools)** — a **Model Context Protocol** server implemented from the spec (JSON-RPC over stdio, no SDK, zero dependencies), exposing **five tools**: an AST-sandboxed calculator (OWASP LLM06), BM25 search, a **no-LLM-judge answer grader** that names the sentences your sources don't support, and read-only lookups against the drift board and eval-history — so an agent can **check its own work before it answers**. *Testable without a client* by speaking the real handshake to it in a subprocess.
- ⚖️ **[evals-differential-oracle](https://github.com/egnaro9/evals-differential-oracle)** — the same logic written twice, fuzzed for disagreements. Where two independent implementations disagree, one is wrong — no gold labels needed.
- 🎲 **[match3-engine](https://github.com/egnaro9/match3-engine)** — the rules engine from my second game, held to 16 **jqwik** property invariants and compiled to the browser via **TeaVM**. Porting it caught a `System.nanoTime()` bug the JVM couldn't show.
- 🛠️ **[agentic-dev-harness](https://github.com/egnaro9/agentic-dev-harness)** — a concepts-only case study of the harness: a self-reviewing loop (Strategy → Execution → Critic → Eval → Ops), a differential-oracle testing strategy, and a human-in-the-loop autonomy ladder.

**Open source:** I use TeaVM to ship Java to the browser, so I went looking for places where the port and the JVM quietly disagree — and a [**one-character `Calendar` fix**](https://github.com/konsoletyper/teavm/pull/1213) got **merged**, closing a bug that had been off by six days since 2018.

**Find me**
- 🌐 Portfolio — https://egnaro9.github.io
- 🎮 SeraphLight Studios — https://egnaro9.github.io/seraphlight-studios/
- 💼 LinkedIn — https://linkedin.com/in/erik-hill-98895575
- ✍️ dev.to — https://dev.to/egnaro9

*Open to remote (US) roles in agentic / AI / evals engineering.*
