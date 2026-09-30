# W07 Worklog — PWA icon integrity
worker: W07 Frontend UX Mobile (w07-frontend-ux-mobile)
date: 2026-09-30T06:17:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P0 release gate

## Problem
`CURRENT_STATE.md` mantém PWA/installability como release gate. O manifest ainda não possui ícones reais 192/512/maskable. O smoke anterior verificava apenas strings em `sizes`, portanto um PNG de dimensão errada poderia passar se o manifest mentisse.

## Implementation
- `scripts/check-pwa-installability.js`: leitura segura do header IHDR de PNG;
- validação das dimensões físicas contra cada tamanho numérico declarado;
- falha explícita quando `type=image/png` aponta para conteúdo inválido;
- preservadas as verificações de start_url/scope/display, existência dos assets, SW e integração install-app.

## Evidence
- application commit/push main: 9cf5fdc8760f3f6aa4a8fb1487fde5f1efc0e774
- combined GitHub status: sem checks reportados no momento do fechamento
- VPS: petertecnetserver offline; nenhuma ação de deploy executada
- pending_deploy_vps: true
- BUILT: no
- DEPLOYED: no
- RUNTIME VERIFIED: no

## Economic / UX impact
Evita falso positivo de installability e reduz risco de publicar uma PWA que o Chrome Android rejeite ou apresente com ícone incorreto, protegendo ativação/retenção mobile.

## Pending
`public/manifest.json` continua com `/images/logo.png`, `sizes:any`, `purpose:any`. O gate não deve ser considerado resolvido sem PNGs oficiais 192x192, 512x512 e maskable 512 reais. Não foi criado ícone aproximado para não adulterar a identidade oficial.

## NEXT_ACTION
Usar o asset mestre oficial da logo para produzir os PNGs PWA corretos; atualizar manifest; rodar `npm run smoke:pwa`; quando runtime voltar, validar HTTPS, Service Worker controlling, `beforeinstallprompt`, instalação Chrome Android e modo standalone.
