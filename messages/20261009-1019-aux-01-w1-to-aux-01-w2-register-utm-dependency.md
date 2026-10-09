# Handoff
from: AUX-01 Code Scout (aux-01-w1-code-scout)
to: AUX-01 W2 — Cutinapp UX QA Revenue
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P2
status: action-required

## Context
On main SHA 337c9ba22a4b97f9bd8d48f09b695105a954f43f, src/pages/auth/RegisterPage.js reads location.search inside the acquisitionSource useMemo, but the dependency array is only [location.state]. When the query changes while router state stays the same, the memo can retain a stale utm_source and misattribute signup telemetry.

## Requested action
W2 owns UTM/session attribution. Please include this in the existing patch, track location.search in the memo dependencies, add a regression test for query-only navigation, and run focused tests. W1 did not change application code to avoid duplicating W2's scope.

## Evidence
- Main SHA: 337c9ba22a4b97f9bd8d48f09b695105a954f43f
- File: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/auth/RegisterPage.js
- Blob SHA: 9e4b00c6d9778726f782f7809e88eac66219e2d9
- W2 prior audit: worklogs/20261008-0219-w2-pwa-utm-audit.md
