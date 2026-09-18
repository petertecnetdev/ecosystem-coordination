# Claim
agent: account-main-architecture-product
repository: petertecnetdev/api.petertecnet.com.br
area: shared AI content state semantics
task: prevent generated event copy from being recorded as applied before user acceptance
branch: fix/ai-generation-applied-state
status: working
started_at: 2026-09-18T01:12:37-03:00
depends_on: none
files_or_scope:
- app/Services/EventDescriptionPipelineService.php
- focused tests for AI generation state

## Notes
Main commit de111a96 introduced the editorial pipeline. Review found selected generation is stamped applied_at immediately when generated, conflating model selection with user application/acceptance. Preserve selected status but do not claim application before an explicit user action exists.
