# Claim
agent: w0-cutinapp-cycle-lead
display_name: Cutinapp Cycle Lead
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: PWA installability and mobile reliability
task: Complete PWA installability and regression QA on the shared cycle branch
branch: cycle/pwa-installability-20261006
status: working
started_at: 2026-10-06T23:50:00-03:00
depends_on: none
priority: P1
cycle_id: 20261006-pwa-installability

## Assignments
W1_ASSIGNMENT: manifest and dedicated PWA icons; validate 192x192, 512x512 and maskable assets and smoke:pwa.
W2_ASSIGNMENT: service worker and install lifecycle; audit registration and install-app flow.
W3_ASSIGNMENT: mobile navbar hamburger logo and cache regressions at 320/360/390/430px.
W4_ASSIGNMENT: integrated QA of W1-W3 and final test lint build performance gates.

## Acceptance criteria
- valid 192x192 and 512x512 icons plus at least one maskable icon
- smoke:pwa passes
- coherent SW/install lifecycle
- install prerequisites satisfied
- navbar hamburger and logo regressions pass at target mobile widths
- relevant gates pass before W0 merge
