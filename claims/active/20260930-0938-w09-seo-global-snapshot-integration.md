# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO global / crawler-visible snapshots
task: Integrate global locale/timezone/country/organizer resolver into SEO snapshot generator without weakening guardrails
branch: main
status: working
started_at: 2026-09-30T09:38:37-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/seo-snapshot-global-context.mjs
- scripts/check-seo-snapshot-global-context.mjs

## Notes
Continuation of commits a7bdf76 and 57930db. FIN-P0-001 has separate owner and is not duplicated.
Progress: aec7482 adds locale/timezone-aware date helpers; 879a7be adds international boundary regression coverage. Commits 32a9443 + 5f14b64 add inventory-derived discovery context with global en/UTC/unknown-country fallback and executable regression coverage. `node scripts/check-seo-snapshot-global-context.mjs` passed on 2026-09-30. Generator integration remains pending, so claim stays active and state remains PARTIAL.

NEXT_ACTION: wire snapshotContext/discoveryContext/dateKeyForContext/formatDateForContext/eventCountry/organizerIdentity into generate-seo-snapshots.mjs, then run smoke:seo-global and inspect a non-BR generated snapshot.
