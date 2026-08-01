### Hi, I'm Erik 👋

**AI evaluation & testing engineer.** I build the tests that catch AI when it's wrong — deterministic graders, not a model grading itself — and keep a human on every step that can't be undone.

Self-taught in under a year, after six years in professional kitchens. Since then: a **live public board** tracking 16 LLMs for drift, a **merged fix in a 12-year-old compiler**, a **game shipped to Google Play**, and an **operator-supervised multi-agent harness** that reviews and validates its own work.

**▶ [egnaro9.github.io](https://egnaro9.github.io)** — the portfolio, where most of this is live and clickable in your browser.

<a href="https://egnaro9.github.io/#tour"><img src="https://egnaro9.github.io/media/portfolio-tour-poster.jpg" width="640" alt="Watch the 90-second portfolio tour"></a>

*▶ A narrated **90-second tour** through the harness, the live board, and the repos — [watch it here](https://egnaro9.github.io/#tour).*

---

## What "deterministic graders" actually looks like

An adversarial battery against a deliberately-vulnerable mock. No API key, no network, no model grading anything — the mock answers from a fixed profile, so every fail card reproduces byte-for-byte on your machine.

<img src="https://raw.githubusercontent.com/egnaro9/crashkit/main/docs/demo.gif" width="100%" alt="Adversarial battery against a vulnerable mock: vulnerability 1.00, with one fail card per broken guarantee — leaked passphrase, unrefused harmful request, unflagged fabricated citation">

*The grader names which guarantee broke and how badly. [Play it as a terminal session](https://asciinema.org/a/1jMrzzjhacCRjt06) · [crashkit](https://github.com/egnaro9/crashkit)*

## A merged fix in a twelve-year-old compiler

[**TeaVM PR #1213**](https://github.com/konsoletyper/teavm/pull/1213) — one character in `TGregorianCalendar`: `days - 2`, where the line above it and the branch beside it both use `days - 3`. Merged nine hours after I opened it, closing an issue open since 2018.

The wrong character dates to 2014. It survived because the only four assertions reaching that line were commented out in 2015 — one by the developer who later hit the bug and filed the issue, three by the maintainer who merged the fix.

**The patch adds no new tests. It uncomments four.** A commented-out assertion is a bug-shaped hole in a suite: the setup above it still runs, so the test still looks alive in the file.

## One system that calls itself

These five aren't separate exercises — they call each other, and one installs another's published wheel. Every one runs offline with deterministic mock backends, so the tests pass without a single API key.

| Repo | What it is |
| --- | --- |
| 🕸️ **[agent-graph](https://github.com/egnaro9/agent-graph)** | A **LangGraph** ReAct agent — multi-step tool-calling with real guardrails (a safe evaluator, a step budget), both tested. Runs real LangGraph in your browser tab. `LangGraph` `WebAssembly` |
| 🚪 **[llm-gateway](https://github.com/egnaro9/llm-gateway)** | A multi-provider LLM gateway on **FastAPI**: auth, per-key rate limiting, caching, retries, per-model cost accounting behind one endpoint. `FastAPI` `observability` |
| 🔍 **[rag-eval-lab](https://github.com/egnaro9/rag-eval-lab)** | A RAG pipeline + eval harness that **catches a planted hallucination** — with a from-scratch **BM25 matching the published SciFact baseline (nDCG@10 0.664 vs 0.665)**, plus hybrid retrieval and a reranker it benchmarks honestly. `RAG` `evals · nDCG` `BM25` |
| 📊 **[eval-dashboard](https://github.com/egnaro9/eval-dashboard)** | A **Next.js 15 + strict TypeScript** dashboard that turns an eval run into metric cards and flags hallucinations in red. Reads live from eval-history. `Next.js` `TypeScript` |
| 🗄️ **[eval-history](https://github.com/egnaro9/eval-history)** | The full-stack one: **FastAPI + SQLAlchemy 2.0 + Postgres** on Neon, deployed on Render, CI against Postgres 16 **and** 18. Alembic migrations with a drift test. `Postgres` `SQLAlchemy` `Alembic` |

## Evaluation & testing

| Repo | What it is |
| --- | --- |
| 📉 **[model-drift](https://github.com/egnaro9/model-drift)** | A **live public board** tracking **16 LLMs across 5 labs** for drift. A frozen 35-task suite runs daily; no LLM-as-judge, so a score that moves means the model moved. [**See the board →**](https://egnaro9.github.io/model-drift/) |
| 💥 **[crashkit](https://github.com/egnaro9/crashkit)** | Point a model at an adversarial battery with **your own key** and get a severity-weighted vulnerability report. Your key **never touches the server** — verify it in the Network tab. [**Crash-test a model →**](https://crashkit.onrender.com) |
| ⚖️ **[gradecore](https://github.com/egnaro9/gradecore)** | The grading engine behind both, extracted rather than reimplemented — `suite_hash` byte-identical across repos. Zero dependencies. |
| 🚦 **[prompt-regress](https://github.com/egnaro9/prompt-regress)** | A merge gate: runs your eval on every PR, compares against the main baseline, and **blocks on a regression**. Ships a GitHub Action. |
| ⚖️ **[evals-differential-oracle](https://github.com/egnaro9/evals-differential-oracle)** | The same logic written twice, fuzzed for disagreements. Where two implementations disagree, one is wrong — no gold labels needed. |

## Agents, tools & guardrails

| Repo | What it is |
| --- | --- |
| 🔌 **[mcp-tools](https://github.com/egnaro9/mcp-tools)** | A **Model Context Protocol** server built from the spec — JSON-RPC over stdio, no SDK, zero dependencies. Five tools, including a grader that names the sentences your sources don't support. |
| 🧪 **[pi-eval](https://github.com/egnaro9/pi-eval)** | Deterministic grading for **[pi](https://pi.dev)** — including when it **refuses**: *"this suite cannot decide between them — that is a limit of the suite, not a finding about the configs."* Reports the noise floor, puts cost next to the score. |
| 🚧 **[pi-gates](https://github.com/egnaro9/pi-gates)** | Refusal gates: `git commit`/`push` denied without an approval typed **that turn**. The trust root is the event *source*, not the text — because an extension can inject input, and a gate honouring every event could be opened by the thing it gates. [**Write-up →**](https://dev.to/agentdev9/i-built-an-ai-dev-harness-that-isnt-allowed-to-trust-itself-then-i-checked-the-part-doing-the-298a) |
| 🛠️ **[agentic-dev-harness](https://github.com/egnaro9/agentic-dev-harness)** | The architecture case study: a self-reviewing loop (Strategy → Execution → Critic → Eval → Ops), a cold independent critic, a **NO-PROOF-NO-CLOSE** evidence trail, and a human-in-the-loop autonomy ladder. |

## Shipped

🎮 **[Tap Dodge Rush](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush)** — my first game, live on Google Play under [SeraphLight Studios](https://egnaro9.github.io/seraphlight-studios/). Two weeks of closed testing, then review, then shipped. &nbsp;<a href="https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush"><img src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png" alt="Get it on Google Play" height="40"></a>

🎲 **[match3-engine](https://github.com/egnaro9/match3-engine)** — the rules engine behind it, held to 16 **jqwik** property invariants and compiled to the browser via TeaVM. Porting it caught a `System.nanoTime()` bug the JVM couldn't show.

## Find me

🌐 [Portfolio](https://egnaro9.github.io) · 💼 [LinkedIn](https://linkedin.com/in/erik-hill-98895575) · ✍️ [dev.to](https://dev.to/AgentDev9) · 🐦 [X](https://x.com/AgentDev9) · 🎮 [SeraphLight Studios](https://egnaro9.github.io/seraphlight-studios/)

*Open to remote (US) roles in AI evaluation, ML test / SDET, backend, or applied AI engineering.*
