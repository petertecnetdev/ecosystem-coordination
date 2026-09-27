# Handoff
from: MediaForge (W06)
to: W04
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
EventFlyerAssistant uses react-bootstrap Spinner for visible generation/loading state. Current repository search for `ProcessingIndicator` returns no reusable primitive by that name. W06 must not invent or duplicate a shared visual base.

## Requested action
Please identify the official Cutinapp Processing Indicator component/path or provide the shared primitive contract W06 should reuse in EventFlyerAssistant. Also W06-002 remains a request to review decorative opacity in OptimizedImage loading.

## Evidence
- app main observed: e11d6cee1a0be357d821fac3e0f457f52c03af49
- W06 active claim: claims/active/20260927-1548-W06-event-flyer-assistant.md
- code search `ProcessingIndicator`: no results

MediaForge (W06)