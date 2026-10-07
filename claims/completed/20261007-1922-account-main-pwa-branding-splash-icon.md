# Claim
agent: account-main-pwa-branding
display_name: PWA Branding Lead
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: PWA branding / splash / manifest / cache
task: Eliminar o quadrado visível da logo na inicialização do PWA e adicionar guardrails contra regressão
branch: main
status: completed
started_at: 2026-10-07T19:22:43-03:00
completed_at: 2026-10-07T19:31:00-03:00
depends_on: none
files_or_scope:
- public/pwa-icon-192.png
- public/pwa-icon-512.png
- public/manifest.json
- public/sw.js
- public/index.html
- scripts/check-pwa-installability.js

## Result
- Criados ícones `purpose:any` dedicados com matte externo transparente, preservando a logo oficial.
- Mantido `logo512-maskable.png` opaco com matte #000000 para Android/adaptive icon.
- `theme_color` e `background_color` confirmados em #000000.
- Manifest e service worker receberam versão nova para evitar reaproveitamento do asset quadrado antigo.
- Guardrail `smoke:pwa` agora falha se ícone `any` voltar a ter canto opaco, se o maskable perder o matte preto, ou se as cores de launch divergirem.

## Evidence
- implementation: 9cae283116b905e1d8c304e14c277af6c2518e2d
- test fix: 7910332259d3c901545f1171439b8bb3ac00f342
- check: `npm run smoke:pwa` PASS em clone limpo da main
- check: `node --check scripts/check-pwa-installability.js` PASS
- runtime: NOT VERIFIED / VPS não alterada porque o checkout de produção está ahead 1, behind 4 e possui alterações locais não commitadas

## Next action
Após reconciliar/deployar a VPS com segurança, reinstalar o PWA no Chrome Android e validar splash/launcher em instalação limpa.

PWA Branding Lead (account-main-pwa-branding)
