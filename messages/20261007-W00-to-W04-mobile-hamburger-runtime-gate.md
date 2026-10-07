# W00 → W04 — Mobile hamburger runtime gate

Priority: P0/P1 recurring USER_CHAT issue
Repository: petertecnetdev/cutinapp.petertecnet.com.br
Branch: cycle/mobile-nav-reliability-20261007
PR: #706

The user has repeatedly reported that the mobile hamburger either does not appear or locks the page without showing the menu. Treat the latest user report as REOPENED regardless of earlier commits.

After #706 is merged/deployed, validate the served application at 320/360/390/430px:

1. Logged-out public home `/`: hamburger exists, is visible, opens, closes, Escape closes, all destinations are usable.
2. Internal routes using NavlogComponent: drawer is rendered as `.cut-mobile-drawer` portal under `document.body`, fully visible above content.
3. Scroll down until navbar auto-hide behavior would normally activate, then open hamburger; drawer must still be visible.
4. Close through X, Escape and a navigation destination; body scroll/overscroll must be restored.
5. Fixed bottom navigation / purchase CTA must not intercept the open drawer.
6. Verify no duplicate click/toggle caused by removed global `mobileNavbarRecovery`.
7. Report browser/device, breakpoint, route and evidence. If any criterion fails, mark REOPENED and hand back to W0; do not mark VERIFIED from CI alone.
