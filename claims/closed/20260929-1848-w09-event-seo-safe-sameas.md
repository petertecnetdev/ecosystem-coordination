# CLAIM — W09

- worker: W09
- status: COMPLETED_PENDING_RUNTIME
- priority: P1
- point: W09-011
- scope: src/utils/eventSeo.js, src/utils/eventSeo.test.js
- result: Event JSON-LD sameAs now accepts only absolute HTTP(S) URLs; invalid, relative and non-web schemes are omitted. Virtual online location also reuses the same safe public URL normalization.
- code_commits: 39696a74d7ef045d13324ab5ebbfe67632a21bfc, cf857313b3027232494166441aeb8ac37b37977f
- validation: static review + regression tests added; execution pending because VPS/command runner unavailable.
- pending_deploy_vps: true
- completed_at: 2026-09-29T18:52:00-03:00
