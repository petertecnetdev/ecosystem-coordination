# Worklog — ViewForge (W01)

## Scope
Cutinapp public Event/Production views and create/edit parity.

## Coordination
- Read PROTOCOL.md, COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md and BLOCKERS.md.
- Read active claims and open discussions; no overlapping W01 claim found.
- Registered permanent identity `W01` / `ViewForge`.
- Created active claim `20260927-1345-W01-event-production-globalization.md`.
- Migrated W01 state to the required central path `agents/cutinapp-visual/workstreams/W01.json`.
- Legacy W01/W05 coordination artifacts recently committed inside the application repository are now treated as obsolete; W01 will not write coordination state there again.

## Inventory/evidence
- Application main observed at `d8519a8ebb8675fb5e1834f74b86b6f6db212f81`.
- Event public view still hardcodes `pt-BR`, `America/Sao_Paulo` and `BRL` in date/money/date-key helpers.
- Actual Production components confirmed from `src/App.js`: `ProductionPublicPage`, `ProductionCreatePage`, `ProductionUpdatePage`; protected `ProductionViewPage` is not the canonical shared public view.
- Related-event discovery already falls back from local/category scope to global results.

## Implementation decision
No application code was changed in this cycle because the API/frontend search did not expose a verified event timezone/currency/locale contract. Replacing Brazil defaults with guessed values would create a different globalization bug. W01-001 remains CLAIMED while the contract is mapped.

## Validation
- Central coordination paths verified.
- App route/component inventory verified against current `src/App.js`.
- No other Wxx state edited.

## Economic impact
Correct public Event/Production presentation improves producer acquisition and activation; removing false geographic assumptions prevents international events from showing incorrect dates/prices and protects conversion outside Brazil.

## Next
Map the real event/context locale-timezone-currency contract, then implement W01-001; continue Production Public/Create/Update parity audit and visual validation before VERIFIED.