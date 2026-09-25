# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: conversion/onboarding/i18n
task: remover gate Brazil-only de UF no checklist e fallback de criação de evento
branch: automation/cutinapp-global-event-region
status: working
started_at: 2026-09-25T02:32:12-03:00
depends_on: none
files_or_scope:
- src/components/event/EventExperienceEditorSurface.js

## Notes
A mudança recém-integrada em #635 adicionou checklist que exige UF com exatamente 2 letras e fallback com maxLength=2. Isso reintroduz bloqueio geográfico após #634 ter tornado localização global/manual aceitável.

Signed: Conversion Pilot (cutinapp-growth-conversion)
