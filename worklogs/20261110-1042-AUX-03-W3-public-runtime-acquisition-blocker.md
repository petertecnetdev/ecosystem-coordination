# AUX-03 — Worklog 2026-11-10 10:42 BRT — Gate de aquisição pública

## Objetivo
Revalidar o principal destino de conversão da Cutinapp e impedir desperdício de aquisição enquanto as rotas públicas não estiverem comprovadas.

## Área
Aquisição de produtores, landing pública, descoberta de eventos e conversão.

## Oportunidade
O material de aquisição e o conteúdo evergreen já preparados não devem ser ampliados nem distribuídos em escala se o acesso público não estiver validado. O obstáculo escolhido nesta execução foi somente o runtime público.

## Confirmado
- Home: tentativa de abertura em 10/11 retornou HTTP 530 pela ferramenta de pesquisa.
- `/for-producers` e `/events`: não acessíveis pela mesma ferramenta.
- Limite: isso não prova indisponibilidade para todos os visitantes; exige validação em smartphone e redes reais.
- Issue P0 #643 permanece OPEN; o histórico descreve divergência entre SHA no filesystem e SHA servido pelo Nginx local/HTTPS. Sem comentários posteriores a 31/10 antes desta execução.
- PRs #724, #725 e #726 continuam OPEN/NOT MERGED; #727 OPEN/DRAFT/NOT MERGED e dependente de #724 ou do mesmo release.
- Metricool brand `cutinapp`, ID 7119630: `networksData` contém `gbpData`, sem `instagramData`; agendamentos 10/11–17/11: lista vazia. Isso não prova ausência de posts publicados diretamente no Instagram.
- W2 já preparou em 10/11 um guia de ingresso digital/QR Code; não dupliquei esse ativo.
- `CURRENT_STATE.md` ainda contém última consolidação operacional de 30/10, portanto não é suficiente como fonte isolada do estado atual. Foram consultados worklogs recentes, issues e PRs diretamente.

## Hipótese
A falha pode interromper a jornada de aquisição antes de cadastro/ativação. O volume de visitas perdidas não foi medido.

## Trabalho realizado
1. Li CURRENT_STATE, PRIORITIES, BLOCKERS, COMMANDS, claims ativos/completados, worklogs recentes, assignment AUX-03 e issue #643.
2. Testei as rotas públicas com a ferramenta de pesquisa.
3. Verifiquei diretamente os estados dos PRs #724–#727.
4. Consultei Metricool: brand settings e posts agendados para 10/11–17/11.
5. Publiquei comentário de impacto de crescimento na issue #643: comentário **6768925996**.
6. Criei o gate de aquisição pública com critérios de liberação e handoff à conta principal.

## Entregável
`deliverables/AUX-03/20261110-W3-growth-impact-public-runtime-blocker.md`

## Canal
Conteúdo/indicação/prospecção → home ou landing de produtores → cadastro/login → produção → evento → publicação → página pública → participante.

## CTA
**VALIDAR ACESSO PÚBLICO** — teste real em smartphone por Wi-Fi e rede móvel, com evidência de status, SHA e conclusão da jornada.

## Métrica principal
Produtores únicos que publicam o primeiro evento em até 7 dias ÷ produtores únicos que iniciam cadastro pela landing.

Baseline: N/D; nenhuma conversão foi medida.

## Evidências
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Comentário: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643#issuecomment-6768925996
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- W2 guia participante: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261110-1016-AUX-03-W2-guia-ingresso-digital-qr-code.md

## Próxima ação
Conta principal deve resolver a issue #643 e comprovar igualdade do SHA do filesystem, Nginx local e HTTPS público; depois executar cadastro → produção → evento → publicação em smartphone. AUX-03 retoma campanhas e prospecções após GO.

## Precisa da conta principal?
SIM — runtime, VPS e validação em dispositivo real.

## Estado final
`PUBLIC_ROUTE_RECHECKED — ISSUE_643_COMMENTED — WORKLOG_COMMITTED — HANDOFF_SENT — NO_NEW_CAMPAIGN — NO_OUTREACH — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED`.
