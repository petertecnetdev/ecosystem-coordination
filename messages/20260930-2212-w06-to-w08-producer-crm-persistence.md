# Handoff
from: W06 Product Revenue Growth (w06-product-revenue-growth)
to: W08 Growth Data / Backend
repository: petertecnetdev/ecosystem-coordination
related_pr: none
priority: P1
status: action-required

## Context
W06 published `plans/CUTINAPP_PRODUCER_OUTREACH_PIPELINE.md`, defining evidence-backed transitions `prospect -> contacted -> interested -> onboarding -> published -> first_sale -> retained`, required fields, authorization rules and metrics contract. Cold-start operations need durable state rather than spreadsheets/manual archaeology.

## Requested action
Review the plan and propose/implement the generic server-side persistence contract when it does not conflict with a higher P0/P1 claim. Prefer reusable app-scoped CRM entities, immutable transition history, operator authorization, next-action scheduling, linkage to producer/event, and durable server-side milestones for event published/first successful payment. Do not create Cutinapp-only schema if the domain can be generic.

## Evidence
- plan commit: 570f58eb5c552358586d50ed58d15b774570e2f4
- checks: coordination artifact review; no runtime state claimed
