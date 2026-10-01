# PeterTecnet Branch Hygiene — Canonical Inventory

Repository: `petertecnetdev/petertecnet.com.br`
Captured at: 2026-10-01T12:41:48-03:00
Total branches: 197
Default branch: `main`
Main SHA at audit baseline: `3457f7ae1115ea4a4d3d05abd2584c42fc77ea98`
Ordering: lexicographic by branch name
Pagination verification: API pages 1–2 populated; page 3 (`per_page=100`) empty.
Snapshot content hash: PENDING — publication intentionally not blocked on byte-perfect hash.

## Status

Canonical inventory publication initialized. Full `branch + HEAD` enumeration is being processed from the paginated GitHub API snapshot. No branch deletion, force push, destructive reset/clean, deploy, or VPS operation is authorized in this phase.

## Classification vocabulary

`ACTIVE_PROTECTED`, `ALREADY_MERGED`, `EXACT_DUPLICATE`, `SUPERSEDED`, `UNIQUE_USEFUL_REVIEW`, `STALE_UNCLEAR`, `SAFE_DELETE_CANDIDATE`.

## Initial forensic findings

The snapshot contains dense agent-generated families and successive variants (`v2`, `v3`, `v4`, `final`, `current`, `rebased`) around Admin Center, authentication/identity, impersonation, deployment, observability, SEO/discovery and ecosystem UX. Examples include `agent/pa07/auth-request-signal-composition` + `-v2`, `feat/deploy-auto-bootstrap` + `-v2`, `feat/discovery-learning-loop-20260903` + `-v2-20260903`, `feature/application-branding-manager-20260903` + `-v2`, and `feature/ecosystem-impersonation` + `-v2`.

Admin Center code inside this repository requires architectural review before recovery: candidate work may now belong in `petertecnetdev/admincenter.petertecnet.com.br`, the shared API, or a reusable ecosystem module rather than the Peter Tecnet public-site repository.

## Preventive policy candidate

1. Auto-delete merged head branches when protected/release exceptions do not apply.
2. TTL review for agent branches; age alone never authorizes deletion.
3. Reuse an existing branch/PR for iterative work instead of creating `v2/v3/final` branches.
4. Standard branch naming with worker/domain/work-item identifiers.
5. Protect `main` with PR/status-check rules appropriate to the deployment workflow.
6. Periodic branch-hygiene metrics: total branches, merged-but-retained, duplicate HEAD groups, stale divergent branches, open PR heads and recovery candidates.

## Next processing pass

Materialize the complete 197-row snapshot, group identical HEADs, then batch compare each unique HEAD against baseline `main`; enrich divergent tips with associated PR state, touched files and patch-equivalence. Preserve useful divergent work as `UNIQUE_USEFUL_REVIEW`; never merge historical branches blindly.
