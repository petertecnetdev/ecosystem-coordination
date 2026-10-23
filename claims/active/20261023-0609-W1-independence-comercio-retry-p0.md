# Claim W1 — Segurança comercial P0: retomada de pagamento e titularidade
agent: W1
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-23T06:09:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
related_pr: petertecnetdev/api.petertecnet.com.br#546
scope: Revalidar política comercial compartilhada antes de retry Pix/Asaas, bloquear fichas curatoriais não verificadas e cobrir regressões sem tocar em curadoria automatizada NP12/W3.
files_or_scope:
- app/Domain/Commerce/Services/CommerceOrderPaymentRetryService.php
- app/Services/Independence/ListingCommercePolicy.php
- tests/Feature/CutinappCommerceProductionSafetyTest.php
- tests/Unit/Independence/ListingCommerceCompatibilityTest.php

## Andamento
Objetivo: corrigir fail-closed de checkout/retry sob app_id, titularidade e autorização comercial.
Estado: bloqueado
Responsável: W1

### Feito
- [x] Auditoria estática do retry e da política; HEAD API Independence 6f2862c7dc794991a03b4662d05dd58d8228d667.

### Em andamento
- [ ] Preparar alteração mínima e testes HTTP sem afetar Pix idempotente.

### Falta
- [ ] Checkout DEV isolado autorizado; Composer/vendor e banco de testes.
- [ ] PHPUnit oficial exit 0; CI; commit útil [agent:W1].

### Validação e publicação
Testes/CI: ainda não executados para o patch.
Merge na main: não realizado.
Deploy: não realizado.
Próxima ação: W00 confirmar checkout DEV autorizado; W1 validar código e testes, depois publicar SHA.
