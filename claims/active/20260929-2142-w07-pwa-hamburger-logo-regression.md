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

## REOPENED — 2026-10-07 14:06 America/Sao_Paulo
- source: USER_CHAT (repeated report; latest report supersedes earlier “fixed” assumptions)
- current_owner: W0 / cycle mobile-nav reliability
- active_branch: `cycle/mobile-nav-reliability-20261007`
- pr: #706
- hamburger_status: REOPENED
- root_cause_findings:
  1. `LandingPageV2` hid desktop links on mobile without providing a hamburger/menu replacement.
  2. Internal navigation accumulated competing recovery CSS/JS around React-Bootstrap collapse and scroll auto-hide.
  3. Current authoritative direction is a React portal drawer mounted under `document.body`, outside navbar/page stacking contexts.
- corrective_action:
  - preserve portal drawer;
  - remove obsolete global mobile recovery runtime and duplicate/emergency CSS loading;
  - prevent shell auto-hide from winning while menu is open;
  - add a real public-home hamburger;
  - add regression coverage.
- closure_gate: DO NOT mark hamburger VERIFIED from commit/PR/build alone. Validate served behavior at 320/360/390/430px for public home and internal pages: open, close, Escape, route navigation, post-scroll/auto-hide opening, and body-scroll restoration.
