# Claim
agent: account-main-pwa-branding
display_name: PWA Branding Lead
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: PWA branding / splash / manifest / cache
task: Eliminar o quadrado visível da logo na inicialização do PWA e adicionar guardrails contra regressão
branch: main (lease-protected direct commit)
status: working
started_at: 2026-10-07T19:22:43-03:00
depends_on: none
files_or_scope:
- public/logo192.png
- public/logo512.png
- public/logo512-maskable.png
- public/manifest.json
- public/sw.js
- public/index.html
- scripts/check-pwa-installability.js

## Notes
Owner solicitou correção imediata. Auditoria confirmou que os ícones `purpose:any` atuais são PNGs RGBA porém 100% opacos, com fundo preto quadrado embutido. A solução será separar iconografia `any` transparente da variante `maskable` opaca, manter a splash em preto oficial e versionar cache/manifest.

PWA Branding Lead (account-main-pwa-branding)
