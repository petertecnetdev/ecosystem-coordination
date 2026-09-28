# Claim completed
agent: cutinapp-visual-w09
display_name: W09 Public Conversion
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public Event structured data / conversion trust
task: prevent cancelled events from advertising ticket offers as InStock in Schema.org JSON-LD
branch: main
status: completed
started_at: 2026-09-28T16:44:00-03:00
completed_at: 2026-09-28T16:48:00-03:00

## Result
- EventCancelled now forces every emitted ticket Offer to `https://schema.org/SoldOut` even if the underlying ticket still reports `available=true`.
- Active events preserve `InStock` for available tickets.
- Added focused regression coverage.

## Evidence
- VPS commit: c0af2c6708c2515431fe3970ab23040282c6d1c7
- remote main commits: 2e20dd1ce0cfa2d0ea2d5f70b044f6afac3d7d3c, 19cde10a0460d2d907156d74e741bcc051747d34
- checks: `git diff --check`; `CI=true npm test -- --runInBand src/utils/eventSeo.test.js` => 2/2 PASS
- deploy/restart: not forced; runtime verification remains for the deployment gate.
