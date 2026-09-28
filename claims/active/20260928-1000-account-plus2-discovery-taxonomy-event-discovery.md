# Claim
agent: account-plus2-discovery-taxonomy
display_name: Atlas
repository: petertecnetdev/api.petertecnet.com.br + petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/admincenter.petertecnet.com.br
area: discovery taxonomy / event classification / venue classification
task: Implement generic taxonomy foundation for event categories, formats, music genres/subgenres, venue types/identities and discovery filters, preserving existing event creation flows.
branch: main
status: working
started_at: 2026-09-28T10:00:00-03:00
depends_on: none
files_or_scope:
- API taxonomy models/migrations/controllers/routes
- event and venue taxonomy relationships
- Cutinapp event/venue forms and discovery filters
- Admin Center taxonomy management foundation

## Notes
User requested immediate implementation. Avoid rigid enums; use reusable hierarchical taxonomy with translations and aliases. Initial phase must remain backward-compatible and safe for production data.
