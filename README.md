### Hi, I'm Erik 👋

**Agentic AI engineer.** I build AI systems that check their own work — and keep a human on every step that can't be undone.

Self-taught, in under a year, after six years in professional kitchens. I wrote an **operator-supervised, multi-agent development harness** that plans, builds, reviews, and validates its own changes behind a machine-checkable evidence trail — [read the architecture case study](https://github.com/egnaro9/agentic-dev-harness). Along the way I **shipped a game to Google Play**, merged a fix into a 12-year-old compiler, and published the repos below — including a deployed FastAPI + Postgres service my CI posts eval runs to.

**▶ [egnaro9.github.io](https://egnaro9.github.io)** — the portfolio, where most of this is live and clickable in your browser.

---

**A merged fix in [TeaVM](https://github.com/konsoletyper/teavm)** — the Java-to-JavaScript compiler, twelve years old, ~3,000 stars. I use TeaVM to ship a Java game engine to the browser, so I went looking for places where the port and the JVM quietly disagree. [**PR #1213**](https://github.com/konsoletyper/teavm/pull/1213): one character in `TGregorianCalendar` — `days - 2`, where the line directly above it and the branch beside it both use `days - 3`. The project lead merged it about nine hours after I opened it, closing an issue open since 2018 with no comments on it.

The wrong character dates to a June 2014 commit about `SimpleDateFormat` tests, so it had been there twelve years. It survived because the only four assertions that reach that line were commented out in 2015 — one by the developer who later hit the bug and filed the issue, three by the maintainer who eventually merged the fix. **The patch adds no new tests. It uncomments four.** A commented-out assertion is a bug-shaped hole in a suite: the setup above it still runs, so the test still looks alive in the file.

---

**One system that calls itself.** These five aren't separate exercises — they call each other, and one installs another's published wheel. Every one runs offline with deterministic mock backends, so the tests pass without a single API key.

| Repo | What it is |
| --- | --- |
| 🕸️ **[agent-graph](https://github.com/egnaro9/agent-graph)** | A **LangGraph** ReAct agent — multi-step tool-calling with real guardrails (a safe evaluator, a step budget), both tested. Runs real LangGraph in your browser tab. `LangGraph` `WebAssembly` |
| 🚪 **[llm-gateway](https://github.com/egnaro9/llm-gateway)** | A multi-provider LLM gateway on **FastAPI**: auth, per-key rate limiting, caching, retries, per-model cost accounting behind one endpoint. `FastAPI` `observability` |
| 🔍 **[rag-eval-lab](https://github.com/egnaro9/rag-eval-lab)** | A dependency-free RAG pipeline + a deterministic eval harness that **catches a planted hallucination** — with a from-scratch **BM25 that matches the published SciFact baseline (nDCG@10 0.664 vs 0.665)**, plus hybrid retrieval and a reranker it benchmarks honestly (measured — they don't beat BM25 here, and it says why). `RAG` `evals · nDCG` `BM25 · hybrid` |
| 📊 **[eval-dashboard](https://github.com/egnaro9/eval-dashboard)** | A **Next.js 15 + strict TypeScript** dashboard that turns an eval run into metric cards and flags hallucinations in red. Reads live from eval-history. `Next.js` `TypeScript` |
| 🗄️ **[eval-history](https://github.com/egnaro9/eval-history)** | The full-stack one: **FastAPI + SQLAlchemy 2.0 + Postgres** on Neon, deployed on Render, CI against Postgres 16 **and** 18. Alembic migrations with a models-vs-migrations drift test. My CI posts every eval run here, tagged with the commit. `Postgres` `SQLAlchemy` `Alembic` |

**Also:**
- 🎮 **[Tap Dodge Rush](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush)** — a real arcade game, **live on Google Play** ([SeraphLight Studios](https://egnaro9.github.io/seraphlight-studios/)). Two weeks of closed testing, then review, then shipped.
- 📉 **[model-drift](https://github.com/egnaro9/model-drift)** — a **live public board** tracking **16 LLMs across 5 labs** (OpenAI, Anthropic, Google, xAI, Meta) for drift: a frozen, deterministically-graded 35-task suite runs **daily** against every model and keeps **accuracy, speed, verbosity, reliability and refusal rate**, plus a breakdown across **nine capabilities** — because one accuracy number hides a model that is near-perfect on most of them and failing one. No LLM-as-judge, so a score that moves means the model moved, not the grader. [**See the board →**](https://egnaro9.github.io/model-drift/)
- 🚦 **[prompt-regress](https://github.com/egnaro9/prompt-regress)** — a **does-my-prompt-still-work merge gate**: runs your eval on every PR, compares it to the main-branch baseline in eval-history, comments the verdict, and **blocks the merge on a regression**. Fills a gap promptfoo leaves open; ships a GitHub Action and gates my own repos.
- 🔌 **[mcp-tools](https://github.com/egnaro9/mcp-tools)** — a **Model Context Protocol** server implemented from the spec (JSON-RPC over stdio, no SDK, zero dependencies), exposing **five tools**: an AST-sandboxed calculator (OWASP LLM06), BM25 search, a **no-LLM-judge answer grader** that names the sentences your sources don't support, and read-only lookups against the drift board and eval-history — so an agent can **check its own work before it answers**. *Testable without a client* by speaking the real handshake to it in a subprocess.
- ⚖️ **[evals-differential-oracle](https://github.com/egnaro9/evals-differential-oracle)** — the same logic written twice, fuzzed for disagreements. Where two independent implementations disagree, one is wrong — no gold labels needed.
- 🎲 **[match3-engine](https://github.com/egnaro9/match3-engine)** — a standalone match-3 rules engine, held to 16 **jqwik** property invariants and compiled to the browser via **TeaVM**. Porting it caught a `System.nanoTime()` bug the JVM couldn't show.
- 🛠️ **[agentic-dev-harness](https://github.com/egnaro9/agentic-dev-harness)** — the architecture case study of the harness: a self-reviewing loop (Strategy → Execution → Critic → Eval → Ops), a **cold, independent critic**, a differential-oracle testing strategy, a **NO-PROOF-NO-CLOSE** evidence trail, and a human-in-the-loop autonomy ladder.

**Find me**
- 🌐 Portfolio — https://egnaro9.github.io
- 🎮 SeraphLight Studios — https://egnaro9.github.io/seraphlight-studios/
- 💼 LinkedIn — https://linkedin.com/in/erik-hill-98895575
- ✍️ dev.to — https://dev.to/egnaro9

*Open to remote (US) roles in agentic / AI / evals engineering.*
