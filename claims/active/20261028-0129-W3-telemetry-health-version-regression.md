# Claim exclusivo W3 — regressão de versão do monitor de telemetria no API CI

agent: W3
display_name: W3 — Independence API e CI
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: em-andamento
started_at: 2026-10-28T01:29:39-03:00
depends_on: ecosystem-coordination#12; API CI #40627090358
area: regressão funcional PHPUnit de monitoramento administrativo, sem alteração de runtime
files_or_scope:
- tests/Feature/TelemetryHealthTest.php

## Evidência e exclusividade
- API CI #40627090358 no SHA `c21da37f39496c7667ab3706e37fc001ebb07e7f`: `TelemetryHealthTest` FAIL, esperava versão `3.3.0`, mas contrato de `config/telemetry.php` define `3.3.3`.
- DEV W3 autorizado `/home/petertecnet/work-w3-independence-api`, branch `Independence`, HEAD atualizado `df6f51bc731838b24fc5090c68952c7b83a05180`, blob do teste `08315a021903ac7c4a33600829d35ca75fdb7d69`.
- PHPUnit isolado reproduziu 1 FAIL/5 assertions, exit 1, em `tests/Feature/TelemetryHealthTest.php:87`.
- Auditoria read-only de `claims/active` não encontrou claim explícito para este teste. Claim do agente Beacon restringe-se a `InteractionController.php`, `FrontendTelemetryService.php` e seu teste unitário; nenhum desses arquivos será tocado. Claim W1 financeiro, W03 RBAC e NP12 curadoria permanecem intocados.
- Se surgir claim concorrente ou edição de terceiro, suspender imediatamente e solicitar handoff.

## Entrega esperada
Atualizar exclusivamente o teste para usar a versão canônica de `config('telemetry.frontend_version')` nos eventos/headers/asserções, sem fixar número antigo nem relaxar o contrato. Preservar a detecção `sdk_outdated` para clientes realmente desatualizados com regressão específica, se viável. Executar PHPUnit isolado e regressões relacionadas exit 0, publicar commit real `[agent:W3]` em português na branch existente e validar CI no SHA exato. Não alterar runtime, produção, gateway, MySQL, /var/www, W1, NP12, main, branches, merge/deploy nem OPENAI_SAFETY_CHECKS.

## Estado
Em andamento: claim criado antes de qualquer edição; próximo passo testar, implementar e validar.
