# W09 evidence — deploy-health-marker-fallback

Captured: 2026-10-01T21:38:01-03:00
Repository: petertecnetdev/petertecnet.com.br
Baseline main: 3457f7ae1115ea4a4d3d05abd2584c42fc77ea98

## Branch

- branch: `agent/np02/deploy-health-marker-fallback`
- HEAD: `aef8cdae80f387946991bd024b674492511af559`
- compare vs main: diverged, ahead 1, behind 353
- merge base: `0c456564dccf647c25153f9c7711a37a9caf47fb`
- exclusive file: `.github/workflows/reusable-vps-deploy.yml`
- exclusive commit: `fix(deploy): tolerate SPA fallback for release marker`

## Classification

`SUPERSEDED` / `SAFE_DELETE_CANDIDATE`.

The exclusive patch makes the public release marker health check tolerate a non-SHA response when nginx routes the `.txt` path to the SPA fallback. Current `main` already contains this behavior, plus later hardening: `EXPECTED_SHA`, a cache-busted release marker URL tied to expected SHA and workflow run/attempt, explicit no-cache headers, retries, and the same SPA fallback handling. There is no useful exclusive code to recover from the historical branch.

Destination of useful code: already represented in current `main`; no cherry-pick or historical merge required.

Deletion preconditions still required at execution time: confirm no active claim and no valid open PR protecting this branch, then delete the remote ref and verify absence. Do not move the ref as a substitute for deletion.
