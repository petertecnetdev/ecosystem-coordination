# Claim
agent: w09-cutinapp-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO crawler snapshots / global readiness
task: Add regression guardrail preventing crawler-visible SEO snapshots from inventing Brazil/timezone/organizer identity
branch: main
status: working
started_at: 2026-09-30T06:42:00Z
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/check-seo-snapshot-global-readiness.mjs

## Notes
P1 SEO regression confirmed on main: snapshot generator hardcodes America/Sao_Paulo, pt-BR, addressCountry BR fallback and Cutinapp URL for external organizer. This cycle adds an executable regression guardrail without weakening existing behavior; remediation remains required before the guard can pass.
