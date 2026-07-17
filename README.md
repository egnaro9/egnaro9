### Hi, I'm Erik 👋

**Agentic AI engineer.** I build AI systems that check their own work — and keep a human on every step that can't be undone.

Self-taught, in under a year, after six years in professional kitchens. In that time I **shipped a game to Google Play**, built a bigger one, wrote an autonomous development harness that builds it, and published seven repos you can run yourself — including a deployed FastAPI + Postgres service my CI posts eval runs to.

**▶ [egnaro9.github.io](https://egnaro9.github.io)** — the portfolio, where most of this is live and clickable in your browser.

---

**One system that calls itself.** These five aren't separate exercises — each installs the others' published wheels and calls them. Every one runs offline with deterministic mock backends, so the tests pass without a single API key.

| Repo | What it is |
| --- | --- |
| 🕸️ **[agent-graph](https://github.com/egnaro9/agent-graph)** | A **LangGraph** ReAct agent — multi-step tool-calling with guardrails that bite (a safe evaluator, a step budget), both tested. Runs real LangGraph in your browser tab. `LangGraph` `WebAssembly` |
| 🚪 **[llm-gateway](https://github.com/egnaro9/llm-gateway)** | A multi-provider LLM gateway on **FastAPI**: auth, per-key rate limiting, caching, retries, per-model cost accounting behind one endpoint. `FastAPI` `observability` |
| 🔍 **[rag-eval-lab](https://github.com/egnaro9/rag-eval-lab)** | A dependency-free RAG pipeline + a deterministic eval harness that **catches a planted hallucination** — and scores **nDCG@10 = 0.581** on SciFact (BM25 is 0.665), so the retriever is measured against a public benchmark, not asserted. `RAG` `evals` `nDCG` |
| 📊 **[eval-dashboard](https://github.com/egnaro9/eval-dashboard)** | A **Next.js 15 + strict TypeScript** dashboard that turns an eval run into metric cards and flags hallucinations in red. Reads live from eval-history. `Next.js` `TypeScript` |
| 🗄️ **[eval-history](https://github.com/egnaro9/eval-history)** | The full-stack one: **FastAPI + SQLAlchemy 2.0 + Postgres** on Neon, deployed on Render, CI against Postgres 16 **and** 18. Alembic migrations with a models-vs-migrations drift test. My CI posts every eval run here, tagged with the commit. `Postgres` `SQLAlchemy` `Alembic` |

**Also:**
- 🎮 **[Tap Dodge Rush](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush)** — a real arcade game, **live on Google Play** ([SeraphLight Studios](https://egnaro9.github.io/seraphlight-studios/)). Two weeks of closed testing, then review, then shipped.
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
