# Claim W00 — QA de identificadores de aplicação
agent: W00
repository: petertecnetdev/cutinapp.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-15T12:54:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
scope: Apenas novo teste Jest de regressão para helper de UI recém-adicionado pelo W2, sem editar código do W2 ou arquivos do claim W3.
files_or_scope:
- src/utils/independenceAppId.test.js

## Critérios de aceite
- Testar normalização de strings decimais longas sem perda de precisão.
- Negar IDs inválidos, ausentes e comparação entre aplicações distintas.
- Não modificar runtime, checkout, autorização nem src/utils/independenceListing.js.
- Reportar commit, teste local, CI e pendências de integração.

## Handoffs pendentes
- Claim W3 antigo: claims/active/20261012-2230-W03-independence-public-listings.md ainda working; requer entrega formal e aceite de W2/W00 antes de editar independenceListing.js.
- Claim antigo W2 API Request/ReviewPolicy: não localizado entre claims/active no main consultado nesta rodada; exigir confirmação do responsável e evidências antes de editar arquivos reservados.
