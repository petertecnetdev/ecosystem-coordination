# PA07 — Support queue stale-response protection

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
priority: P1
status: START
branch: agent/pa07/admincenter-support-stale-response

## Scope
Protect `apps/admincenter/src/SupportAdminApp.jsx` from out-of-order list/detail responses when filters change or a refresh is triggered while an earlier request is still pending. Preserve existing endpoints, payloads, auth, and support workflow semantics.

## Coordination
Reviewed ecosystem coordination COMMANDS/CURRENT_STATE/PRIORITIES/BLOCKERS, active claims, target repo AGENTS/CURRENT_STATE/AGENT_CHAT, recent main commits, and open PRs. Existing PA07/NP05 work covers shared `adminApi.js`, streamed requests, retry delay cleanup, establishments, realtime, and navigation; this claim is isolated to the support queue local request lifecycle.

## Safety
GitHub-only. No VPS, SSH, production services, production filesystem, database, Redis, Nginx, PHP-FPM, Supervisor, DNS, SSL, secrets, force-push, bypass, destructive operations, or merge to main.
