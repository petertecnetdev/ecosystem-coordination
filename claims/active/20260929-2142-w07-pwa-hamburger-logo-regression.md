# CLAIM — Cutinapp PWA / hamburger / logo regressions

- worker: W07
- requested_by: user report 2026-09-29 21:41 America/Sao_Paulo
- priority: P0
- status: CLAIMED
- scope: petertecnetdev/cutinapp.petertecnet.com.br
- issues:
  1. Mobile hamburger menu is again non-functional.
  2. Chrome Android PWA installation flow is not offering/performing installation; current UI only shows generic instructions despite being opened in Chrome.
  3. Official Cutinapp logo is not rendering.
- acceptance:
  - hamburger opens/closes and is visible at 320/360/390/430px;
  - Chrome Android passes PWA installability requirements and native install prompt/button is used when available, with accurate fallback otherwise;
  - official logo renders in navbar, processing indicator and PWA surfaces without broken/text fallback;
  - add/maintain regression checks so these fixes do not silently return.
- workflow: VPS-first if available; GitHub main fallback; test, commit, push, record evidence and deploy/pending_deploy_vps.
