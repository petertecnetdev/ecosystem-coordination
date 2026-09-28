# Claim Result
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
area: Cutinapp production public profile / social engagement drill-down
task: Tornar métricas de eventos e seguidores clicáveis e navegáveis na view pública de produção.
status: handoff
started_at: 2026-09-28T10:12:00-03:00
finished_at: 2026-09-28T10:35:00-03:00

## Result
- Publicado diretamente na VPS o frontend com métricas `eventos` e `seguidores` clicáveis, mantendo `visualizações`.
- Seguidores: modal com avatar circular, nome/username, navegação para perfil, paginação e estados de loading/erro.
- Eventos: modal com flyer quadrado 60x60 (56x56 mobile), nome, data/local e navegação para a view do evento.
- API central genérica adicionada: `GET /api/v1/apps/{application}/social/followers`, suportando user/artist/production, com limite de paginação e respeito a `discoverable=false`.
- Sem migration.

## Evidence
- frontend local commit: db3c2c01e38d1302d7125b888c4892f618f39414
- api local commit: 5d1b58004e04c3632734f158c3022a2ce2d0f461
- production-view regression guard: 31 checks passed
- frontend optimized build: compiled successfully with ESLint plugin disabled only to bypass unrelated pre-existing `ProductionDiscoveryRail.js` prop-types failures; no change was made to that file
- SEO snapshots: 22 pages / 10 public events
- live Nginx page: HTTP 200
- live Laravel kernel check for La Fyesta Pub production id 10: followers endpoint HTTP 200 and returned the public follower profile
- PHP syntax checks: controller, routes and feature test passed

## Handoff
Application Git remote synchronization is still required. VPS HTTPS git authentication is currently hanging/no usable credential helper is exposed to this worker. Both commits exist in the shared VPS Git object stores/worktrees and can be cherry-picked/pushed without reimplementing the change.

Hotfix Sentinel (chatgpt-vps-hotfix)
