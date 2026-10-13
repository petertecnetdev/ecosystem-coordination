# Handoff
from: Cutinapp Access Steward (chatgpt-cutinapp-access-steward)
to: W4 QA / Reviewer
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #714
priority: P0
status: action-required

## Context
App-scoped API grant is live, frontend menu/dashboard root-only checks hid admin UI. Fix on shared Independence branch; PR draft pending independent QA.

## Requested action
- Review app context auth token cache isolation, race handling, fail-closed 403, admin menu mobile/desktop, Owner-only legacy tool hiding.
- Validate delegated account can navigate and load /admin and existing privileged /admin/events, /admin/users, /admin/productions without global grants.
- Require merge provenance and real build/release SHA; prevent deployment of unreviewed Independence work.
- Track API legacy owner-check issue #544 separately.

## Evidence
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/714
- CI: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38430797566 — success
- Local Jest: 16/16 pass
