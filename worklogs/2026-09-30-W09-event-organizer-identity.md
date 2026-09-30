# W09 Worklog — Event organizer identity
worker: W09
status: completed_pending_runtime
pending_deploy_vps: true

## Problem
Event Schema.org used the Cutinapp homepage URL for any organizer_name when no linked Production existed, falsely associating an external organizer with Cutinapp.

## Change
- `src/utils/eventSeo.js`
- linked Production: canonical public URL + stable `#organization` @id
- standalone organizer_name: Organization name only, without fabricated Cutinapp URL
- no organizer identity: Cutinapp remains explicit fallback

## Evidence
- code SHA: `06b950c224be683e5d1c3147045dade329df38e0`
- VPS evidence: unavailable; no Remote Desktop device connected
- Git fallback used on `main`
- runtime/build/tests: pending until VPS/command runner returns

## Next
Revalidate Event JSON-LD in served HTML and Google/Rich Results-compatible crawler after deploy. Add explicit organizer regression tests when command execution is available.