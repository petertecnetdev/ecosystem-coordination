# Claim exclusivo W3 — testes HTTP de rascunho/publicação de eventos (Independence P0)

agent_id: W3
owner: W3 — Desbloquear API e CI Independence
status: WORKING
started_at: 2026-10-30T10:33:00-03:00
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
issue: petertecnetdev/ecosystem-coordination#10
pr: petertecnetdev/api.petertecnet.com.br#546
head_at_claim: 689c4bec63cac7e3e88a66df93c1f9f56046245b
files_or_scope:
- tests/Feature/CutinappEventLifecycleTest.php
blob_at_claim:
- tests/Feature/CutinappEventLifecycleTest.php: 92f87063c6897ff6703ea645e5cd3b946bf75cca

## Exclusividade
Escopo estrito ao teste de contrato rascunho/publicação e data do mesmo dia. Não editar EventManagementController.php (Atlas WORKING d5d61027; Genre HANDOFF b826161a), rotas, política comercial, outros testes ou main de produto. Nenhum claim nominal para este teste identificado no inventário de 181 claims/4 handoffs; revalidar HEAD/blob antes de qualquer alteração. Se houver sobreposição, parar e exigir CEDO+ACEITO.

## Falhas reproduzidas no CI oficial
Actions #41038109186, validate exit 1: CutinappEventLifecycleTest.php linhas 29 e 205 exigem event.is_published=true na resposta de POST /events. Runtime EventManagementController::store() linhas 169-184 cria explicitamente rascunho is_published=false, exige ingressos e publicação explícita. Corrigir contrato dos dois testes sem publicar automaticamente nem flexibilizar proteção comercial; usar rota publish apenas após criar ingresso, verificar visibilidade pública só após publicação. Reexecutar PHPUnit dirigido, CI no novo SHA e QA W4. Nenhum deploy/merge.
