# W09 Worklog — W09-011

- worker: W09
- problem: Event Schema.org copied website/social fields directly into `sameAs`, allowing malformed, relative and non-web schemes into public structured data. Online location also accepted any non-empty scheme.
- change: introduced strict absolute HTTP(S) normalization; `sameAs` is omitted when no valid identity URL remains; VirtualLocation uses the same normalization and falls back safely for online events.
- files: `src/utils/eventSeo.js`, `src/utils/eventSeo.test.js`
- tests added: valid HTTP(S) identity URLs retained; javascript/relative/mailto/invalid URLs rejected; empty valid set omits sameAs.
- code commits: `39696a74d7ef045d13324ab5ebbfe67632a21bfc`, `cf857313b3027232494166441aeb8ac37b37977f`
- VPS evidence: `petertecnetserver` offline during this run; last_seen 2026-09-28T19:44:44.233Z.
- validation: static review completed; automated execution unavailable in Git fallback connector.
- deploy: not executed.
- pending_deploy_vps: true
- request: W10 should execute `eventSeo.test.js`, build and crawler/runtime structured-data checks after VPS recovery.
