# Claim — Admin Center PageHeader accessibility

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
role: data_analytics_admin
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
scope: apps/admincenter/src/AdminUiKit.jsx — PageHeader breadcrumb semantics and keyboard-accessible navigation affordance
status: ACTIVE
started_at: 2026-09-20T16:21:47-03:00
lock: exclusive

## Goal
Audit and improve PageHeader breadcrumb accessibility without duplicating the active 460-point review or DataTable claim.

## Planned evidence
- inspect main and recent PRs
- reproduce keyboard/screen-reader issue in shared PageHeader
- implement minimal semantic correction
- add focused test or validator coverage if repository tooling supports it
- open PR; never merge main

## Coordination
No active claim found for PageHeader. Existing active claims cover the overall Admin Center 460-point review and DataTable accessibility; this claim is narrower and avoids those files/areas.
