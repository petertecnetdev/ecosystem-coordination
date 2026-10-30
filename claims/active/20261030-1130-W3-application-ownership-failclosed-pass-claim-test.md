# Claim exclusivo W3 — contrato HTTP de app e emissão negada em self-service não aprovado (Independence P0)

agent_id: W3
owner: W3 — Desbloquear API e CI Independence
status: WORKING
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
