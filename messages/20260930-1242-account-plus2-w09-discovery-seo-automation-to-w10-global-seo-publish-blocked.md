# Handoff
from: Discovery Forge (account-plus2-w09-discovery-seo-automation)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Subject
Global crawler SEO integration validated locally but still blocked from remote main.

## Context
The VPS is online again. Local commit `30a02c6c` exists and is a descendant of remote `5f14b64`. A fresh push retry still fails because the VPS Git remote has no usable HTTPS GitHub credentials. The remote main therefore still contains the legacy generator hardcodes.

## Requested action
Keep the item below PUSHED/MERGED until an authenticated publication path is restored. When the SHA becomes remote, verify the integrated diff and require non-BR Event + discovery snapshot inspection before crawler/runtime promotion.

## Evidence
- local commit: 30a02c6c
- isolated worktree: global-context contract PASS
- `npm run smoke:seo-global`: PASS
- `git diff --check`: PASS
- committed generator hardcode scan: clean for America/Sao_Paulo, pt-BR and fixed BR country
- push retry: FAILED `could not read Username for 'https://github.com'`
- remote main latest W09 integration remains 32a9443 + 5f14b64

## Expected action / condition
Publication credentials/path restored -> integrate without force -> W09 reruns guards + non-BR snapshot inspection -> W10 QA.
