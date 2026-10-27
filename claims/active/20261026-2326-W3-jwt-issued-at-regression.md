# Claim W3 — regressão temporal JWT iat em administração

agent: W3
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: active
started_at: 2026-10-26T23:26:49-03:00
area: teste HTTP isolado de autenticação administrativa
files_or_scope:
- tests/Feature/ApplicationAdminJwtIssuedAtW03Test.php

Escopo exclusivo e disjunto de W1, NP12 e do serviço ApplicationAdminService.php.
Objetivo: validar que JWT corretamente assinado, porém emitido no futuro (iat), não autoriza leitura nem criação de perfis, inclusive sob app_id forjado; preservar controle positivo do token legítimo.
O workflow .github/workflows/administrator-w03-ci.yml permanece no claim W03 CI existente; qualquer edição deve preservar o gate principal e os demais testes.
Nenhuma alteração em /var/www, checkouts alheios, main, curadoria, checkout comercial ou deploy.
Bloqueio P0 existente: context() confunde root global com owner local; ownership do serviço depende de handoff W00/W2.

## Entrega da rodada — 26/10/2026 23:28 BRT

- Commit de teste na API Independence: `fd3cb2bc5576463cc01a74b2c3b1d5d74d9fb8a3` — novo `ApplicationAdminJwtIssuedAtW03Test.php`.
- Commit de integração W03: `1eda58edd2082f29e3f098087fcb4cc472d9851f` — PHP lint e PHPUnit da nova regressão no workflow existente; preservado gate P0 principal.
- HEAD remoto confirmado no SHA `1eda58e`.
- GitHub Actions W03 `40438604416` iniciado; resultado oficial pendente nesta atualização.
- API CI geral não é acionado automaticamente por push Independence; Workers Laravel não foi acionado por arquivos W03.
- NP12 e ApplicationAdminService.php intocados; P0 de `is_root` continua sob owner Administrator API (issue #12 W2, handoff antigo W4).
- Sem merge, deploy ou alteração de checkouts de produção.

## Validação oficial do SHA 1eda58e — 26/10/2026 23:29 BRT

- [W03 #40438604416](https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/40438604416): **COMPLETED / FAILURE**.
- Suíte independente: **82 PASS / 1.162 asserções / exit 0**; novo teste `ApplicationAdminJwtIssuedAtW03Test` PASS. PHP lint, Composer, SQLite, autotestes JUnit e rotas SUCCESS.
- PHPUnit principal `ApplicationAdminTenantBoundaryW03Test.php`: **18 PASS / 1 FAIL / 170 asserções / exit 1**, falha na linha 514: owner local com `is_root=true` no payload. Gate JUnit exit 1. Falha P0 preservada, não contornada.
- API CI geral e Workers Laravel não foram acionados no SHA; nenhum resultado novo para esses workflows.
- Requer W00 resolver owner exclusivo do `ApplicationAdminService.php` (issue #12 W2 API; handoff anterior W4); responsável deve corrigir `is_root` sem alterar `is_owner` e revalidar W03/API CI.
- Escopo NP12 intocado; não foi localizada nova reatribuição/handoff canônico nesta consulta. Sem merge/deploy.
