# Handoff P0 — autoridade root global versus proprietário local

from: W3 (W03)
to: W00 / responsável autorizado Administrator API (W2 conforme issue #12; confirmar com W4)
repository: petertecnetdev/api.petertecnet.com.br
related_pr: none
priority: P0
status: action-required
date: 2026-10-24T19:35:00-03:00

## Diagnóstico verificável

- Branch: `Independence`; HEAD observado: `db2bfae023de6496d4d92ea8e1537bb65ee3c464`.
- `app/Domain/Platform/Services/ApplicationAdminService.php`, método `context()`, ramo `isOwner()`: define `'is_root' => true` mesmo quando `isRoot($user) === false`.
- O contrato correto separa `is_root` (autoridade global) de `is_owner` (titularidade da aplicação); preservar permissões legítimas do proprietário local sem promover autoridade global.
- PHPUnit oficial `ApplicationAdminTenantBoundaryW03Test.php:514` segue **18 PASS / 1 FAIL**, exit 1; W03 CI #40134604647 FAILURE.
- Suíte independente `ApplicationAdminOwnerAuthorityW03Test.php` teve **31 PASS / 325 asserções**, exit 0, mas não desbloqueia a release.
- `API CI` geral do SHA não foi acionado; não alegar aprovação.
- Ownership do serviço **não** foi transferido a W3. A issue #12 nomeia W2 como Administrator API, mas os assignments recentes de W2 são frontend; W4 aparece em handoff anterior. Não presumir transferência.

## Ação requerida (W00)

1. Confirmar quem possui claim atual/exclusivo de `ApplicationAdminService.php` e obter aceite formal de handoff para o executor Administrator API (sem concorrência de escrita).
2. Responsável autorizado: ajustar o campo `is_root` do payload de `context()` para refletir `isRoot($user)`, preservando `is_owner`, `authority_level` e autorização local; auditar consumidores React para que não interpretem owner local como root global.
3. Executar regressões root global, owner local, delegado, cross-app e revogação. Exigir `ApplicationAdminTenantBoundaryW03Test.php` exit 0, suíte independente exit 0 e API CI geral no mesmo SHA. Não enfraquecer/remover a asserção P0.
4. Reportar SHA, arquivos, testes, CI, riscos e handoff concluído. Sem merge ou deploy sem autorização específica.

## NP12 e limites

NP12 `TASK-20261022-CURATION-NP12` continua `RUNNING`, owner NP12, `delegation_count=0`; lock histórico expirado, mas não há reatribuição formal. Não editar `events:discover` ou arquivos de curadoria, comércio W1, `main`, `/var/www` nem DEV alheio.

## Evidências

- API: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/Independence/app/Domain/Platform/Services/ApplicationAdminService.php
- W03 CI: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40134604647
- Ownership e atribuições: https://github.com/petertecnetdev/ecosystem-coordination/issues/12
- Task NP12: https://github.com/petertecnetdev/petertecnet.com.br/blob/main/.agents/tasks/TASK-20261022-CURATION-NP12.json
