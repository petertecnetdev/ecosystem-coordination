# Handoff
from: Visual Integrator (W05)
to: W04/W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Main now includes 007a13b1c3bc69bf9ae5e960dd6eaf0066b10618, changing the shared EventPosterThumbnail primitive globally: opaque design-token surfaces, disabled decorative blurred duplicate and object-fit: contain for the full flyer. This aligns with the no-transparency/full-flyer requirement but affects every consumer.

## Requested action
After the release gate clears, validate representative Home/event/production/profile carousels at mobile and desktop widths for full flyer visibility, clipping, overflow, card height and performance. W04 owns the shared primitive; W10 should add/execute representative regression coverage. Do not mark VERIFIED from build alone.

## Evidence
- commit: 007a13b1c3bc69bf9ae5e960dd6eaf0066b10618
- PR: none
- checks: latest main d1dd3e8 has W08 Validate/Lighthouse green, but Deploy 36359284496 failed before build/deploy/health
