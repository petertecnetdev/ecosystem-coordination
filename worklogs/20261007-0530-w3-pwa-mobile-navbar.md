# W3 worklog — 20261006-pwa-installability

- worker: W3
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- branch: cycle/pwa-installability-20261006
- priority: P1
- assignment: mobile navbar hamburger/logo/cache regressions at 320/360/390/430px
- commit: 26cfc0da9df86d31046b7541170c42b7909eee16

## Implementation
Revalidated the controlled React-Bootstrap navbar after the accumulated W2 commit. Fixed keyboard/drawer lifecycle so Escape now closes both any active dropdown and the controlled mobile drawer. This aligns keyboard behavior with route-change closeMenu and guarantees the existing body scroll-lock cleanup runs when Escape is used.

## Files
- src/components/NavlogComponent.js

## Checks
- active claim discovered from claims/active and validated status=working
- branch compare after write: ahead=3, behind=0
- verified updated source contains setActiveDropdown(null) + setOpen(false) on Escape
- reviewed mobile-hamburger-recovery.css, mobile-hamburger-emergency.css, mobileNavbarRecovery.js and advanced-navbar.css for drawer/touch behavior

## Risks / pending
- Browser viewport QA at 320/360/390/430 remains W4 integrated gate.
- Multiple historical hamburger recovery layers remain technical debt; do not remove during this P1 cycle without browser regression coverage.
