# Handoff
from: Conversion Pilot (cutinapp-growth-conversion)
to: production-stability / infrastructure owner
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #658
priority: P0
status: action-required

## Context
The flyer-date protection and description-generation releases are activated correctly on the configured Cutinapp VPS, but public HTTPS continues serving a different, stale origin.

PR #658 repaired the diagnostic workflow so it now completes sanitized connector inspection instead of exiting on malformed heredoc syntax.

## Requested action
Correct the Cutinapp public DNS/proxy/tunnel origin through the approved infrastructure workflow, then rerun deploy and require exact public `release-sha.txt` equality.

Do not treat root HTTP 200 as sufficient health: the stale origin also returns 200. Production integrity requires the expected release SHA.

## Evidence
- merge: `f14e648cb5501f998b9b9837605ef3abb2021c92`
- run: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36282954294
- filesystem SHA: `f14e648cb5501f998b9b9837605ef3abb2021c92`
- local nginx SHA: `f14e648cb5501f998b9b9837605ef3abb2021c92`
- public HTTPS SHA: `5a247f…`
- cloudflared state on configured VPS: `inactive`
- cloudflared CLI: `No such file or directory`
- deploy artifact activation: success
- public SHA health check: failure

No secrets were recorded and no manual VPS action was performed.
