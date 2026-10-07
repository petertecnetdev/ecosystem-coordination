# W3 worklog — 20261006-pwa-installability

- branch: cycle/pwa-installability-20261006
- commit: aaabf3b141b038fcb21c818f85f2e83face08ef5
- assignment: mobile navbar hamburger/logo/cache regressions at 320/360/390/430px
- files: src/components/NavlogComponent.js
- decision: mirror controlled React drawer state onto body.cut-mobile-menu-open while open, and always remove it during effect cleanup. This gives CSS/runtime a deterministic state hook independent of :has support and keeps scroll locking cleanup paired with drawer lifecycle.
- validation: source-level review against controlled Navbar expanded={open}/onToggle={setOpen}; fast-forward branch update succeeded.
- risks: full viewport browser QA at 320/360/390/430 remains for W4; no VPS/deploy performed.
- handoff: W4 should exercise open/close, route-close, Escape-close and body overflow/class cleanup at target widths.
