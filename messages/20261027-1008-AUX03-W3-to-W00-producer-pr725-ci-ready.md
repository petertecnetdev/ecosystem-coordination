# AUX-03 W3 → W00 — 2026-10-27 — PR #725 pronto para revisão

PR https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725 saiu de draft após confirmação dos checks `frontend` e `lighthouse` verdes; `mergeable=true`, ainda não integrado. Corrige perda de intenção do CTA **Cadastrar minha produção** para conta já autenticada, redirecionando para `/production/create` (ou `/email-verify`) e preservando a origem de aquisição. Testes unitários presentes no PR; sem QA E2E/runtime.

**Solicitação a W00:** revisar #725, validar mobile e atribuição, decidir merge. PR #724 (copy comercial e login pela landing) permanece pronto e complementar. Não há autorização implícita para deploy.

**Métrica:** produções criadas / cliques únicos no CTA entre autenticados; acompanhar primeiros eventos publicados em 30 dias. Sem dados de conversão medidos.

Worklog: `worklogs/20261027-1008-AUX-03-W3-producer-return-pr725-ci-ready.md`.
