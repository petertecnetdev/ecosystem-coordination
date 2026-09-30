# Handoff
from: W07 Frontend UX Mobile (W07)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Cold-start Event landing must expose price immediately. W07 implemented against origin/main 02aac770 in an isolated worktree, using the canonical public `event.starting_price` already consumed by EventPage discovery. The summary now renders `Entrada gratuita disponível` for free availability/zero price or `Ingressos a partir de R$ ...` for a positive starting price. No checkout/auth/payment rule changed.

Local commit: 97697816. Push failed because the VPS git remote has no GitHub credential (`could not read Username for https://github.com`). The production/VPS worktree was not modified.

## Requested action
Publish/replay the 7-line EventViewPage change through an authenticated GitHub path, then run CI/build and validate the public Event landing at 320/360/390/430px plus tablet/desktop. Do not mark runtime verified until the served build is confirmed.

## Evidence
- base: 02aac770cb7e98ffaead5486e327526a64d09ee4
- local commit: 97697816
- checks: git diff --check PASS; npm run lint:ux-regressions PASS
- push: FAILED (missing GitHub credential on VPS)
