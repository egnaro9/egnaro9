# Recommended pinned repositories

For the operator to apply. Order matters: GitHub shows pins in the order set, and
the profile allows a maximum of six, so vac-gate stays unpinned (it is linked from
vac-protocol's README and the profile README's suite table).

| # | Repo | Rationale |
| --- | --- | --- |
| 1 | **evalmut** | The method the program grew from: mutation testing for eval graders, with the paper in-repo; the most-starred of these repos and the subject of the launch posts. |
| 2 | **exposure-watch** | The newest work: does an AI agent beat plain code at known-exploited-vulnerability triage? A pre-registered held-out set of 57 pairs, a tie on correct answers, and only the agent pipeline with a skeptic gave no wrong answer. Also hosts the harness case study, docs/HARNESS.md. |
| 3 | **model-drift** | Longest-running live surface: a public board with daily runs shows sustained operation, not a one-shot project. Pin it once its auto-filed drift alerts are triaged. |
| 4 | **reference-fleet** | The answer key: six certified defect models plus the live audit board; the most self-explanatory demo of "measure the benchmark". |
| 5 | **agent-certlab** | Capability contracts for coding agents with replayable evidence: eight certifications, five of them earned entirely inside GitHub Actions. |
| 6 | **vac-protocol** | The trust layer over everything else: protocol, stdlib-only verifier, and the live registry (12 accepted claims from 5 issuers, all my own repos; 11 of 12 replayed green on 2026-10-19). |

Alternative for slot 6 while the registry replay is not fully green: **deadgate**, the
linter for CI checks that cannot fail.

## Current pins (as of 2026-10-19)

model-drift, crashkit, evalmut, agent-certlab, reference-fleet, vac-protocol

Delta: remove crashkit; add exposure-watch; reorder as above.

## How to apply

The public GitHub GraphQL API has **no mutation for profile pinned items** (verified
2026-08-14 by schema introspection with the account's own token: 258 mutation
fields, none touching profile pins; `pinIssue` exists, `UpdateUserPinnedItemsInput`
and every candidate input type do not). Profile pins are settable only in the web
UI:

1. Go to <https://github.com/egnaro9>, then **Customize your pins**.
2. Check exactly: evalmut, exposure-watch, model-drift, reference-fleet,
   agent-certlab, vac-protocol. Save.
3. Drag the pinned cards into the order above (GitHub supports drag-to-reorder
   after saving).

Verify the result from the CLI (read-only, this does work):

```sh
gh api graphql -f query='query { user(login: "egnaro9") { pinnedItems(first: 6, types: REPOSITORY) { nodes { ... on Repository { name } } } } }' --jq '.data.user.pinnedItems.nodes[].name'
```

Expected output, in order:

```
evalmut
exposure-watch
model-drift
reference-fleet
agent-certlab
vac-protocol
```
