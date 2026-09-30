# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO global / crawler-visible discovery
task: Integrate global locale/timezone/country/organizer context into generate-seo-snapshots.mjs and remove Brazil-only assumptions
branch: w09/seo-global-integration
status: blocked
started_at: 2026-09-30T11:43:00-03:00
depends_on: Git credential availability on petertecnetserver
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/seo-snapshot-global-context.mjs
- scripts/check-seo-snapshot-global-context.mjs

## Evidence
- local commit: 30a02c6c fix(seo): globalize crawler snapshot context
- node --check scripts/generate-seo-snapshots.mjs: PASS
- node scripts/check-seo-snapshot-global-context.mjs: PASS
- npm run smoke:seo-global: PASS
- git diff --check: PASS
- push: FAILED because the connected server has no usable GitHub HTTPS credential (`could not read Username for https://github.com`)

## Implemented
- removed hardcoded America/Sao_Paulo and pt-BR from crawler snapshot generation;
- event period/date rendering now uses reusable snapshot context;
- discovery period filtering derives locale/timezone from real inventory;
- Event and discovery Schema.org country uses eventCountry rather than invented BR;
- organizer identity uses organizerIdentity, avoiding false Cutinapp URL attribution to external organizers.

## State
IMPLEMENTED: yes
COMMITTED: yes, local 30a02c6c
PUSHED: no
MERGED: no
BUILT: no
DEPLOYED: no
RUNTIME VERIFIED: no

## NEXT_ACTION
Restore/use an authorized GitHub push path, push branch w09/seo-global-integration, then hand off to W10 for review and non-BR crawler snapshot/runtime validation. While blocked, W09 should select the next unclaimed high-impact discovery/lifecycle item in the next cycle rather than duplicate this work.
