**New:** [exposure-watch](https://github.com/egnaro9/exposure-watch): does an AI agent beat plain code at deciding whether installed software is exposed to a known-exploited vulnerability? On a pre-registered held-out set of 57 pairs, it is a tie on correct answers: 47 for the agent pipeline with a skeptic, 45 for a plain matcher plus one keyword rule (exact McNemar p = 0.69). The difference is where the errors go: the code gave 12 wrong answers, one of them a missed exposure, while the agent pipeline with a skeptic gave none and sent 10 pairs to a person, for $33.34 across the 57. In the first round the agents also found an error in my own answer key.

## Hi, I'm Erik 👋

**AI evaluation & testing engineer.** I build the tests that decide whether an AI system is ready to ship: capability contracts, integrity gates and replayable evidence, graded deterministically, never by a model grading itself.

**Do not trust us: run it.** The suite members below ship their claims as replayable evidence bundles (sha256-pinned, limitations mandatory, verdicts re-earnable offline), and the protocol rows are the machinery that checks them.
The format: sha256-pinned artifacts, mandatory limitations, and the exact commands to re-earn every verdict offline. [REPLAY_REQUEST.md](https://github.com/egnaro9/vac-protocol/blob/main/REPLAY_REQUEST.md) is the ten-minute falsification path: no API keys, no GPU, and if you break something it gets published, not buried.

## The suite

| Repo | What it is |
| --- | --- |
| **[vac-protocol](https://github.com/egnaro9/vac-protocol)** | **VAC: Verifiable Agent Claims.** A capability claim ships as an evidence bundle: sha256-pinned artifacts, mandatory limitations, declared numbers a stdlib-only verifier recomputes offline. The [**registry**](https://erikhill.dev/vac-protocol/) holds 12 accepted claims from 5 issuers, all of them my own repos, re-verified before every deploy and replayed weekly in CI: 11 of 12 replayed green on 2026-10-19. |
| **[agent-certlab](https://github.com/egnaro9/agent-certlab)** | Capability contracts for coding agents: seeded, known defects; grading only the artifacts left on disk, never the agent's own account. Two agents certified, and five of eight contracts earned entirely inside GitHub Actions. [**COMPARISON.md**](https://github.com/egnaro9/agent-certlab/blob/main/COMPARISON.md) is the index. |
| **[reference-fleet](https://github.com/egnaro9/reference-fleet)** | Certified reference models: six deterministic models, each broken in exactly **one documented way** at a stated, seeded rate. Point a benchmark at the fleet and you measure the benchmark. [**Audit board**](https://erikhill.dev/reference-fleet/). |
| **[evalmut](https://github.com/egnaro9/evalmut)** | Mutation testing for eval graders: inject a known defect mined from a real failure into an output your grader passed. If the grader stays green, that hole ships green. No LLM-as-judge. [**Paper**](https://github.com/egnaro9/evalmut/blob/main/paper/evalmut.pdf) (August 2026 snapshot; the README has the current numbers). |
| **[model-drift](https://github.com/egnaro9/model-drift)** | A live public board tracking 17 LLMs from five labs, daily, with a frozen suite; no LLM-as-judge, so when a score moves it was the model, the serving path or the harness, never a judge. [**Board**](https://erikhill.dev/model-drift/). |
| **[crashkit](https://github.com/egnaro9/crashkit)** | Adversarial crash-testing with deterministic grading and a severity-weighted report. Bring your own key: it never touches the server, and you can verify that in the Network tab. [**Live**](https://crashkit.erikhill.dev). |
| **[vac-gate](https://github.com/egnaro9/vac-gate)** | The integrity gate as a composite GitHub Action: no verified capability contract, no green check. Optionally re-earns verdicts from the pinned issuer commit, because "cannot regrade" is not "regraded". |

## Tools

| Repo | What it is |
| --- | --- |
| **[deadgate](https://github.com/egnaro9/deadgate)** | Finds CI checks that cannot fail: a required check satisfied by a skipped job, an exit status swallowed by a pipe. Two of its detectors were removed rather than tuned, on hand-labelled evidence that they were never right. On [PyPI](https://pypi.org/project/deadgate/). |
| **[deadcheck](https://github.com/egnaro9/deadcheck)** | Measures what a rubric can and cannot see. Run on rubrics nobody here wrote, from promptfoo, OpenAI evals and Inspect AI; OpenAI evals' `Match` accepts "10" for an ideal answer of "1". |
| **[readme-test-count](https://github.com/egnaro9/readme-test-count)** | Fails CI when the test count a README states in prose disagrees with what pytest collects. |
| **[findings-ledger](https://github.com/egnaro9/findings-ledger)** | The source of [**erikhill.dev/findings**](https://erikhill.dev/findings/): defects found by planting the defect each check claims to catch, in other people's code and in my own. Every forge status is fetched when the page is built. |
| **[pi-gates](https://github.com/egnaro9/pi-gates)** · **[pi-eval](https://github.com/egnaro9/pi-eval)** | For the [pi](https://pi.dev) agent: refusal gates that fail closed when they cannot tell (a port of my own approval gate), and deterministic grading with fixed predicates and no LLM judge. |
| **[agent-hub](https://github.com/egnaro9/agent-hub)** | An interactive galaxy of my projects and the agent roles that work on them. The agents run on canned personas until you bring your own Anthropic key. [**Fly it.**](https://erikhill.dev/agent-hub/) |

## Posts

- [**Our mutation score said 42 of 46 caught. It meant 42 of 46 labelled.**](https://dev.to/agentdev9/our-mutation-score-said-42-of-46-caught-it-meant-42-of-46-labelled-4a48): evalmut
- [**Two eval scorers passed a wrong answer because it mentioned the right one**](https://dev.to/agentdev9/two-eval-scorers-passed-a-wrong-answer-because-it-mentioned-the-right-one-10c7): deadcheck
- [**I shipped a linter for checks that cannot fail. It had four of them.**](https://dev.to/agentdev9/i-shipped-a-linter-for-checks-that-cannot-fail-it-had-four-of-them-50da): deadgate
- [**Your eval suite passes. I built the tool that checks whether it checks anything.**](https://dev.to/agentdev9/your-eval-suite-passes-i-built-the-tool-that-checks-whether-it-checks-anything-2c3f): evalmut
- [**I built an answer key for eval suites: six models broken on purpose, exactly.**](https://dev.to/agentdev9/i-built-an-answer-key-for-eval-suites-six-models-broken-on-purpose-exactly-5f98): reference-fleet

## Elsewhere

Everything else is at [**erikhill.dev**](https://erikhill.dev), including two merged PRs to [promptfoo](https://github.com/promptfoo/promptfoo) (26k+ stars), a BLEU scoring fix ([#11278](https://github.com/promptfoo/promptfoo/pull/11278)) and the `rouge-l`/`rouge-s` assertion types ([#10256](https://github.com/promptfoo/promptfoo/pull/10256)); a merged one-character fix in a compiler in development since 2013 ([TeaVM PR #1213](https://github.com/konsoletyper/teavm/pull/1213)); and a game shipped to [Google Play](https://play.google.com/store/apps/details?id=com.seraphlight.tapdodgerush).

[Portfolio](https://erikhill.dev) · [LinkedIn](https://linkedin.com/in/erik-hill-98895575) · [dev.to](https://dev.to/AgentDev9) · [X](https://x.com/AgentDev9)

*Open to remote (US) roles or relocation, in AI evaluation, ML test / SDET, backend, or applied AI engineering.*
