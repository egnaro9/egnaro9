# Recommended pinned repositories

For the operator to apply. Order matters — GitHub shows pins in the order set, and
the profile allows a maximum of six, so vac-gate stays unpinned (it is linked from
vac-protocol's README and the profile README's suite table).

| # | Repo | Rationale |
| --- | --- | --- |
| 1 | **vac-protocol** | The trust layer over everything else — protocol, stdlib-only verifier, and the live registry (11 accepted claims, 5 issuers); the right first thing a stranger reads. |
| 2 | **agent-certlab** | The flagship application: capability contracts for coding agents with replayable evidence, including one earned entirely inside GitHub Actions. |
| 3 | **reference-fleet** | The answer key — six certified defect models plus the live audit board; the most self-explanatory demo of "measure the benchmark". |
| 4 | **evalmut** | The method the program grew from: mutation testing for eval graders, with the paper in-repo; anchors the launch posts. |
| 5 | **model-drift** | Longest-running live surface — a public board with daily runs shows sustained operation, not a one-shot project. |
| 6 | **crashkit** | The interactive one — a stranger can crash-test a model in the browser with their own key in under a minute. |

## Current pins (as of 2026-08-14)

agentic-dev-harness, rag-eval-lab, eval-history, model-drift, crashkit, gradecore

Delta: remove agentic-dev-harness, rag-eval-lab, eval-history, gradecore; add
vac-protocol, agent-certlab, reference-fleet, evalmut; reorder as above.

## How to apply

The public GitHub GraphQL API has **no mutation for profile pinned items** (verified
2026-08-14 by schema introspection with the account's own token: 258 mutation
fields, none touching profile pins; `pinIssue` exists, `UpdateUserPinnedItemsInput`
and every candidate input type do not). Profile pins are settable only in the web
UI:

1. Go to <https://github.com/egnaro9> → **Customize your pins**.
2. Check exactly: vac-protocol, agent-certlab, reference-fleet, evalmut,
   model-drift, crashkit. Save.
3. Drag the pinned cards into the order above (GitHub supports drag-to-reorder
   after saving).

Verify the result from the CLI (read-only, this does work):

```sh
gh api graphql -f query='query { user(login: "egnaro9") { pinnedItems(first: 6, types: REPOSITORY) { nodes { ... on Repository { name } } } } }' --jq '.data.user.pinnedItems.nodes[].name'
```

Expected output, in order:

```
vac-protocol
agent-certlab
reference-fleet
evalmut
model-drift
crashkit
```
