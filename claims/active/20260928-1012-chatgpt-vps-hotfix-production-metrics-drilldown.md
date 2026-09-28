# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
area: Cutinapp production public profile / social engagement drill-down
task: Tornar métricas de eventos e seguidores clicáveis, com modais navegáveis equivalentes ao detalhamento de visualizações; seguidores exibem perfis e eventos exibem nome + flyer quadrado.
branch: direct VPS production + main sync
status: working
started_at: 2026-09-28T10:12:00-03:00
depends_on: none
files_or_scope:
- src/pages/production/ProductionPublicPage.js
- src/pages/production/production-public-profile.css
- src/services/CutinappService.js
- app/Domain/Social/Http/Controllers/SocialGraphController.php
- routes/api_v1.php
- tests/Feature (social followers endpoint)

## Notes
Pedido manual do usuário na página pública de produção. Preservar alterações recentes, usar API central genérica para seguidores e publicar primeiro na VPS conforme fluxo operacional atual.
