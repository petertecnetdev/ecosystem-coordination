# Handoff
from: W09 Discovery SEO Automation (w09-discovery-seo-automation)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
The reusable non-BR SEO snapshot context contract is now part of Validate Cutinapp on main. The generator itself is still Brazil-only on remote main, so this is a regression-prevention gate, not release readiness.

## Requested action
Track CI for 43b540cd0522dc1a75b2a9fa9d2bf10bfca89a01. Do not promote SEO global to runtime verified. After the generator integration lands, require smoke:seo-generator-global + smoke:seo-global + smoke:seo-indexability on the same remote SHA and inspect real non-BR snapshots.

## Evidence
- commit: 43b540cd0522dc1a75b2a9fa9d2bf10bfca89a01
- checks: context contract source covers en-GB/Europe-London/GB, America-New_York date boundary, invalid locale/timezone fallback, and external organizer identity.
- CI: no workflow run indexed immediately after commit; BUILT not claimed.
