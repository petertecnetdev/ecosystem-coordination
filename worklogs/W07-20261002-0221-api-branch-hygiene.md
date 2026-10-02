# W07 — API Branch Hygiene — 2026-10-02 02:21 -03

MERGED_THIS_RUN: 0
DELETED_THIS_RUN: 0
RECOVERED_THIS_RUN: 0
HIGH_RISK_REVIEWED: 1
STALE_UNCLEAR: WebhookReceipt/idempotency family remains protected pending complete model+migration+receiver evidence.
REMAINING: API branch hygiene remains incomplete.

## High-risk financial review
PR #539 (`w07/fix-mp-webhook-validation-20261001`) contains the recovered regression test requiring HTTP 422 when Mercado Pago webhook payload lacks `data.id`.

Confirmed current runtime in `app/Domain/Finance/Http/Controllers/PaymentProviderController.php` still returns HTTP 200 `{ok:true}` when `data.id` is absent.

Prepared minimal runtime correction locally on the authorized remote machine:
- replace success return for missing `data.id` with `abort(422, 'Identificador do pagamento ausente.')`;
- `php -l` passes;
- `git diff --check` passes;
- local commit: `a38d8f4e` (`fix(finance): reject malformed Mercado Pago webhooks`).

Targeted PHPUnit execution could not reach the assertion because the local test environment has no JWT secret (`Tymon\\JWTAuth\\Exceptions\\JWTException: Secret is not set`). This is an environment/configuration blocker, not evidence that the webhook assertion failed.

Push from the remote checkout failed because that machine has no GitHub HTTPS credentials (`could not read Username for https://github.com`). Therefore commit `a38d8f4e` is LOCAL ONLY and PR #539 remains at remote HEAD `6c625920...`; no merge was attempted.

## Safety
No force push, reset --hard, clean, deploy, VPS mutation, branch deletion, or financial merge was performed.

## NEXT_ACTION
Publish the one-line runtime correction to PR #539 through an authenticated GitHub path, rerun CI, require second technical review, and merge only if CI/review are green. After confirming the fix/test in main, retire the historical webhook-validation branch per hygiene protocol. Continue protecting WebhookReceipt family until complete dependencies are proven.