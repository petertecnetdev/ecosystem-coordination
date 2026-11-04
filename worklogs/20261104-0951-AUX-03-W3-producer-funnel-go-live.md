# AUX-03 W3 — Worklog 2026-11-04 — Go-live do funil de produtores

## Objetivo
Destravar a passagem de materiais de aquisição já preparados para distribuição real, leads qualificados e publicação do primeiro evento, sem produzir peças redundantes.

## Área
Aquisição de produtores, distribuição social, landing pública, conversão e ativação.

## Oportunidade
A execução de 03/11 deixou um playbook de Direct pronto, mas dependente de Stories W1 que ainda não têm publicação confirmada. A maior lacuna observável passou a ser operacional: material pronto sem distribuição e sem caminho de cadastro/publicação validado.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, claims/active/, claims/completed/, orchestration/STATE.md, assignments AUX-03/W1-W3 e worklogs de 01–03/11.
- Confirmei W3 como DONE/fallback_to_base_role=true; W1 está BLOCKED por falta de publicação/Insights Instagram; W2 está AVAILABLE para SEO/blog. Não assumi escopo de SEO/blog de W2 nem dupliquei os materiais sociais W1/W3.
- Consultei novamente o worklog e o entregável W1 de Stories de 03/11 e o playbook W3 de Direct. Os Stories seguem NOT_SCHEDULED — NOT_PUBLISHED; não há respostas ou métricas reais registradas.
- Consultei Metricool brand settings: marca cutinapp, ID 7119630, timezone America/Sao_Paulo; networksData contém somente gbpData, sem instagramData.
- Consultei posts agendados no Metricool de 04/11/2026 a 11/11/2026: data vazia.
- Consultei diretamente os PRs do frontend: #724, #725 e #726 open, mergeable, not merged, ready-for-review; #727 open, mergeable, draft, not merged. #727 registra dependência de #724.
- Confirmei na configuração API citada pelo worklog anterior: subscription_enabled=false, monetization_model=transaction_fee, plans=[]; não há percentual de taxa nesse bloco.
- Consultei a raiz pública via navegador web; o crawler recebeu apenas a instrução de ativar JavaScript. A rota /for-producers não foi recuperada. Isso não prova indisponibilidade em browser real.
- Busquei páginas públicas indexadas de eventos Cutinapp; nenhuma página de evento real foi localizada nesta busca. Isso não prova ausência de eventos no banco ou em URLs não indexadas.
- Produzi runbook de go-live com gates, sequência de execução, CTA único, métricas, definições do funil e rastreador mínimo sem dados sensíveis.
- Não publiquei Stories/Reels, não enviei DMs, não abordei produtores, não integrei PRs e não acessei VPS.

## Entregável
deliverables/AUX-03/20261104-W3-producer-funnel-go-live-runbook.md

## Canal
Instagram Stories W1 → resposta voluntária → Instagram Direct → qualificação → preparação da produção → primeiro evento publicado.

## CTA
Responder PREPARAR para solicitar orientação sobre a preparação do primeiro evento.

## Métrica principal
Produtores qualificados que publicam o primeiro evento em até 7 dias ÷ produtores qualificados que responderam à campanha.

## Métricas secundárias
- Respostas voluntárias ÷ alcance do Story 3 (24h).
- Produções criadas ÷ leads qualificados.
- Primeiras vendas em 30 dias ÷ produtores com evento publicado.

Baseline: N/D; publicação e Insights não confirmados.

## Evidências
- CURRENT_STATE: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/CURRENT_STATE.md
- PRIORITIES: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/PRIORITIES.md
- BLOCKERS: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/BLOCKERS.md
- W1 Stories worklog: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261103-1007-AUX-03-W1-story-pesquisa-produtores.md
- W1 Stories asset: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261103-W1-story-pesquisa-produtores.md
- W3 Direct playbook: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261103-W3-playbook-respostas-stories-produtores.md
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Metricool brand 7119630 e scheduled posts 04/11–11/11 consultados em 04/11/2026.
- Repositório frontend: public/index.html SHA 3995f9485a48790313bcce758d9fa1c7214b86d2; public/robots.txt SHA 07590bc915a6d45033e2a55ecf19c4c7a69b6cf5; SeoManager.js SHA 14216dcf98e6fb27cb02a52ba33b46230fae4eb4.

## Próxima ação
Conta principal executar Gates 1 e 2 do runbook: revisar/validar os PRs e o caminho público em smartphone real; publicar os Stories com stickers nativos; confirmar acesso autorizado ao Instagram Direct. AUX-03 assume conversas e qualificação depois da liberação.

## Precisa da conta principal?
SIM — revisão/integração dos PRs, validação mobile, publicação dos Stories e acesso autorizado ao Direct.

## Estado final
RUNBOOK_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_SENT — STORIES_NOT_PUBLISHED — NO_DM_SENT — NO_PR_MERGE — NOT_DEPLOYED — CONVERSION_NOT_MEASURED.