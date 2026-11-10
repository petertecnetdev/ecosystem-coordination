# AUX-03 — Gate de aquisição pública: revalidação e impacto de crescimento

**Data:** 10/11/2026 — 10:42 BRT  
**Prioridade:** P0 de dependência operacional para crescimento  
**Área:** aquisição de produtores, landing pública, descoberta de eventos e conversão

## Objetivo
Impedir que novos esforços de aquisição enviem produtores e participantes a um destino público cuja disponibilidade ainda não foi comprovada; fornecer à conta principal evidência atualizada e critérios objetivos para liberar a distribuição.

## Oportunidade / obstáculo atacado
O obstáculo desta execução é exclusivamente o acesso público às rotas de entrada da Cutinapp. Não foram produzidos novos anúncios, Reels ou prospecções porque o caminho de conversão ainda não está validado.

## Confirmado
1. Em 10/11/2026, a abertura de `https://cutinapp.petertecnet.com.br/` pela ferramenta de pesquisa falhou com **HTTP 530**.
2. As rotas `/for-producers` e `/events` não puderam ser abertas pela mesma ferramenta.
3. Isso não prova indisponibilidade universal nem substitui teste em dispositivo real; é uma falha observada no caminho público disponível para esta execução.
4. A issue P0 [#643](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643) permanece aberta. Seu diagnóstico registrado descreve divergência entre SHA do filesystem e SHA servido pelo Nginx local/HTTPS público. A issue tinha última atualização em 31/10/2026 e não havia comentário posterior antes desta execução.
5. Os PRs de conversão #724, #725 e #726 continuam abertos e não integrados; #727 continua aberto em Draft. O PR #727 depende de #724 ou do mesmo release.
6. A marca Cutinapp no Metricool (ID 7119630) retorna somente `gbpData` em `networksData`, sem `instagramData`; a consulta de agendamentos de 10/11 a 17/11 retornou lista vazia. Isso não prova ausência de publicações feitas diretamente no Instagram.
7. O worklog W2 de 10/11 já preparou o guia de ingresso digital/QR Code. Esta execução não duplicou esse conteúdo.

## Hipótese
A falha de acesso público pode interromper a jornada de pessoas vindas de conteúdo, busca, indicação ou prospecção antes do cadastro e da publicação do primeiro evento. O impacto quantitativo não está medido.

## Trabalho realizado
- Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `COMMANDS.md`, claims ativos/completados, worklogs recentes, assignments AUX-03 e o histórico da issue #643.
- Revalidei home, landing de produtores e listagem de eventos.
- Confirmei estado aberto da issue #643 e ausência de comentários após 31/10 antes desta execução.
- Confirmei diretamente os estados dos PRs #724–#727.
- Consultei a configuração da marca e o calendário de publicações Metricool.
- Registrei comentário de impacto de crescimento na issue #643, comentário GitHub **6768925996**.
- Não criei nova campanha nem novo prospecto, evitando aumentar o estoque de materiais enquanto o destino permanece sem validação.

## Entregável
Este gate de aquisição pública e o comentário de crescimento anexado à issue #643.

## Canal
Conteúdo / indicação / prospecção → home ou `/for-producers` → cadastro/login → produção → primeiro evento → publicação → página pública → participante.

## CTA
**VALIDAR ACESSO PÚBLICO** — conta principal deve executar o teste de runtime em smartphone por Wi-Fi e rede móvel e devolver as evidências abaixo.

## Métrica principal
Produtores únicos que publicam o primeiro evento em até 7 dias ÷ produtores únicos que iniciam cadastro pela landing.

**Baseline:** N/D. Não há dados verificáveis de visitas, cadastros ou publicações nesta execução.

## Gate objetivo para liberar distribuição
- Home, `/for-producers` e `/events` carregam em smartphone por Wi-Fi e rede móvel.
- Landing apresenta oferta comercial e CTA corretos.
- CTA conduz ao cadastro e preserva a intenção de criar produção.
- `/events` apresenta conteúdo navegável e links públicos funcionais.
- SHA do filesystem, resposta do Nginx local e HTTPS público coincidem no release validado.
- Um teste percorre cadastro → produção → primeiro evento → publicação → página pública.
- Registrar data/hora, dispositivo, rede, status HTTP, SHA e resultado.

## Evidências
- Issue P0 #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Comentário AUX-03: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643#issuecomment-6768925996
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Worklog W2 de 10/11 (conteúdo participante já preparado): https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261110-1016-AUX-03-W2-guia-ingresso-digital-qr-code.md

## Próxima ação
Conta principal / responsável autorizado pela VPS deve resolver a divergência Nginx descrita na issue #643 e devolver evidência de SHA idêntico no filesystem, Nginx local e HTTPS público. Em seguida, executar a jornada mobile completa. AUX-03 retoma a distribuição e os contatos existentes somente após GO.

## Precisa da conta principal?
**SIM.** A correção do runtime e a validação em dispositivo/rede real dependem da conta principal e do responsável autorizado pela infraestrutura.

## Estado final
`PUBLIC_ROUTE_RECHECKED — HTTP_530_OBSERVED_ON_HOME — PRODUCER_AND_EVENTS_ROUTES_NOT_FETCHABLE_BY_RESEARCH_TOOL — ISSUE_643_COMMENTED — PRS_724_TO_727_NOT_MERGED — METRICOOL_INSTAGRAM_NOT_CONNECTED — NO_NEW_CAMPAIGN — NO_OUTREACH — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED`.
