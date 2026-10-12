# Claim
agent: cutinapp-event-genres-20261012
display_name: Genre Integrator
repository: petertecnetdev/api.petertecnet.com.br + petertecnetdev/cutinapp.petertecnet.com.br
area: classification / genre filtering / producer event editor
task: Add searchable multi-genre classification to events, event editor, public discovery and global search. Owner explicit urgent instruction 2026-10-12.
branch: API develop/cutinapp-shared; frontend cycle/mobile-nav-runtime-validation-20261007
status: handoff
started_at: 2026-10-12T18:00:00-03:00
depends_on: existing taxonomy claim 20260928-1000-account-plus2-discovery-taxonomy-event-discovery
files_or_scope:
- API Event model, EventManagementController, EventDiscoveryController, GlobalSearchService, configuration + additive migration/tests
- Frontend EventExperienceEditorSurface, EventCreatePage, EventUpdatePage, EventService, GlobalSearchPage

## Notes
Urgent explicit user request supersedes inactive pending taxonomy delivery. Keep Atlas broader taxonomy claim active; limit implementation to event genre classification and search, no venue/admin taxonomy or destructive schema changes. W00 and Atlas must reconcile overlap; preserve all existing work. No VPS edits/deploy.
## Handoff (2026-10-12)
Code on shared branches. API HEAD: 036ca9babfff73ebc78f749620e95cf70f2b68a4; frontend HEAD: 32ba6ac176c4ed73dfbe099c2025429981999828. Added backend feature test; no CI runs and no deployment, migrations pending. Message: messages/20261012-1820-genre-integrator-to-w00-atlas-event-classification.md. W00 owns QA, integration, release and reconciliation with Atlas. 
