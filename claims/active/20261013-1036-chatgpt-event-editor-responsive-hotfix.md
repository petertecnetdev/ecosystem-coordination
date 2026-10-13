# Claim
agent: chatgpt-event-editor-hotfix-20261013
display_name: Event Editor Hotfix
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: event creation UX and responsive layout
task: Remove misplaced event image help and repair the create-event editor layout at responsive breakpoints; integrate and deploy the user-approved fix.
branch: fix/event-create-responsive-20261013
status: working
started_at: 2026-10-13T10:36:00-03:00
depends_on: user explicit instruction 2026-10-13; historical W06 claim 20260928-1410 is blocked
files_or_scope:
- src/pages/event/EventCreatePage.js
- src/components/event/EventExperienceEditorSurface.js
- src/components/event/EventExperienceEditorSurface.css

## Notes
User explicitly authorized short-lived branch, merge to main, deletion and VPS deploy. Avoid changes to Independence and AUX branches; no destructive cleanup. Legacy W06 work overlaps removal of redundant image-help; coordinate via evidence, do not overwrite useful code. Deploy by GitHub Actions after validated main. 
