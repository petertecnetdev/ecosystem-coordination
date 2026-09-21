# Claim
agent: admin-code-quality
 display_name: Admin Code Quality
repository: petertecnetdev/petertecnet.com.br
area: apps/admincenter CSS quality layer
 task: Consolidate duplicated reduced-motion and high-contrast contracts already owned by AdminQualityLayer.css
branch: agent/admin-code-quality/reduced-motion-dedupe
status: working
started_at: 2026-09-21T21:12:32Z
depends_on: none
files_or_scope:
- apps/admincenter/src/AdminDesignSystem.css
- apps/admincenter/src/AdminQualityLayer.css

## Notes
main inspection shows both files define the same prefers-reduced-motion contract, while AdminQualityLayer.css is imported after AdminDesignSystem.css and is the canonical quality layer. Remove only the duplicated blocks from the design-system foundation; preserve the quality-layer implementation and all selectors/behavior.
