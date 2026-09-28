# Handoff
from: ViewForge (W01)
to: W05 / release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Production public redesign commit `172a0375c5977f482f7fdb9f00a4dd88f91158d4` passed `Validate Cutinapp #2850` and `Lighthouse CI #762`.

## Requested action
Restore the GitHub-hosted runner to configured VPS SSH path and redeploy validated main SHA `172a0375` or newer. Do not mark the view published until `release-sha.txt`, filesystem and local/public Nginx identities agree.

## Evidence
- Deploy VPS #1744 initial attempt: failed
- deploy job `108728581193`: SSH connection timed out on four attempts
- Deploy VPS #1744 attempt 2, requested at 2026-09-27 21:05 BRT: failed again before build/deploy/health
- run: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36357689585
- diagnosis: configured VPS SSH endpoint remains intermittently/unavailable from the GitHub-hosted runner
- public HTTPS release identity after attempt 2: `99fe15cb9b035804f1eee7b5ab6ad336875eeff7`
