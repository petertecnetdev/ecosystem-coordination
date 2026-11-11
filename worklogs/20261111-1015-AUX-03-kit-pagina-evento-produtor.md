# AUX-03 — Worklog 2026-11-11 10:15 BRT — Kit de página de evento para aquisição de produtores

## Objetivo
Criar um ativo social de aquisição que gere conversas qualificadas com produtores sem encaminhar tráfego à landing pública enquanto o gate de runtime permanece sem validação.

## Área
Aquisição de produtores, Instagram, conteúdo, comunicação e conversão.

## Oportunidade
O conteúdo anterior tratou de primeiro evento, ativação pós-cadastro e ingresso digital/QR. O novo ângulo é ajudar o produtor a estruturar uma página de evento clara antes de divulgar: proposta, data/local, atrações confirmadas, ingressos e regras de entrada. A peça usa Direct como CTA e não depende de link público.

## Confirmado
- Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `COMMANDS.md`, worklogs recentes e claims consultáveis. `CURRENT_STATE.md` está desatualizado (última consolidação visível em 30/10); complementei com estado atual de issue/PRs e Metricool.
- Issue Cutinapp #643 permanece OPEN; último comentário disponível no histórico consultado é o registro AUX-03 de 10/11.
- Consulta web em 11/11: home retornou HTTP 530; `/for-producers` e `/events` não puderam ser abertas pela ferramenta. Isso não comprova indisponibilidade universal.
- PRs #724, #725, #726 e #727 seguem OPEN/NOT MERGED; #727 segue Draft e dependente de #724 ou do mesmo release.
- Metricool brand `cutinapp` (7119630) retorna somente `gbpData`, sem `instagramData`; posts agendados de 11/11 a 18/11: lista vazia. Isso não prova ausência de posts publicados diretamente pelo Instagram.
- Worklog AUX-03 de 10/11 contém guia QR Code para participantes; o presente ativo é de aquisição de produtores e não replica esse conteúdo.
- Worklogs anteriores já contêm Reel de primeiro evento, playbook de Direct e sequência pós-cadastro. O novo CTA `PAGINA` trata de copy/estrutura da página do evento, não de cadastro ou QR.

## Hipótese
Um checklist que melhora a clareza da página do evento pode atrair produtores que já estão preparando uma data e gerar conversas de maior intenção. Não há dados de alcance, resposta ou uplift que confirmem a hipótese.

## Trabalho realizado
1. Revalidei coordenação, prioridades, bloqueios, issue #643 e PRs #724–#727.
2. Revalidei a resposta pública da home, landing e rota de eventos pela ferramenta de pesquisa.
3. Consultei Metricool: marca, redes conectadas e agenda 11/11–18/11.
4. Evitei duplicar o conteúdo de QR Code e os ativos anteriores de primeiro evento/ativação.
5. Preparei carrossel de 7 telas, legenda, sequência de 3 Stories, resposta de Direct para a palavra `PAGINA`, modelo reutilizável de descrição e critérios de qualificação.

## Entregável
`deliverables/AUX-03/20261111-AUX-03-kit-pagina-evento-que-converte.md`

## Canal
Instagram carrossel + Stories → Direct → qualificação → demonstração → cadastro/produção → primeiro evento publicado.

## CTA
Enviar **PAGINA** no Instagram Direct.

## Métrica principal
Produtores qualificados originados pelo conteúdo que publicam o primeiro evento em até 7 dias ÷ produtores qualificados originados pelo conteúdo.

Baseline: N/D; publicação e conversões ainda não ocorreram.

## Evidências
- Issue P0 #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Worklog QR Code participante (10/11): https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261110-1016-AUX-03-W2-guia-ingresso-digital-qr-code.md
- Gate público anterior: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261110-1042-AUX-03-W3-public-runtime-acquisition-blocker.md

## Próxima ação
Conta principal aprova e publica manualmente o carrossel/Stories no Instagram; se o Direct estiver autorizado, AUX-03 acompanha e qualifica as respostas. Depois do GO do runtime, conduzir leads ao cadastro e medir o primeiro evento publicado em sete dias.

## Precisa da conta principal?
SIM — aprovação/publicação no Instagram e autorização de acesso ao Direct; conta principal/infra também precisa resolver o gate público P0 antes de campanhas com links.

## Estado final
`CONTENT_PACKAGE_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_SENT — NOT_PUBLISHED — NO_DM_SENT — PUBLIC_RUNTIME_NO_GO — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS`.
