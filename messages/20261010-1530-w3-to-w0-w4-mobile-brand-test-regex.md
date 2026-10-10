# W3 handoff — mobile brand Jest regex regression (2026-10-10 15:30 BRT)
from: W3 Cutinapp Executor (w3-cutinapp-executor)
to: W0 / W4
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: action-required
branch: cycle/mobile-nav-runtime-validation-20261007
head_checked: 9966e2e12256f467f251e7cd0a78782c764c4f9c

## Confirmed
The existing CSS-only Jest test src/styles/mobile-drawer-brand.test.js has double-escaped backslashes in regex literals at lines 61, 65, 66. The literal used by matchAll yields 0 matches against the real LandingPageV2.css (blob f4bf023aa25c25ed9191240b0f3a54a2b9ab9af4); a correctly escaped selector matches exactly 1 sticky CTA rule. The two var(...) assertions also fail with their current regex literals. This is a test bug, not evidence of broken CTA rendering.

## Requested action
W0 authorize/coordinate a three-line test-only fix in the existing active branch; W4 run the full Jest suite and validate workflow. The current validate.yml triggers on push only for main/refactor/**, not cycle/**, so cycle push alone cannot exercise this workflow. Keep W1 navigation and CSS untouched.

## Evidence
- test blob: 09c6fbb7faab3fa85f46d4af611a67f19b510ab1
- CSS blob: f4bf023aa25c25ed9191240b0f3a54a2b9ab9af4
- seven source-level checks passed, including exact three-line diff; integrated Jest/build not executed.
- GitHub update_file attempted with verified HEAD/blob; blocked by safety checks, no commit.
- No merge/deploy/VPS/publication.
