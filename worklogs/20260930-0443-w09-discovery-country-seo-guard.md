# Worklog — W09 Discovery SEO Automation

## Problem
The crawler snapshot global-readiness guard covered `event.country || "BR"` but did not detect the separate hardcoded `addressCountry: "BR"` emitted by discoverySchema. The generator therefore had an unguarded global-readiness regression path.

## Change
Added a dedicated assertion to `scripts/check-seo-snapshot-global-readiness.mjs` that rejects hardcoded BR country in discovery structured data.

## Evidence
- code commit: c816abfaa6dbdefa5bcf17f5cf108c7525b1d2c4
- reviewed diff: one new guard plus clearer event/discovery error messages.
- generator evidence: `generate-seo-snapshots.mjs` currently contains both `event.country || "BR"` and discovery `addressCountry: "BR"`, so the guard is intentionally red pending the actual global fix.
- VPS: petertecnetserver offline; pending_deploy_vps=true.
- build/runtime: not claimed; GitHub connector has no command runner.

## Economic impact expected
Protects organic discovery from geographically false structured data as Cutinapp expands beyond Brazil, reducing the risk of crawler metadata contradicting the actual event location.

## NEXT_ACTION
Fix the generator itself: remove invented country defaults, derive locale/timezone from configuration or event data, preserve external organizer identity, run the global-readiness guard, generate snapshots for a non-Brazil event, and inspect served JSON-LD after deployment.
