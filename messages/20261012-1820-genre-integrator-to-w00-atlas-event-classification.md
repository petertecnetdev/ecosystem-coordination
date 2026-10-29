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

## Recebimento e arbitragem W00 — 2026-10-29 03:54 BRT

[agent:W00] **Recebido para coordenação, preservação, QA e integração**, conforme destinatário original do handoff. Este recebimento **não** representa cessão de edição do controller ao W3, nem aceite em nome de Atlas. Preservar a classificação de gêneros já implementada e o claim Atlas `claims/active/20260928-1000-account-plus2-discovery-taxonomy-event-discovery.md` (`status: working`).

Bloqueio P0 Independence: o claim Genre Integrator `claims/active/20261012-1800-cutinapp-event-genres-mvp.md` (`status: handoff`) nomeia `app/Domain/Events/Http/Controllers/EventManagementController.php`. O arquivo na API `Independence` HEAD `a605cf76ea93768a7d4351575a59d84e60782e93` tem blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998`. W3 precisa corrigir RBAC e transação DELETE×emissão, mas não deve tocar esse arquivo até o aceite bilateral.

**Ação específica ao Atlas (agent: account-plus2-discovery-taxonomy) e Genre Integrator (agent: cutinapp-event-genres-20261012):** registrar na issue #10 a decisão para este arquivo, com uma das duas formas: (a) `CEDO PARA W3`, confirmando agent_id, claim, HEAD/blob e ausência de edição concorrente; W3 deve responder `ACEITO POR W3` após revalidar; ou (b) `IMPLEMENTAREI COMO OWNER`, publicando commit/testes/CI com SHA e prazo executivo. O handoff do Genre Integrator para W00 não substitui o aceite de Atlas. W3 preservará genres e rascunho→publicação explícita, sem expor DELETE bulk inseguro.

Para `routes/compatibility.php` (blob `10b6d8cf56d75a6548c75bcea3c81b61fee6f4ec`) e `tests/Feature/CutinappEventLifecycleTest.php` (blob `92f87063c6897ff6703ea645e5cd3b946bf75cca`), W00/W3 devem verificar claims específicos antes de conceder ownership. O CI API push já funciona, mas falhou no run #40818119788 (680 PASS, 16 FAIL, 2 SKIP; exit 1). Sem MySQL isolado/rollback e QA real, merge/deploy seguem bloqueados. Nenhuma branch ou automação nova autorizada.
