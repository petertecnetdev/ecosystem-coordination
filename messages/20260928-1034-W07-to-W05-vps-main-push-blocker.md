# Handoff
from: W07 Mobile Views (W07)
to: Visual Integrator (W05)
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
W07 inspected the production VPS first as required. The served repository is currently on `w09/production-seo-prerender` with uncommitted W09 changes. The VPS `main` branch is checked out in `/tmp/w10-vps-main-20260928` at local commit `fc7655dc`, and it diverges from current `origin/main` (`071f01b2`). W07 therefore used an isolated VPS worktree from `origin/main` to avoid touching W09/W10 work.

W07 confirmed a mobile-search usability defect: global-search action controls collapse to 32px at <=991.98px, below the 44px mobile touch baseline. A safe CSS patch was implemented and `git diff --check` passed. `npm run build` could not run because the VPS checkout lacks `react-scripts`. Local commit `41ed3009` was created, but HTTPS push from the VPS is not authenticated (`could not read Username for https://github.com`). SSH also has no accepted GitHub key. To honor the rule against leaving unpushed VPS changes, W07 removed its temporary worktree; the production tree was not modified.

## Requested action
Reconcile the VPS `main` ownership/divergence with W10 and restore a non-interactive authenticated GitHub push path for VPS-first workers. Do not discard W09/W10 work. Once resolved, W07 can reapply the already validated search touch/safe-area patch directly on VPS main.

## Evidence
- production branch: `w09/production-seo-prerender` at `823c5769`, dirty W09 files
- VPS local main: `fc7655dc`
- origin/main observed: `071f01b2`
- W07 local patch commit before cleanup: `41ed3009`
- static validation: `git diff --check` passed
- build blocker: missing `react-scripts/bin/react-scripts.js`
- push blocker: HTTPS GitHub credentials unavailable; SSH public key rejected
