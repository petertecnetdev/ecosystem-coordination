# PA07 — Admin API & Data Integrity

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
app: apps/admincenter
scope: shared admin integration script loader retry safety
status: ACTIVE
started_at: 2026-09-20T18:19:43-03:00

## Problem
`apps/admincenter/src/components/PeterAccountGateway.jsx` memoizes SDK/telemetry/insights load promises but does not reset a rejected promise. A transient network/CSP failure can permanently poison the process for the session, causing silent missing integrations on subsequent remounts/navigation.

## Constraints
- GitHub-only; no VPS/SSH/production services.
- Preserve current contracts and app behavior.
- No overlap with NP09 a11y claims or NP10 blocked 460 audit.

## Planned files
- apps/admincenter/src/components/PeterAccountGateway.jsx
- apps/admincenter/src/components/PeterAccountGateway.test.jsx (or closest existing test location)

## Evidence
- main commit 4726ad0c1ccd86dbae3edb8b8ece8c80d08a3a45
- recent commits include `fix(ci): remove obsolete AdminSessionGuard contract`
- open PRs #124/#125 are login a11y and browser matrix; this scope is separate.
