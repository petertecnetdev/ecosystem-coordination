# AUX-03 W3 — Worklog 2026-11-18 — fila priorizada de contatos pós-evento

## Objetivo
Converter a pesquisa comercial acumulada em uma fila acionável, com prioridade e janela de contato, evitando adicionar novos prospectos enquanto as abordagens anteriores permanecem sem envio.

## Área
Aquisição de produtores, relacionamento comercial, qualificação e conversão.

## Oportunidade
Há sete produtores/organizações com eventos identificados e mensagens preparadas entre 05 e 16/11. Nenhum dos worklogs correspondentes registra contato enviado. O primeiro prospecto pronto para contato pós-evento é Taberna Music Pub: GERAÇÃO 2K encerrou em 15/11. A oportunidade imediata é transformar uma mensagem preparada em uma conversa comercial autorizada, sem encaminhar cadastro público não validado.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, COMMANDS.md, REVENUE_TARGET.md e PROFITABILITY_PLAN.md.
- orchestration/STATE.md, orchestration/WORKER_REGISTRY.md e orchestration/assignments/AUX-03/W1.md, W2.md e W3.md.
- Claims ativos AUX-03: W2 SEO/public discovery e claim geral W3 de aquisição; esta execução não altera arquivos de produto nem assume escopo técnico.
- Claims concluídos e worklogs de 05 a 17/11; entregáveis dos prospectos Taberna, Joint Records, NC Entretenimento, Funclube, Noite Infame, Blue Velvet e Undergoth.
- PRs #724–#727 e issue #643 diretamente no repositório Cutinapp.
- Metricool getBrandSettings para a marca 7119630 e getScheduledPosts para 18–25/11/2026.
- Páginas primárias dos eventos na Sympla e Shotgun para revalidar produtor, data, situação e canal público.

## Estado de coordenação observado
- CURRENT_STATE.md continua com última consolidação de 30/10/2026; não foi atualizado nesta execução.
- COMMANDS.md mantém a distribuição W1 Independence, W2 Administrator, W3 site, W4 conteúdo; AUX-03 W3 tem assignment específico de landing DONE com fallback para função-base de aquisição e conversão.
- AUX-03 W1 está BLOCKED por dependência de mídia pública para distribuição social.
- AUX-03 W2 está AVAILABLE, com claim ativo de SEO/public discovery; não assumi esse escopo.
- Issue #643 continua OPEN.
- PR #724 OPEN/READY_FOR_REVIEW; #725 OPEN; #726 OPEN; #727 OPEN/DRAFT e dependente de #724 ou do mesmo release.
- A home pública retornou HTTP 530 nesta consulta. A evidência não prova indisponibilidade universal.
- Metricool retorna apenas gbpData para a marca Cutinapp, sem instagramData. A agenda de posts de 18 a 25/11 retornou lista vazia.

## Confirmado
- Taberna Music Pub: GERAÇÃO 2K aconteceu de 14/11 às 20h a 15/11 às 03h; a página agora informa evento encerrado, produtor Taberna Music Pub, botão “Fale com o produtor” e WhatsApp de reservas (62) 99692-0505.
- Joint Records Brasil: Mosh Pit Fest em 21/11, 22h–06h, página Sympla com botão “Fale com o produtor”.
- Raiza Morgana Lima Ribeiro: Noite Infame 2 em 21/11, 18h30–22h, página Sympla com botão “Fale com o produtor”.
- Undergoth: evento de 21/11, 20h–03h30, página Shotgun identifica organizador Undergoth; e-mail público registrado no worklog de 16/11.
- NC Entretenimento: CHAWON FEST tem Fan Event em 26/11 e show em 27/11; página Sympla identifica NC Entretenimento.
- Funclube: Funfarra Last Dance em 28/11, 22h–06h; página Sympla identifica Funclube.
- Debora Machado: Blue Velvet em 11/12, 20h–00h30; perfil Sympla identifica Debora como produtora.
- Os worklogs anteriores registram as mensagens como preparadas e NÃO enviadas.
- Metricool brand ID 7119630 não retorna instagramData; posts agendados de 18 a 25/11: lista vazia.

## Hipótese
Uma fila com janela pós-evento reduz o risco de abordar produtores durante a operação da edição atual e aumenta a chance de uma conversa sobre a próxima produção. Ainda não há taxa de resposta medida.

## Trabalho realizado
1. Releitura dos prospectos e mensagens existentes para não duplicar copy.
2. Revalidação das páginas de eventos e datas atuais.
3. Consolidação de sete contatos em ordem de prioridade e janela recomendada.
4. Priorização do Taberna Music Pub como primeiro piloto porque o evento encerrou em 15/11.
5. Preparação de uma mensagem pós-evento específica para Taberna, CTA PRÓXIMA DATA.
6. Orientação de canal: Sympla “Fale com o produtor” primeiro; WhatsApp de reservas não deve ser tratado automaticamente como canal B2B autorizado.
7. Definição de regra para pausar novas prospecções até medir o primeiro contato.
8. Registro de dependência da conta principal para autorizar contato e validar apresentação/cadastro.

## Entregável
deliverables/AUX-03/20261118-1040-AUX-03-fila-contatos-produtores-pos-evento.md

## Canal
Contato B2B pós-evento por botão público “Fale com o produtor” na Sympla; e-mail/Instagram oficial quando já documentados para o prospecto. Não usar grupo de participantes nem canal de venda como canal B2B sem autorização.

## CTA
PRÓXIMA DATA — piloto Taberna Music Pub.

## Métrica principal
Primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada e aceita.

Métrica operacional: respostas positivas ÷ contatos autorizados efetivamente enviados.

Baseline: zero contatos enviados nesta fila; conversões N/D.

## Evidências
- Taberna GERAÇÃO 2K: https://www.sympla.com.br/evento/geracao-2k/3626527
- Joint Records Mosh Pit Fest: https://www.sympla.com.br/evento/mosh-pit-fest/3613539
- Noite Infame 2: https://www.sympla.com.br/evento/lgc/3639378
- Undergoth: https://shotgun.live/pt-br/events/undergoth
- CHAWON FEST: https://www.sympla.com.br/evento/chawon-fest-trapped-in-gyn/3628371
- Funfarra Last Dance: https://www.sympla.com.br/evento/funfarra-last-dance/3645891
- Blue Velvet: https://www.sympla.com.br/evento/blue-velvet-hip-hop-lounge/3648736
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs #724–#727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pulls
- Worklogs de origem: 20261105-1012, 20261106-1043, 20261108-1047, 20261112-1017, 20261113-1027, 20261114-0954, 20261115-0949 e 20261116-1017.

## Próxima ação
Conta principal/W00 autoriza ou nega o piloto Taberna e confirma qual apresentação pode ser oferecida sem runtime GO. Após autorização, AUX-03 envia um único contato pelo canal aprovado e registra resposta. Só depois do piloto, liberar individualmente a fila de 23–24/11.

## Precisa da conta principal
SIM — autorização de contato externo e validação do caminho de demonstração/cadastro.

## Estado final
QUEUE_PRIORITIZED — TABERNA_FIRST_CONTACT_READY — NOT_SENT — WORKLOG_COMMITTED — HANDOFF_REQUIRED — NOT_DEPLOYED.
