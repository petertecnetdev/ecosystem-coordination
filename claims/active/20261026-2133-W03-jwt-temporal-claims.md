# Claim W03 — JWT com validade temporal futura (API Administrator)

agent: W03
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: em-andamento
started_at: 2026-10-26T21:33:00-03:00
area: regressão de segurança de JWT no fluxo administrativo, somente teste
files_or_scope:
- tests/Feature/ApplicationAdminJwtTemporalClaimsW03Test.php

Objetivo: validar que um JWT com assinatura legítima porém claim `nbf` no futuro não autoriza leitura ou mutação administrativa, mesmo com `app_id`, `application_id` e `X-Peter-App` forjados; preservar acesso com token corrente legítimo.

Escopo exclusivo e disjunto do claim anterior W03 (ApplicationAdminOwnerAuthorityW03Test.php), W1 checkout, W2 Administrator API e NP12 events:discover. Não editar ApplicationAdminService.php, workflows, fontes de curadoria, checkouts de produção/DEV compartilhados, nem arquivos de outros owners.

Antes da escrita: consultados workflows administrator-w03-ci.yml, automation-workers.yml, api-ci.yml, COMMANDS.md, issue #12, estado/tarefa NP12 e branch Independence. A CI W03 já inclui o padrão `tests/Feature/ApplicationAdmin*Test.php`. A falha P0 de is_root em ApplicationAdminService::context() permanece atribuída ao owner Administrator API W2 e não será ocultada.

Critérios de entrega: 1 commit real [agent:W3] apenas no arquivo de teste; registrar SHA, PHPUnit isolado (exit code) e CI do SHA, inclusive qualquer falha. Sem merge/deploy.