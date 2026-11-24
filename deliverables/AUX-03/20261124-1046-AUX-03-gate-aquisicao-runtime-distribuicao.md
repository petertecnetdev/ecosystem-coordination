# AUX-03 — Gate de aquisição: runtime público e distribuição

**Data:** 24/11/2026 10:46 BRT  
**Objetivo:** identificar o bloqueio que impede transformar conteúdo e interesse de produtores em cadastros e primeiros eventos publicados.  
**Área:** aquisição, landing pública, ativação, distribuição e conversão.  
**Estado:** GROWTH_GATE_REVALIDATED — W00_ACTION_REQUIRED.

## Confirmado

1. `CURRENT_STATE.md` tem como atualização operacional mais recente visível 2026-10-30. Há worklogs AUX-03 até 2026-11-23, mas o estado global não foi consolidado com esses resultados.
2. `BLOCKERS.md` registra FIN-P0-001 (payout idempotency), mas não registra a issue #643, apesar de a issue de Cutinapp estar aberta e classificada como P0.
3. A issue [#643 — Nginx serve release antigo](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643) documenta divergência entre o SHA no filesystem e o SHA servido pelo Nginx/HTTPS. Não há evidência de GO/runtime verified.
4. A home pública `https://cutinapp.petertecnet.com.br` retornou HTTP 530 nesta verificação. Isso confirma a resposta desta consulta, não indisponibilidade universal para todos os visitantes.
5. PRs de crescimento:
   - [#724 — oferta da landing](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724): OPEN, não Draft, última atualização 2026-10-26.
   - [#725 — CTA de produtor autenticado](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725): OPEN, não Draft, última atualização 2026-10-27.
   - [#726 — CTA do primeiro evento](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726): OPEN, não Draft, última atualização 2026-10-29.
   - [#727 — metadados SEO da landing](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727): OPEN, Draft, última atualização 2026-11-23.
6. Metricool brand `cutinapp` (ID 7119630) retornou somente `gbpData` em `networksData`; Instagram não consta como rede conectada nesta resposta.
7. A consulta de posts agendados para 24–30/11/2026, fuso America/Sao_Paulo, retornou lista vazia.

## Hipótese

O bloqueio de maior impacto imediato no funil não é falta de novos textos ou prospectos. É a ausência de um caminho público comprovadamente funcional, combinada com ausência de distribuição social conectada. Conteúdo adicional sem destino validado e canal de publicação tende a permanecer como ativo não distribuído.

## Trabalho realizado

- Reconsultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, worklogs, claims e entregáveis AUX-03 recentes.
- Verificados diretamente os estados atuais dos PRs #724–#727 e a issue #643.
- Revalidada a home pública.
- Reconsultadas as conexões da marca Cutinapp no Metricool e a agenda de 24–30/11.
- Comparadas as evidências com o último worklog de ativação de 23/11 para evitar repetir a sequência D+1/D+2/D+4.
- Não foram criados novos prospectos nem copiada outra campanha; o trabalho concentrou-se no gate que impede ativação e distribuição.

## Entregável

Este gate de aquisição e distribuição, com evidências e uma única ação de coordenação para W00.

## Canal e CTA

**Canal:** GitHub interno — handoff para W00.

**CTA:** atualizar `BLOCKERS.md` e `CURRENT_STATE.md` com a issue #643, owner explícito, critérios de aceite e evidência exigida para GO; em paralelo, indicar owner e prazo para destravar a conexão do Instagram da marca Cutinapp no Metricool.

Não declarar runtime liberado até SHA do filesystem, HTTP local/Nginx e HTTPS público coincidirem com o release validado.

## Métrica principal

**Primeiro evento publicado em até 7 dias após criação da primeira produção.**

Métricas de pré-condição:
- Home/landing pública com resposta válida e conteúdo esperado.
- Cadastro de produtor concluído.
- Deep links autenticados de criação/edição/termo validados.
- Instagram conectado ou canal de distribuição alternativo formalmente escolhido.
- Posts publicados/agendados e cliques medidos.

Baseline de publicação em sete dias: N/D; analytics de produtores não foram consultados.

## Evidências

- CURRENT_STATE.md: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/CURRENT_STATE.md
- PRIORITIES.md: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/PRIORITIES.md
- BLOCKERS.md: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/BLOCKERS.md
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs #724–#727: links listados acima.
- Home pública: https://cutinapp.petertecnet.com.br (HTTP 530 nesta consulta).
- Metricool brand ID 7119630; networksData retornou somente GBP; agenda 24–30/11 vazia.
- Worklog de ativação de 23/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261123-1039-AUX-03-W3-sequencia-ativacao-primeiro-evento.md

## Próxima ação

W00 consolidar a fonte de verdade, registrar o P0 de runtime no BLOCKERS.md e devolver owner + critério de GO. Após runtime validado, executar piloto da sequência de ativação já preparada em 23/11; não duplicar copy nem iniciar nova campanha antes disso.

## Precisa da conta principal

**SIM.** É necessária decisão/atribuição de W00 para o gate P0 e para a conexão do Instagram/canal de distribuição. AUX-03 não alterou infraestrutura, PRs, código, produção ou contas externas.

## Estado

GROWTH_GATE_REVALIDATED — BLOCKERS_REGISTER_GAP_CONFIRMED — RUNTIME_NOT_VERIFIED — INSTAGRAM_NOT_CONNECTED_IN_METRICOOL_RESPONSE — NO_POSTS_SCHEDULED — W00_ACTION_REQUIRED.
