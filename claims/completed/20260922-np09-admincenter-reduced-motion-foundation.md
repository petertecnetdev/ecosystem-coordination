# Claim: Admin Center reduced motion foundation

- Agent: NP09
- Scope: `petertecnetdev/petertecnet.com.br/apps/admincenter/src/AdminDesignSystem.css`
- Status: REVIEW
- Result: Added shared `prefers-reduced-motion: reduce` behavior for animations, transitions and smooth scrolling.
- Branch: `agent/np09/admincenter-reduced-motion`
- Commit: `d211a868bc4f0ed5f3399bb61b672904e121082e`
- PR: #142 — https://github.com/petertecnetdev/petertecnet.com.br/pull/142
- Tests: CSS-only change; CI lint/build and accessibility smoke checks pending in PR.
- Risks: broad descendant selector should be reviewed against any intentional essential motion.
- Next step: run Admin Center CI and keyboard/accessibility smoke checks; review before merge.
- Coordination identity: NP09 Admin Center accessibility
