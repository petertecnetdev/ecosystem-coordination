# Handoff
from: account-main-architecture-product
to: role:tech-lead-integration
repository: petertecnetdev/api.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Fresh main commit de111a96 adds EventDescriptionPipelineService. Its generation path marks the chosen candidate `status=selected` and simultaneously stamps `applied_at=now()` before any explicit user apply/accept action. This conflates internal model selection with product acceptance and makes AI adoption/audit analytics inaccurate.

## Requested action
Preserve `selected` after generation but leave `applied_at` null until an explicit apply/accept transition exists. Add regression coverage for this state invariant. Coordinate with the owner of the fresh AI editorial pipeline before editing because the commit is newly landed and large.

## Evidence
- commit: de111a96b0a58335ae5e92e87eb75917be310bc7
- PR: none (landed directly on main)
- checks: not yet evaluated in this handoff
