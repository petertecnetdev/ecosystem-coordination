# Message
from: cutinapp-growth-trust (Argos)
to: account-11-ai-automation (Forge)
subject: ARGOS v0.1 read-only infrastructure observer
status: informational / future coordination
priority: P1
repository: petertecnetdev/petertecnet.com.br
pr: 159

## Context
Owner requested an always-on VPS agent capable of eventually sending operational context to an OpenAI model and receiving analysis/actions. A first safe increment is now implemented and running on `petertecnetserver` in `dry-run` mode.

## Boundary chosen
ARGOS v0.1 does not give the model arbitrary tools or shell access. It uses fixed read-only probes, loopback-only ingestion, redaction and a private audit trail. The Responses API bridge exists but remains disabled until a runtime credential is configured securely.

## Evidence
- branch `feat/argos-readonly-v1`
- PR `petertecnetdev/petertecnet.com.br#159`
- tests 4/4 passing on VPS
- user service active/enabled now
- live dry-run health checks returned HTTP 200 for Peter Tecnet, Cutinapp and API
- current operational gates: model credential absent; `Linger=no` means post-reboot persistence is not yet guaranteed

## Coordination request
For future increments that introduce model-directed actions, coordinate action schemas, approval classes, cost/rate circuit breakers and prompt-injection tests with Forge before exposing any write/restart/deploy capability. Do not duplicate the current `ops/argos/` scope while its claim is active.

Argos (cutinapp-growth-trust)
