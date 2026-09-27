# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Profile conversion UX
task: Repair user profile cover image picker so the native library chooser opens reliably.
branch: fix/profile-cover-picker (coordination branch only; no duplicate implementation pushed)
status: completed
started_at: 2026-09-27T12:55:00Z
completed_at: 2026-09-27T13:09:38Z
depends_on: none
files_or_scope:
- src/pages/user/UserEditPage.js
- src/pages/user/UserEditPage.css

## Result
The reported production defect was confirmed: the served release was stale and the cover control did not open a reliable native file chooser. During implementation, concurrent commits landed on main before this agent pushed duplicate code. The existing main fix was adopted instead of duplicating it: e4f86d90178a8c0ca298fbbe0d56062fe4dbeb47 restores an explicit cover input ref/click path, and a3e0638fb3625156418e2c518096e373085a1066 makes the cover surface explicitly interactive.

The validated GitHub deploy for a3e0638 failed at the frontend environment-fetch step, so the public site remained on release 5a247f22. An operator-controlled emergency release was built from the exact current main SHA using the server's existing production frontend environment, with the same package-lock as production, then atomically activated with rollback protection.

## Evidence
- main implementation commits: e4f86d90178a8c0ca298fbbe0d56062fe4dbeb47, a3e0638fb3625156418e2c518096e373085a1066
- focused profile activity tests: 10/10 passed
- production build: compiled successfully; SEO snapshots generated
- built bundle contains `Selecionar imagem da capa`
- GitHub deploy run 36320983147 failed before build/deploy at `Fetch frontend build environment`
- emergency release activated: a3e0638fb3625156418e2c518096e373085a1066
- local nginx release identity: a3e0638fb3625156418e2c518096e373085a1066
- public HTTPS release identity: a3e0638fb3625156418e2c518096e373085a1066
- previous release retained for rollback: 5a247f22abc48277d9f09ebd3dbfe9dd3d9f5e03

## Follow-up
Repair the reusable GitHub deploy workflow's frontend environment-fetch path so future validated releases do not require an operator-controlled emergency activation.

Signed: Conversion Pilot (cutinapp-growth-conversion)
