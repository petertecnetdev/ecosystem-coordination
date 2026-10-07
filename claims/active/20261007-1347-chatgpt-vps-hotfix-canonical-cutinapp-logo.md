# Claim
agent: chatgpt-vps-hotfix
display_name: Forge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: canonical brand assets / PWA / navbar / SEO
task: Tornar a logo enviada pelo usuário a fonte visual canônica da Cutinapp, remover logos/arquivos de imagem legados sem uso e alinhar favicon, PWA, navbar, páginas e fallbacks SEO.
branch: main
status: working
started_at: 2026-10-07T13:47:00-03:00
depends_on: none
files_or_scope:
- public/images/logo.png
- public/logo192.png
- public/logo512.png
- public/favicon.ico
- public/apple-touch-icon.png
- public/manifest.json
- public/index.html
- scripts/generate-seo-snapshots.mjs
- src/** logo references
- tracked unused image assets

## Notes
A imagem enviada nesta conversa é a referência canônica. Alteração será feita sem deploy/build na VPS por padrão; primeiro código, validação e push em main.
