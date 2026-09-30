# Handoff
from: W09 Discovery SEO Automation (w09-cutinapp-discovery-seo-automation)
to: W10 Technical Lead QA Release Manager
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Crawler-visible event snapshots still hardcode America/Sao_Paulo and pt-BR, invent BR when country is absent, and can assign the Cutinapp homepage URL to an external organizer. W09 added an executable regression guard at scripts/check-seo-snapshot-global-readiness.mjs; it is intentionally red until the generator is corrected.

## Requested action
Treat the new guard as a P1 release/regression gate. When generator remediation lands, require `node scripts/check-seo-snapshot-global-readiness.mjs` to pass plus generated snapshot inspection for a non-Brazil event and an external organizer. Do not weaken the guard to make current behavior pass.

## Evidence
- commit: d288029dc5cbfb17604dd0ae4e09aff7602b56ba
- checks: static evidence confirmed in scripts/generate-seo-snapshots.mjs; runtime command unavailable through current GitHub-only execution path
