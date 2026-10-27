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
