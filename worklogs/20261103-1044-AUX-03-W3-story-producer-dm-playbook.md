# AUX-03 W3 — Worklog 2026-11-03 — Playbook de resposta aos Stories de produtores

## Objetivo
Preparar a conversão das respostas voluntárias da pesquisa W1 em conversas comerciais qualificadas e oportunidades de publicação do primeiro evento.

## Área
Aquisição de produtores, Instagram Direct, qualificação, comunicação e ativação.

## Oportunidade
O W1 preparou três Stories de pesquisa para 03/11: identificar produtores, distinguir entre dificuldade de atrair público ou vender ingressos e coletar respostas abertas. A publicação ainda não foi confirmada. Esta execução cobre a etapa seguinte — como responder e conduzir cada tipo de interação — sem duplicar os próprios Stories, o Reel de 02/11 ou o piloto de agenda recorrente de 01/11.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, claims/active/, claims/completed/, orchestration/STATE.md, assignment AUX-03/W3, plano CUTINAPP_COLD_START_GROWTH.md e worklogs AUX-03 de 01–03/11.
- Confirmei que não há claim AUX-03 W3 ativo cobrindo este playbook.
- Li o roteiro dos Stories W1 de 03/11 para alinhar as respostas às opções reais das enquetes e à caixa aberta.
- Verifiquei Metricool brand cutinapp, ID 7119630: networksData contém apenas gbpData, sem instagramData; agendamentos 03/11–10/11 retornaram vazios. Isso não comprova ausência de publicações orgânicas diretas no Instagram.
- Verifiquei API config/subscriptions.php em main: Cutinapp tem subscription_enabled=false, monetization_model=transaction_fee, plans=[]; não existe percentual de taxa no bloco consultado.
- Verifiquei PRs #724, #725, #726 e #727: #724/#725/#726 abertos e não integrados; #727 aberto em draft, não integrado e dependente de #724. A experiência de onboarding do #726 não está em main.
- Preparei respostas distintas para produtor ativo/iniciante, atração de público, venda de ingressos e resposta aberta; incluí convite de orientação assistida, objeções comerciais, limites de contato e estados do lead.
- Não enviei mensagens, não publiquei Stories, não alterei código, não fiz merge nem deploy.

## Entregável
deliverables/AUX-03/20261103-W3-playbook-respostas-stories-produtores.md

## Canal
Instagram Stories → resposta voluntária → Instagram Direct → qualificação → preparação da produção → primeiro evento publicado.

## CTA
Responder PREPARAR para solicitar orientação sobre a preparação do primeiro evento.

## Métrica principal
Produtores que publicam primeiro evento em até 7 dias ÷ produtores qualificados que responderam aos Stories.

## Métrica intermediária
Leads qualificados ÷ respostas voluntárias aos Stories.

Baseline: N/D; material W1 ainda não publicado e respostas não medidas.

## Evidências
- Worklog W1 Stories: worklogs/20261103-1007-AUX-03-W1-story-pesquisa-produtores.md.
- Roteiro W1: deliverables/AUX-03/20261103-W1-story-pesquisa-produtores.md.
- API comercial: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php (SHA consultado: 380033cdb502c34896b907ae2209c91e31f7f14f).
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Metricool brand settings e scheduled posts consultados em 03/11/2026.

## Próxima ação
Conta principal publicar os Stories, inserir stickers nativos e confirmar acesso autorizado ao Direct. Após respostas reais, aplicar o playbook e medir qualificação e publicação em 7 dias. Não enviar link de landing nem prometer onboarding atualizado até validação/integração dos PRs correspondentes.

## Precisa da conta principal?
SIM — publicação dos Stories, acesso autorizado ao Direct e confirmação do caminho de cadastro/publicação ativo.

## Estado final
PLAYBOOK_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_SENT — NOT_PUBLISHED — NO_DM_SENT — NOT_DEPLOYED — CONVERSION_NOT_MEASURED.
