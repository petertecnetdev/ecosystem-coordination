# W08 API exact-head merged-PR cleanup batch O — 2026-10-04 07:40 BRT

## Outcome

- API branch count: **208 -> 202**.
- Six live refs were physically deleted and independently confirmed absent.
- Each live SHA was exactly equal to the source head SHA of a merged pull request.
- No selected ref was an open PR head or part of the reserved W07/agent/preserve/quality scope.

| Deleted ref | Exact SHA | Merged PR | Merge target |
|---|---|---:|---|
| `feat/generic-resource-operations` | `a481506d31d7048a90f3acfdbfd6391a151fa47a` | #109 | `feat/leasing-lifecycle-intelligence-v2` |
| `feat/generic-portfolio-analytics` | `12e2190c06c476bd6917db5c1a7183e464e4caf5` | #107 | `feat/leasing-lifecycle-intelligence-v2` |
| `feat/admin-pdf-reports-20260903` | `538c02d802b69446838b5b1ca202ed09c2b797a6` | #63 | `staging` |
| `refactor/commerce-domain-maturity` | `a547f2b8e5ec43b37ae91aa6f75d928e51961d21` | #58 | `staging` |
| `hardening/public-file-privacy-20260902` | `2306855ffc590366eec590fe1b3a392882dbfc95` | #54 | `staging` |
| `hardening/health-deploy-gate-20260902` | `e1ba91ca2aabaee664d62c9ee1d49665bf11b32d` | #53 | `staging` |

## Execution evidence

- Workflow commit: `a5b29405b208f32092797e37143b5f7fdf2c3655`
- Workflow run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37195845993
- Job: `111417414659`
- Conclusion: `success`
- Summary: `deleted=6 already_absent=0 changed=0 failures=0`
- GitHub token permission: `contents: write`.
- Every ref was checked against its expected live SHA immediately before deletion.
- Post-run enumeration returned 202 branches and all six selected refs absent.

## Risk review

Four refs received high-risk second review based on changed-file surfaces:

- PR #109 includes a migration and route/provider changes.
- PR #58 includes payment gateway and commerce checkout services.
- PR #54 includes public-file privacy controls.
- PR #53 includes deployment workflow and health-gate files.

The operation deleted only already-merged source refs; it did not modify product code, migrations, payment logic, security behavior or deployment configuration.

## Admin Center live state

- Branch count: **2** — `main` and `feat/media-library-admin`.
- GitHub reports `main.protected=false`; protection remains an owner/admin gap.
- PR #2 remains merged and its source branch remains absent.
- PR #1 remains **KEEP**.
- API PR #534 remains open; CI run `36343439430` concluded `failure`.

## Remaining pool

- Exact live-head merged-PR refs remaining in the non-reserved W08 shard: **0**.
- Unique useful refs identified in this deletion shard: **0**.
- Remaining branches require owner-aware delta analysis or belong to open/reserved scopes.

No new branch, force push, reset, `update_ref` deletion, manual deploy or VPS action was used.
