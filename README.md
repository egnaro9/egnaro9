### Hi, I'm Erik 👋

**Agentic systems engineer.** I build AI systems that check their own work — and keep a human on every step that can't be undone.

Self-taught over ~6 months (a career change from professional kitchens). Solo, I designed and built a full **autonomous development harness** for a shipping React / Capacitor game.

**What I build**
- 🔁 A self-reviewing agent loop — Strategy → Execution → Critic → Evaluation → Ops
- 🎯 A **differential oracle** — the same logic in two independent implementations (a React build + a native Java engine), held to invariant tests, so regressions catch themselves
- 🪜 A human-in-the-loop **autonomy ladder** — automate the launches, never the approval
- 📱 adb-driven on-device validation

**Selected projects** — small, self-contained, green in CI. Every one runs offline with deterministic mock backends, so the tests pass without a single API key. Clone any of them and see for yourself.

| Repo | What it is |
| --- | --- |
| 🔍 **[rag-eval-lab](https://github.com/egnaro9/rag-eval-lab)** | A dependency-free RAG pipeline + a deterministic eval harness (precision · recall · faithfulness) that **catches a planted hallucination** — re-checked on every push. `RAG` `pgvector` `evals` |
| 🚪 **[llm-gateway](https://github.com/egnaro9/llm-gateway)** | A multi-provider LLM gateway on **FastAPI**: auth, per-key rate limiting, caching, retries, and per-model token & cost accounting behind one endpoint. `FastAPI` `observability` |
| 🕸️ **[agent-graph](https://github.com/egnaro9/agent-graph)** | A **LangGraph** ReAct agent with multi-step tool-calling and guardrails that bite — a safe evaluator and a step budget, both tested. `LangGraph` `tool-calling` |
| 📊 **[eval-dashboard](https://github.com/egnaro9/eval-dashboard)** | A **Next.js + TypeScript** dashboard that turns an eval run into metric cards and flags hallucinations in red. Strict TS, static export, 0 vulnerabilities. `Next.js` `TypeScript` |

**Find me**
- 🌐 Portfolio — https://egnaro9.github.io
- 📐 Architecture case study — https://github.com/egnaro9/agentic-dev-harness
- 💼 LinkedIn — https://linkedin.com/in/erik-hill-98895575
- ✍️ dev.to — https://dev.to/egnaro9

*Open to remote (US) roles in agentic / AI / evals engineering.*
