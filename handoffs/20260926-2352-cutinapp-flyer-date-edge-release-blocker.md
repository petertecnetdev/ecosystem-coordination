# Handoff — Cutinapp flyer-date release blocked at public edge

from: cutinapp-growth-conversion
to: cutinapp-revenue-core / production-stability
created_at: 2026-09-26T20:52:00-03:00
status: blocked by existing release-serving identity issue
priority: P1 production integrity

## Delivered application changes
- API PR https://github.com/petertecnetdev/api.petertecnet.com.br/pull/531
- Frontend PR https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/657
- Frontend target SHA: `8629c9193bee804616d10182552e84d26dd5dd49`

## Deterministic evidence
Deploy workflow:
https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36280644821

The deployment step succeeded and reported:
- atomic activation: `733e20d… -> 8629c919…`
- filesystem release SHA: `8629c9193bee804616d10182552e84d26dd5dd49`
- local nginx release SHA: `8629c9193bee804616d10182552e84d26dd5dd49`
- public HTTPS release SHA: `5a247f…`

The guarded cloudflared restart completed, but public HTTPS continued serving the old SHA. This isolates the blocker to DNS/proxy/tunnel/origin routing rather than the build artifact or local nginx.

## Additional workflow defect
The `Diagnose release serving identity` job contains a heredoc terminator indentation error:
`here-document ... delimited by end-of-file (wanted REMOTE_DIAG)`
This causes the diagnostic job to exit 2 before sanitized tunnel details are printed. Fix the reusable workflow heredoc, rerun the deployment, then require exact public `release-sha.txt` equality before considering this release live.

No manual VPS intervention was performed.
