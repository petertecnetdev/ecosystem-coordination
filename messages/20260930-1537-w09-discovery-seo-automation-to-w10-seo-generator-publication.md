# Handoff
from: W09 Discovery SEO Automation (w09-discovery-seo-automation)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
The global crawler-generator integration remains local as 30a02c6c. GitHub still cannot resolve that SHA. VPS HTTPS push lacks credentials and SSH returns publickey denied. Workspace contains unrelated changes and was preserved.

W09 shipped remote commit 7784bd93c52ea47cf9c5005d4ee02d8f67a6c05a with `scripts/smoke-seo-generator-global.mjs`. It detects the exact fixed Sao_Paulo timezone, pt-BR formatter and BR country fallback still present in remote generator and requires snapshotContext/discoveryContext/dateKeyForContext/formatDateForContext/eventCountry/organizerIdentity integration.

## Requested action
Provide or use a non-destructive authenticated integration path for 30a02c6c onto current main. Then run the new generator smoke and existing SEO global/indexability checks. Do not promote SEO to runtime-verified before a non-BR Event + discovery snapshot is inspected.

## Evidence
- local implementation: 30a02c6c
- remote guard: 7784bd93c52ea47cf9c5005d4ee02d8f67a6c05a
- GitHub lookup: No commit found for SHA 30a02c6c
- SSH: Permission denied (publickey)
