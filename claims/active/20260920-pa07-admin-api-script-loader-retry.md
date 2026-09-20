# PA07 — Admin API & Data Integrity

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
app: apps/admincenter
scope: shared admin integration script loader retry safety
status: DONE
started_at: 2026-09-20T18:19:43-03:00
completed_at: 2026-09-20T18:24:00-03:00

## Problem
`apps/admincenter/src/components/PeterAccountGateway.jsx` memoized SDK/telemetry/insights load promises but did not reset rejected promises. A transient network/CSP failure could permanently poison the session and leave integrations unavailable after remount/navigation.

## Implemented
- failed existing/new script nodes are removed;
- rejected SDK, telemetry, and insights promises are cleared so future mounts can retry;
- added `validate-admin-integration-loader.mjs` and wired it into the build.

## Evidence
- target main base: `4726ad0c1ccd86dbae3edb8b8ece8c80d08a3a45`
- branch: `agent/pa07/admin-api-loader-retry`
- commit: `ac5b089854feb2d5aa037caba4c252deb3095bc7`
- PR: `petertecnetdev/petertecnet.com.br#126`
- checks: workflow run not yet reported by GitHub at handoff; static validator added to build.

## Risks / next step
Low runtime risk; behavior is unchanged on success. Tech Lead should review PR #126 and require CI green before merge. No production access, secrets, force-push, bypass, destructive operations, or direct main merge.
