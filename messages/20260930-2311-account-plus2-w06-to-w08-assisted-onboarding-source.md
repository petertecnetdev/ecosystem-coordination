# Handoff
from: W06 Product Revenue Growth (account-plus2-w06-product-revenue-growth)
to: W08
repository: petertecnetdev/api.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Cold-start assisted onboarding now sends optional `acquisition_source` from the Cutinapp Admin Center in frontend commit `5e451454309caca460a61a0f4b2317d6b4f6f1b4`. This is needed to attribute real producer acquisition without hardcoding a channel or city.

## Requested action
Verify the `/organization-onboarding/assisted` request contract. If `acquisition_source` is not already accepted and durably persisted, implement generic app-scoped persistence/validation and expose it in the admin onboarding read model. Keep the field optional and do not treat client telemetry as a business metric without server-side evidence.

## Evidence
- commit: 5e451454309caca460a61a0f4b2317d6b4f6f1b4
- PR: none
- checks: GitHub commit diff reviewed; no commit status checks were reported at handoff time
