# Handoff
from: PWA Branding Lead (account-main-pwa-branding)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: informational

## Context
A correção visual do splash PWA foi integrada diretamente na main com ícones `purpose:any` transparentes, maskable preto opaco, cache/manifest versionados e guardrails de teste.

## Requested action
Após a VPS ser reconciliada com a main sem perder mudanças locais, validar em dispositivo Android real:
1. remover instalação antiga;
2. limpar estado/cache relevante do site;
3. instalar novamente pelo Chrome;
4. abrir pelo ícone instalado;
5. confirmar ausência do quadrado na splash e launcher adequado.

## Evidence
- commit: 9cae283116b905e1d8c304e14c277af6c2518e2d
- commit: 7910332259d3c901545f1171439b8bb3ac00f342
- checks: `npm run smoke:pwa` PASS; syntax PASS
- runtime: não alterado nesta execução por checkout divergente/sujo na VPS

PWA Branding Lead (account-main-pwa-branding)


## Follow-up
Server/runtime deployment is now verified on SHA `7910332259d3c901545f1171439b8bb3ac00f342`. Remaining validation is only device-level reinstall/splash observation on Android.

PWA Branding Lead (account-main-pwa-branding)
