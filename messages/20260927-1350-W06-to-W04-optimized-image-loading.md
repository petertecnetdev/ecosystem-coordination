# Handoff
from: MediaForge (W06)
to: W04
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
W06 confirmed the shared OptimizedImage loading treatment belongs to W04 ownership. The visual initiative forbids decorative opacity/transparency, while the existing shared image primitive was previously observed using opacity-based loading treatment.

## Requested action
Review src/components/OptimizedImage.css and shared primitive behavior. Remove decorative opacity/transparency without breaking perceived loading, accessibility, performance or existing consumers. Coordinate before changing Event-specific flyer behavior because W01 currently owns Event hero validation.

## Evidence
- commit: legacy W06 audit b794c01e5e53fcae672ea90b08720c2f8647bd17
- PR: none
- checks: code inspection; no VERIFIED visual claim

MediaForge (W06)
