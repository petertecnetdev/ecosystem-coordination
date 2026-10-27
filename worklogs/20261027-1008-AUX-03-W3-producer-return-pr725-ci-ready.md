# AUX-03 W3 — 2026-10-27 — PR #725 pronto para revisão

- **Objetivo:** remover a interrupção do funil para produtor que já está autenticado e chega pelo CTA de cadastro.
- **Área:** aquisição → landing → cadastro → produção → primeiro evento.
- **Oportunidade / obstáculo único:** `guestRoute` enviava o usuário autenticado ao dashboard ao abrir `/register` com intenção explícita de criar produção.
- **Trabalho realizado:** reconsulta de `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/active`, `worklogs/`, assignment W3 e PRs #724/#725; inspeção do diff e dos cinco testes de redirecionamento; verificação de checks remotos; promoção do PR #725 de draft para ready for review.
- **Entregável:** PR #725 pronto para revisão, preservando retorno a `/production/create`, verificação de e-mail quando necessária e `acquisitionSource` válida. Não foi criado novo PR nem alterado código.
- **Canal:** landing de produtores / aquisição orgânica e indicação, com continuidade após cadastro.
- **CTA:** **Cadastrar minha produção**.
- **Métrica principal:** produções criadas / cliques únicos no CTA entre usuários previamente autenticados (segmentar por `acquisitionSource`). Métrica de negócio: primeiro evento publicado em até 30 dias. **Nenhum uplift medido**.
- **Confirmado (2026-10-27):** PR #725 `draft=false`, `state=open`, `merged=false`, `mergeable=true`; head `eb2fb688`. GitHub Actions `frontend=success` e `lighthouse=success`. PR #724 continua aberto, `draft=false`, `mergeable=true`, head `37456fc`; checks `frontend=success` e `lighthouse=success`.
- **Hipótese:** preservar a intenção de criar produção após autenticação reduz abandono de produtores recorrentes; sem dados de produção que comprovem.
- **Evidências:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725 ; https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40196102013/job/121177145505 ; https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40196102011/job/121177145655 ; https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724 .
- **Recomendação / próxima ação:** W00 revisar PR #725 e #724; testar manualmente mobile 320/360/390/430 com usuário autenticado/verificado, autenticado/não verificado e visitante novo; confirmar persistência da origem e criação de produção; decidir merge e acompanhar conversão real. Não executar deploy na VPS por padrão.
- **Conta principal necessária:** **SIM**, para QA E2E e decisão de merge.
- **Estado:** `PR725_READY_FOR_REVIEW — CI_GREEN — WORKLOG_RECORDED — NOT_MERGED — NOT_DEPLOYED`.
