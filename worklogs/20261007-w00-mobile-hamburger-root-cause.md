# W0 / USER_CHAT — Mobile hamburger root-cause cycle

- date: 2026-10-07
- source: USER_CHAT repeated report
- priority: P0/P1 recurring essential mobile navigation
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- branch: cycle/mobile-nav-reliability-20261007
- pr: #706
- status: IMPLEMENTING / CI

## Root causes confirmed
1. Public landing `/` (logged out) used `LandingPageV2`; its responsive CSS hid desktop navigation under 991px without providing any hamburger replacement.
2. Internal navigation had accumulated multiple emergency/recovery layers around React-Bootstrap collapse.
3. Scroll shell could mark the top navbar `cut-mobile-nav--hidden`, while the menu state could still lock body scrolling, matching the user symptom “clicks, page freezes, menu does not appear”.
4. Main received an authoritative React portal drawer mounted directly under `document.body`, removing the drawer from navbar/page stacking contexts.

## Consolidated implementation
- Preserve the React portal drawer on internal navigation.
- Remove runtime import of `mobile-hamburger-emergency.css`.
- Load `mobile-hamburger-recovery.css` only once, last.
- Remove global `installMobileNavbarRecovery()` so global recovery JS no longer competes with the explicit React toggle + portal.
- Prevent Instagram-style navbar auto-hide while menu state is open.
- Add real public landing hamburger with explicit state, Escape handling, ARIA, full-screen mobile nav and touch targets.
- Normalize mobile drawer background to Cutinapp black.
- Add regression tests for auto-hide versus open menu.

## Validation evidence
- First CI attempt: 143 suites passed; only new test failed because this repository does not install the Jest DOM `toHaveClass` matcher.
- Assertion corrected to baseline `classList.contains`.
- Second CI: test phase passed; build/performance/Lighthouse still pending at this worklog write.

## Closure gate
Do not mark VERIFIED on commit/merge alone. Validate served behavior at 320/360/390/430px:
- public home hamburger visible;
- open/close;
- Escape;
- route navigation;
- internal portal after scroll/auto-hide;
- body scroll restored after close.

## Integration update — 2026-10-07
- PR #706 squash-merged into Cutinapp `main`.
- main commit: `60154ea27c00acfdc52f3a953733f4c53b2b92a9`
- final branch head before merge: `8596ae017c3f4606a53a4eee3a1b093635b3ffb5`
- PR Validate Cutinapp: SUCCESS.
- PR Lighthouse CI: SUCCESS.
- main Validate Cutinapp: SUCCESS.
- main Lighthouse CI: SUCCESS.
- deployment workflow started for exact main SHA `60154ea27c00acfdc52f3a953733f4c53b2b92a9`.
- final architecture: React state + body portal is the only mobile drawer implementation. Emergency CSS, global mobileNavbarRecovery JS and its old regression suite were removed; legacy Bootstrap collapse is explicitly non-interactive while the portal is open.
- public logged-out landing now also uses a body portal instead of a fixed drawer inside the backdrop-filter header.
- functional served-device closure gate remains open until deploy identity/health and W4 breakpoint/runtime validation pass.
