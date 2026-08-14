### Hi, I'm Erik 👋

**Agent Release Readiness.** I build the infrastructure that decides whether an AI system is ready to ship: capability contracts, integrity gates, and replayable evidence — deterministic graders, never a model grading itself.

**Do not trust us — run it.** Every claim below ships as a replayable evidence bundle: sha256-pinned artifacts, mandatory limitations, and the exact commands to re-earn every verdict offline. [REPLAY_REQUEST.md](https://github.com/egnaro9/vac-protocol/blob/main/REPLAY_REQUEST.md) is the ten-minute falsification path — no API keys, no GPU, and if you break something it gets published, not buried.

## The suite

| Repo | What it is |
| --- | --- |
| **[vac-protocol](https://github.com/egnaro9/vac-protocol)** | **VAC — Verifiable Agent Claims.** A capability claim ships as an evidence bundle: sha256-pinned artifacts, mandatory limitations, declared numbers a stdlib-only verifier recomputes offline. The [**registry**](https://egnaro9.github.io/vac-protocol/) holds 11 accepted claims from 5 issuers, re-verified before every deploy. |
| **[agent-certlab](https://github.com/egnaro9/agent-certlab)** | Capability contracts for coding agents: seeded, known defects; grading only the artifacts left on disk, never the agent's own account. Two agents certified — one contract earned entirely inside GitHub Actions. [**COMPARISON.md**](https://github.com/egnaro9/agent-certlab/blob/main/COMPARISON.md) is the index. |
| **[reference-fleet](https://github.com/egnaro9/reference-fleet)** | Certified reference models: six deterministic models, each broken in exactly **one documented way** at a stated, seeded rate — point a benchmark at the fleet and you measure the benchmark. [**Audit board**](https://egnaro9.github.io/reference-fleet/). |
| **[evalmut](https://github.com/egnaro9/evalmut)** | Mutation testing for eval graders: inject a known defect mined from a real failure into an output your grader passed — if the grader stays green, that hole ships green. No LLM-as-judge. [**Paper**](https://github.com/egnaro9/evalmut/blob/main/paper/evalmut.pdf). |
| **[model-drift](https://github.com/egnaro9/model-drift)** | A live public board tracking 16 LLMs with a frozen suite on a schedule; no LLM-as-judge, so a score that moves means the model moved. [**Board**](https://egnaro9.github.io/model-drift/). |
| **[crashkit](https://github.com/egnaro9/crashkit)** | Adversarial crash-testing with deterministic grading and a severity-weighted report. Bring your own key — it never touches the server; verify that in the Network tab. [**Live**](https://crashkit.onrender.com). |
| **[vac-gate](https://github.com/egnaro9/vac-gate)** | The integrity gate as a composite GitHub Action: no verified capability contract, no green check. Optionally re-earns verdicts from the pinned issuer commit — "cannot regrade" is not "regraded". |

## Launch posts

- [**Your eval suite passes. I built the tool that checks whether it checks anything.**](https://dev.to/agentdev9/your-eval-suite-passes-i-built-the-tool-that-checks-whether-it-checks-anything-2c3f) — evalmut
- [**I built an answer key for eval suites: six models broken on purpose, exactly.**](https://dev.to/agentdev9/i-built-an-answer-key-for-eval-suites-six-models-broken-on-purpose-exactly-5f98) — reference-fleet

## Elsewhere

Everything else is at [**egnaro9.github.io**](https://egnaro9.github.io) — including a merged one-character fix in a twelve-year-old compiler ([TeaVM PR #1213](https://github.com/konsoletyper/teavm/pull/1213)) and a game shipped to [Google Play](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush).

[Portfolio](https://egnaro9.github.io) · [LinkedIn](https://linkedin.com/in/erik-hill-98895575) · [dev.to](https://dev.to/AgentDev9) · [X](https://x.com/AgentDev9)

*Open to remote (US) roles in AI evaluation, ML test / SDET, backend, or applied AI engineering.*
