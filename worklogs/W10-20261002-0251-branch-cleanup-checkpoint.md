# W10 — Ecosystem Branch Cleanup Checkpoint — 2026-10-02 02:51 -03

## Run summary

| repo | branch_count_before | MERGED_THIS_RUN | DELETED_THIS_RUN | RECOVERED_THIS_RUN | branch_count_after | REMAINING | STALE_UNCLEAR | blockers |
|---|---:|---:|---:|---:|---|---|---|---|
| Cutinapp frontend | baseline 751 | 0 | 0 | 0 | not re-enumerated | incomplete | acquisition activation unique-useful branch still requires selective recovery; delete-ready refs still require physical ref deletion | W10 GitHub surface has no delete-ref action |
| API | baseline 622 | 0 | 0 | 0 | not re-enumerated | incomplete | WebhookReceipt/idempotency family protected | PR #539 is draft/high-risk; runtime guard missing remotely; PHPUnit environment lacks JWT secret; second review required before merge |
| Admin Center | baseline 3 | 0 | 0 | 0 | not re-enumerated | incomplete | inventory still pending | W08 must close Admin Center then reinforce API |
| PeterTecnet | baseline 197 | 0 | 0 | 0 | not re-enumerated | incomplete | superseded browser-matrix branch is delete-authorized | W10 GitHub surface has no delete-ref action |

## API high-risk checkpoint

W07 published new evidence after the previous W10 checkpoint. PR #539 (`w07/fix-mp-webhook-validation-20261001`) is open, draft, mergeable, and contains the recovered regression test requiring HTTP 422 when a Mercado Pago webhook omits `data.id`.

Independent W10 verification confirms the PR branch still has runtime code returning HTTP 200 `{ok:true}` when `data.id` is absent. Therefore the branch is **not merge-ready**.

W07 prepared a minimal local-only runtime correction (`a38d8f4e`) changing that path to HTTP 422. `php -l` and `git diff --check` passed locally. Targeted PHPUnit could not reach the assertion because the local test environment has no JWT secret. The local commit could not be pushed from that checkout because HTTPS GitHub credentials were unavailable there.

State: `REVIEWED -> RECOVERED/INTEGRATED (test only on remote PR; runtime fix local-only) -> TESTED (partial static checks only)`. **MERGED has not occurred.** Because this is financial/webhook code, second technical review remains mandatory before merge or retirement of any branch carrying exclusive work.

## Coordination

- W07: publish the one-line runtime guard onto PR #539 through an authenticated GitHub path, rerun CI, obtain second technical review, merge only if green, then retire historical webhook-validation refs after main verification.
- W08: finish Admin Center inventory/decisions, then reinforce API on a non-overlapping batch.
- W06: continue Cutinapp delete-ready execution and selective recovery of unique activation telemetry before historical deletion.
- W09: continue PeterTecnet safe-delete batches; `agent/np03/admincenter-browser-matrix` remains `DELETE_AUTHORIZED_BY_POLICY` until physical deletion and absence verification.

## Safety

No force-push, reset --hard, destructive clean, deploy, or VPS mutation performed. No branch was reported DELETED without physical ref removal and verification.
