# Claim exclusivo W3 — contrato HTTP de app e emissão negada em self-service não aprovado (Independence P0)

agent_id: W3
owner: W3 — Desbloquear API e CI Independence
status: DONE_REVIEWED
started_at: 2026-10-30T11:30:00-03:00
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
issue: petertecnetdev/ecosystem-coordination#10
pr: petertecnetdev/api.petertecnet.com.br#546
head_at_claim: 97abfe783649ca372f679d7ed2ea4bfb10ec19a6
files_or_scope:
- tests/Feature/CutinappApplicationOwnershipTest.php
blob_at_claim:
- tests/Feature/CutinappApplicationOwnershipTest.php: f4909db2c192028e7f599dc2b63bfc779a8a3899

## Exclusividade e ACEITO W3
Revisados COMMANDS.md, issues #10/#12, 183 entradas em claims/active, quatro handoffs, despacho W00 20261030-1056, PRs API #546/React #715/Admin #4 e CI #41064583758. Nenhum claim nominal sobre este teste encontrado; claim W1 de EventPassService.php e teste próprio permanece exclusivo, W2 é React e Atlas/Genre reservam EventManagementController.php. **ACEITO W3** somente para o arquivo, HEAD e blob acima, sem cessão presumida de qualquer outro escopo.

## Objetivo e critérios
Ajustar teste HTTP legado de isolamento por aplicação que esperava 201/QR para evento recém-criado sem revisão humana. Manter verificações de app_id para produção, evento, ingresso e vínculo de produtor; exigir HTTP 403 para retirada por participante em ficha self-service sem autorização comercial e ausência de EventPass/QR. Não alterar ListingCommercePolicy, EventPassService, controller, rotas, migrations ou testes de outro owner. A cobertura de emissão positiva exigirá fixture separado com aprovação humana, grants auditáveis por app e autorização comercial independente.

## Evidência inicial
API HEAD 97abfe783649ca372f679d7ed2ea4bfb10ec19a6; teste blob f4909db2c192028e7f599dc2b63bfc779a8a3899. CI oficial #41064583758: 736 PASS/20 FAIL/3 SKIP, exit 1; teste atual falha em POST /api/cutinapp/passes/claim/{ticket} com esperado 201 e recebido 403. MySQL dirigido já verde, não repetir setup.

## Gates
Commit real em Independence, CI no SHA exato, QA W4 independente. Preservar OPENAI_SAFETY_CHECKS, sem merge, main de produto, deploy ou novas branches/automações.

## Entrega W3 — 30/10/2026 ~11h31 BRT
- **COMMIT REAL de teste:** `028d5dc5da75c2794689a4d80a68e62cbb2d61db` na API `Independence`, PR #546.
- **Arquivo exclusivo:** `tests/Feature/CutinappApplicationOwnershipTest.php`, blob `f4909db2c192028e7f599dc2b63bfc779a8a3899` → `e89840b8a14ca03b3903ee006c39d631e16c33de`.
- O teste mantém asserts de app_id de produção/evento/ticket e vínculo do produtor; para participante sem aprovação comercial exige HTTP 403, ausência de `pass.token` e inexistência de `event_passes` para app/usuário/evento/ticket. Removeu expectativa de vínculo `participant` decorrente de emissão que deve ser negada. Nenhum guard de produção foi alterado.
- **CI no SHA:** workflow API CI #41072181823 disparado, inicialmente `in_progress`; resultados finais a registrar. Testes locais não executados (exit N/A).
- **Escopo não tocado:** `OrganizationService.php` sob bloqueio OPENAI_SAFETY_CHECKS; `EventManagementController.php` Atlas/Genre; W1 EventPassService/ListingCommercePolicy; main/merge/deploy.
- **Próxima ação única:** W4 revisar o SHA e confirmar o contrato fail-closed no CI oficial, sem liberar merge antes do gate integral.

## Validação CI final — SHA 028d5dc5 (30/10/2026 11h33 BRT)
- Workflow oficial API CI #41072181823, job validate #124118854613 **FAILURE/exit 1**: **737 PASS / 19 FAIL / 3 SKIP**, 5.556 asserções. Comparado ao HEAD anterior: **+1 PASS / -1 FAIL**. `CutinappApplicationOwnershipTest` consta **PASS** e sintaxe PHP do arquivo passou. Arquitetura segue 2 FAIL, gate exit 1, não silenciado.
- Job MySQL 8 efêmero #124118854926 **SUCCESS/exit 0**: **38/38 PASS**, 389 asserções, migrations/rollback/remigrate conforme job. Não houve novo setup de MySQL fora do CI disparado automaticamente.
- API PR #546 HEAD `028d5dc5da75c2794689a4d80a68e62cbb2d61db`; main...Independence **278 ahead/0 behind** na verificação.
- Testes locais W3: **NOT_RUN**, exit N/A. QA W4 neste SHA: **NOT_RUN**; merge/deploy/main: **não realizados**.
- Estado: **REVIEW**. Próxima ação única: **W4** revisar este diff e o CI no SHA exato; manter veto à integração até o gate geral verde.

## Encerramento do claim — 30/10/2026 12h30 BRT
- W4 aprovou o contrato negativo no comentário https://github.com/petertecnetdev/ecosystem-coordination/issues/10#issuecomment-6525533831, CI #41072194839 no SHA 028d5dc5: teste PASS, 737 PASS/19 FAIL/3 SKIP geral, MySQL 38 PASS/389 assertions. O veto global ao merge continua.
- **Status: DONE_REVIEWED**, arquivo liberado para novos claims explícitos; nenhuma alteração adicional neste teste. Próximo escopo W3 sob claim distinto `20261030-1230-W3-community-selfservice-failclosed-test.md`.
