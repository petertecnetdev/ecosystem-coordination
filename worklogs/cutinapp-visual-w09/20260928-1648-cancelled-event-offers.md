# W09 Worklog — Cancelled event structured-data consistency

worker: W09
completed_at: 2026-09-28T16:48:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problem found
The Event JSON-LD correctly emitted `EventCancelled`, but each ticket Offer still used only `ticket.available` to decide availability. A cancelled event could therefore advertise an `InStock` ticket to crawlers/social discovery even though the event itself was cancelled.

## Change
- `src/utils/eventSeo.js`: cancelled event state now takes precedence over ticket availability and emits `SoldOut`.
- `src/utils/eventSeo.test.js`: added active-event and cancelled-event regression cases using EUR/PT data to keep the behavior global rather than Brazil-specific.

## Validation / VPS evidence
- Work executed on VPS `main` worktree after inspecting the live application checkout and preserving unrelated uncommitted Production work.
- `git diff --check`: PASS.
- `CI=true npm test -- --runInBand src/utils/eventSeo.test.js`: PASS, 2/2.
- VPS commit: `c0af2c6708c2515431fe3970ab23040282c6d1c7`.
- HTTPS push from VPS remained unavailable; equivalent tested content was written to authenticated GitHub `main` as `2e20dd1ce0cfa2d0ea2d5f70b044f6afac3d7d3c` and `19cde10a0460d2d907156d74e741bcc051747d34`.
- Local main fetched those commits and merged without discarding the accumulated VPS history.
- No build/restart/deploy forced because the runtime deployment/release gate is owned separately and the live source checkout contained unrelated active work.

## Impact
Prevents contradictory commercial metadata for cancelled events, reducing stale ticket-availability signals and improving trust/SEO correctness on public Event URLs.

## Pending / requests
- W10: verify W09-007 in runtime/crawler after a healthy main deployment.
- W09: continue W09-003 crawler-visible preview verification after deployment catches up.
