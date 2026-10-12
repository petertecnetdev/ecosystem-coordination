# Handoff
from: Genre Integrator (cutinapp-event-genres-20261012)
to: W00 Global Cutinapp Orchestrator / Atlas (account-plus2-discovery-taxonomy)
repository: petertecnetdev/api.petertecnet.com.br + petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Explicit owner request 2026-10-12 for music styles and event types to improve discovery and cold-start conversion. Old taxonomy claim 20260928-1000 was reviewed and not deleted. A focused compatible MVP was implemented directly on existing shared branches, not on a new branch.

## Implemented
- 35 musical genres and 15 event category labels in config/event_taxonomy.php; stable music genre slugs in nullable events.genres JSON column.
- Server validation of up to six genres, multipart normalization, model casting and event update signals.
- Backend: typed genre filter for GET /api/cutinapp/events, taxonomy options via /events/facets, global search own event genres with legacy artist fallback, text search + optional external-index safety, reindex includes genres.
- Frontend: classification selection in shared create/edit event editor; event listing and global search filters, home shortcuts, genre labels in cards and public event summary.
- Feature test: CutinappDiscoveryFiltersTest validates rock/forro matching without assigned artists.
- Genres optional to preserve existing producers/events. Existing events must be categorized manually, not automatically guessed.
- Broad hierarchy, subgenres, localized labels and Admin Center taxonomy remain Atlas scope. Category remains backwards-compatible free text; catalog selects Portuguese labels for now.

## Evidence
- API branch develop/cutinapp-shared at 036ca9babfff73ebc78f749620e95cf70f2b68a4
- Frontend branch cycle/mobile-nav-runtime-validation-20261007 at 32ba6ac176c4ed73dfbe099c2025429981999828
- No CI check runs returned for branch HEAD commits; tests have not run.
- Neither repository merged into main; no database migrations run; nothing deployed to VPS.

## Requested action
1. W00 coordinate with Atlas and other existing claims, preserving this code (no blind merges, no extra branches).
2. Run PHP/feature tests, React Jest/build/lint plus mobile responsive checks. Run migration on a safe test environment before production. Exercise create/update/clear genres, genre filters, category filters and mixed existing/legacy events.
3. Complete branch cleanup and safe PR/review per CMD-005; integrate and deploy only after pipeline approval. Confirm actual served API/frontend and cache invalidation.
4. For external search driver, run `php artisan search:reindex cutinapp` after migration/deploy; monitor query latencies and index strategy for genre JSON at scale.
5. Coordinate future hierarchical taxonomy/Admin Center/global labels with Atlas; do not overwrite existing active claim.
