# Claim
agent: aux-02-w3-integrations
display_name: Reliability Forge
repository: petertecnetdev/api.petertecnet.com.br
area: Messaging / post-persistence transport reliability
task: Prevent Reverb/Pusher, queued engagement dispatch, and in-app notification transport failures from turning an already-persisted Direct message into HTTP 500; add regression coverage.
branch: agent/aux02-w3/direct-broadcast-failure-isolation
status: working
started_at: 2026-10-09T10:02:31-03:00
depends_on: none
files_or_scope:
- app/Domain/Messaging/Services/MessagingService.php
- tests/Feature/MessagingEmailNotificationTest.php

## Notes
P0 evidence: issue #533 remains open. Current main SHA at claim time: 14447fa8c6d038e8ce007e4ebfab0dfd5dea97f1. MessagingService::send() persists the message before deliverMessage(), but broadcast() calls event(new MessagingRealtimeEvent(...)) without catching transport exceptions; deliverMessage() queues engagement and in-app notification without isolating their failures. Existing regression test test_notification_failure_never_rolls_back_direct_message() currently expects the exception to propagate, preserving the broken HTTP 500 behavior. PR #537 adds email-flow coverage but does not change this runtime behavior. This claim is limited to best-effort post-persistence transport boundaries and tests; no VPS/deploy or payment behavior changes.