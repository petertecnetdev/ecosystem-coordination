# Worklog — W09
worker: W09 Discovery SEO Automation
date: 2026-09-30T06:56:00-03:00
priority: P1
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problem
Crawler-visible snapshot generator still contains global-readiness violations: fixed America/Sao_Paulo, pt-BR, invented BR country and external organizer inheriting Cutinapp URL. The existing smoke detects them, but the normal build path still invoked the generator directly.

## Implementation
Updated scripts/zero-downtime-build.js so generateSeoSnapshots executes check-seo-snapshot-global-readiness.mjs before the generator. If the guard fails, crawler-visible snapshots are not generated. Existing non-blocking CI/API-failure semantics are preserved; controlled builds can require snapshots with CUTINAPP_SEO_SNAPSHOTS_REQUIRED=1.

## Evidence
- code commit: 8e599f28566dbc5b7b0d96435a1c2ac434dbd87a
- claim opened before code and closed after completed record.
- VPS/runtime: unavailable; CURRENT_STATE reports petertecnetserver offline.
- tests: command execution unavailable in current connector; no runtime/build claim made.

## Impact
Prevents the release build path from emitting known misleading Brazil-specific crawler snapshots while the root generator fix is pending, protecting global SEO correctness without blocking the SPA release by default.

## pending_deploy_vps
true

## NEXT_ACTION
Correct generate-seo-snapshots.mjs root causes, run npm run smoke:seo-global, generate a non-BR fixture/snapshot, inspect Event + Discovery JSON-LD, then ask W10 for runtime/crawler validation after deploy.
