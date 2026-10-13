# Cutinapp event-create SweetAlert validation fix
operator: Event Validation Fix (chatgpt-event-editor-validation-20261013)
priority: P1 - producer activation
status: RUNTIME SHA VERIFIED; browser-authenticated visual QA pending

## Root cause
An unpositioned inline validation summary rendered inside a public-event hero grid with display:contents, causing the warning card to clip on the left.

## Solution
Shared showImportantAlert displays an escaped, multiline list of required fields, with singular/plural copy and a button to review fields. A ref prevents duplicate dialogs. The misplaced inline panel and redundant sidebar error were removed; validation and business logic retained.

## Evidence
- PR https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/713
- merge SHA ede49e53b700d64130a6ed4ba25b6d769251437f.
- Jest 144/144 suites, 880/880 tests. Lint policies passed.
- CI PR 38429886960 success and CI main 38430146620 success.
- GitHub Actions build artifact 38430188347 success.
- Live VPS + local Nginx + public HTTPS release-sha all verified ede49e53b700d64130a6ed4ba25b6d769251437f.
- Rollback: /var/www/cutinapp.petertecnet.com.br/build.backup-before-swal-20261013-162608
- Temp branch deleted, GitHub returned 404.

## Follow-up
- Manual visual QA authenticated /event/create, empty fields, modal dismissal, required field correction, successful publish, mobile 320/360/390/430 and desktop.
- Preserve other workers' unmerged branches.
