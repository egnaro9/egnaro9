### Hi, I'm Erik 👋

**AI evaluation & testing engineer.** I build the tests that catch AI when it's wrong — deterministic graders, not a model grading itself — and keep a human on every step that can't be undone.

Self-taught, in under a year, after six years in professional kitchens. I wrote an **operator-supervised, multi-agent development harness** that plans, builds, reviews, and validates its own changes behind a machine-checkable evidence trail — [read the architecture case study](https://github.com/egnaro9/agentic-dev-harness). Along the way I **shipped a game to Google Play**, merged a fix into a 12-year-old compiler, and published the repos below — including a deployed FastAPI + Postgres service my CI posts eval runs to.

**▶ [egnaro9.github.io](https://egnaro9.github.io)** — the portfolio, where most of this is live and clickable in your browser.

<a href="https://egnaro9.github.io/#tour"><img src="https://egnaro9.github.io/media/portfolio-tour-poster.jpg" width="640" alt="Watch the 90-second portfolio tour"></a>

*▶ A narrated **90-second tour** through the harness, the live board, and the repos — [watch it here](https://egnaro9.github.io/#tour).*

🎮 **Shipped:** my first game, **Tap Dodge Rush**, is live on Google Play — &nbsp;<a href="https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush"><img src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png" alt="Get it on Google Play" height="52"></a>

---

**A merged fix in [TeaVM](https://github.com/konsoletyper/teavm)** — the Java-to-JavaScript compiler, twelve years old, ~3,000 stars. I use TeaVM to ship a Java game engine to the browser, so I went looking for places where the port and the JVM quietly disagree. [**PR #1213**](https://github.com/konsoletyper/teavm/pull/1213): one character in `TGregorianCalendar` — `days - 2`, where the line directly above it and the branch beside it both use `days - 3`. The project lead merged it about nine hours after I opened it, closing an issue open since 2018 with no comments on it.

The wrong character dates to a June 2014 commit about `SimpleDateFormat` tests, so it had been there twelve years. It survived because the only four assertions that reach that line were commented out in 2015 — one by the developer who later hit the bug and filed the issue, three by the maintainer who eventually merged the fix. **The patch adds no new tests. It uncomments four.** A commented-out assertion is a bug-shaped hole in a suite: the setup above it still runs, so the test still looks alive in the file.


**What "deterministic graders" actually looks like.** An adversarial battery run against a
deliberately-vulnerable mock — no API key, no network, no model grading anything. The mock
answers from a fixed profile, so every fail card below reproduces byte-for-byte on your
machine:

<img src="https://raw.githubusercontent.com/egnaro9/crashkit/main/docs/demo.gif" width="100%" alt="Adversarial battery against a vulnerable mock: vulnerability 1.00, with one fail card per broken guarantee — leaked passphrase, unrefused harmful request, unflagged fabricated citation">

*The grader names which guarantee broke and how badly. [Play it as a terminal session](https://asciinema.org/a/1jMrzzjhacCRjt06) · [crashkit](https://github.com/egnaro9/crashkit)*

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
- 💥 **[crashkit](https://github.com/egnaro9/crashkit)** — an **interactive AI crash test**: point a model at an adversarial battery with **your own key** (Anthropic, Gemini, xAI, Groq, OpenAI, or any OpenAI-compatible endpoint) and get back a severity-weighted vulnerability report — a fail card for every miss. Graded by **[gradecore](https://github.com/egnaro9/gradecore)**, the same deterministic, **no-LLM-judge** engine behind the drift board (`suite_hash` byte-identical — extracted, not reimplemented). Your key **never touches the server**: the browser calls the provider direct — verify it in the Network tab. Red-teaming LLMs is well-trodden ground (garak, PyRIT, promptfoo cover far more); what's checkable here is the deterministic grading and the never-touches key. [**Crash-test a model →**](https://crashkit.onrender.com)
- 🚦 **[prompt-regress](https://github.com/egnaro9/prompt-regress)** — a **does-my-prompt-still-work merge gate**: runs your eval on every PR, compares it to the main-branch baseline in eval-history, comments the verdict, and **blocks the merge on a regression**. Fills a gap promptfoo leaves open; ships a GitHub Action and gates my own repos.
- 🔌 **[mcp-tools](https://github.com/egnaro9/mcp-tools)** — a **Model Context Protocol** server implemented from the spec (JSON-RPC over stdio, no SDK, zero dependencies), exposing **five tools**: an AST-sandboxed calculator (OWASP LLM06), BM25 search, a **no-LLM-judge answer grader** that names the sentences your sources don't support, and read-only lookups against the drift board and eval-history — so an agent can **check its own work before it answers**. *Testable without a client* by speaking the real handshake to it in a subprocess.
- ⚖️ **[evals-differential-oracle](https://github.com/egnaro9/evals-differential-oracle)** — the same logic written twice, fuzzed for disagreements. Where two independent implementations disagree, one is wrong — no gold labels needed.
- 🎲 **[match3-engine](https://github.com/egnaro9/match3-engine)** — a standalone match-3 rules engine, held to 16 **jqwik** property invariants and compiled to the browser via **TeaVM**. Porting it caught a `System.nanoTime()` bug the JVM couldn't show.
- 🧪 **[pi-eval](https://github.com/egnaro9/pi-eval)** — deterministic grading and config comparison for **[pi](https://pi.dev)**, an open agent runtime. Runs a frozen suite headlessly, grades it with fixed predicates (no LLM judge), and compares two configs with an exact paired sign test — **including when it refuses**: *"even a clean sweep of 4 could not clear p<0.05, so this suite cannot decide between them — that is a limit of the suite, not a finding about the configs."* Reports the **noise floor** a config produces against *itself*, and puts **cost next to the score**, because "did it help" and "did it just cost more" are one question. Built on **[gradecore](https://github.com/egnaro9/gradecore)**, the same engine behind the drift board.
- 🚧 **[pi-gates](https://github.com/egnaro9/pi-gates)** — the refusal half, ported from my harness's Claude Code hooks onto pi: `git commit`/`push` denied without an approval phrase typed **that turn**, and judgment roles halted on the wrong model tier. The trust root is one comparison — pi's `InputSource` is `"interactive" | "rpc" | "extension"`, so an extension can inject input, and a gate honouring every input event could be opened by the thing it gates. Verified by firing synthetic events at the handler with **no model in the loop**, after a session refused a commit on its own and reported *"the gate is functioning as intended"* — with no command run and the gate never invoked. [**The write-up →**](https://dev.to/agentdev9/i-built-an-ai-dev-harness-that-isnt-allowed-to-trust-itself-then-i-checked-the-part-doing-the-298a)
- 🛠️ **[agentic-dev-harness](https://github.com/egnaro9/agentic-dev-harness)** — the architecture case study of the harness: a self-reviewing loop (Strategy → Execution → Critic → Eval → Ops), a **cold, independent critic**, a differential-oracle testing strategy, a **NO-PROOF-NO-CLOSE** evidence trail, and a human-in-the-loop autonomy ladder.

**Find me**
- 🌐 Portfolio — https://egnaro9.github.io
- 🎮 SeraphLight Studios — https://egnaro9.github.io/seraphlight-studios/
- 💼 LinkedIn — https://linkedin.com/in/erik-hill-98895575
- ✍️ dev.to — https://dev.to/AgentDev9
- 🐦 X — https://x.com/AgentDev9

*Open to remote (US) roles in AI evaluation, ML test / SDET, backend, or applied AI engineering.*
