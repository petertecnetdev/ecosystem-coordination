# AUX-03 — Worklog 2026-11-17 — campanha checklist de pré-venda

## Objetivo
Criar um ativo social de aquisição de produtores que gere conversas qualificadas pelo Instagram Direct, sem depender da landing pública ainda não validada.

## Área
Instagram/Reels/Stories, conteúdo para produtores, qualificação comercial e conversão.

## Oportunidade
Os materiais recentes já cobrem página do evento, check-in/QR Code, line-up e respostas a Stories. Esta execução trabalha uma etapa distinta: decisões comerciais e operacionais que precisam estar definidas antes de abrir a venda ou inscrição.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/STATE.md, WORKER_REGISTRY.md e assignments/AUX-03/W1.md, W2.md e W3.md.
- Claims ativos e concluídos AUX-03; worklogs e entregáveis de 03/11 a 17/11.
- Playbook de Direct de 03/11; kit de página do evento de 11/11; guia de check-in de 13/11; guia de line-up de 14/11; cluster editorial de 15/11; correção de rota de 17/11.
- PRs #722 e #724 e issue #643.
- Metricool getBrandSettings para brand ID 7119630 e getScheduledPosts para 17–24/11/2026.
- Pesquisa pública por eventos Cutinapp: não retornou página de evento da Cutinapp que pudesse ser confirmada nesta rodada. Isso não prova inexistência de eventos publicados.

## Confirmado
- Metricool retorna `gbpData`, mas não `instagramData`, para a marca Cutinapp.
- A agenda Metricool consultada de 17/11 a 24/11 está vazia.
- A elegibilidade do GBP não foi confirmada; não usar esse canal até validação da conta principal.
- PR #724 está OPEN e NOT MERGED; a campanha não afirma mensalidade, preço ou taxas.
- Issue #643 está OPEN; o CTA foi desenhado para Direct, sem depender de link público.
- A pesquisa não forneceu um evento Cutinapp público verificável para usar como exemplo; a peça não inventa evento ou prova social.

## Hipótese
Um checklist de pré-venda pode atrair produtores em fase de preparação e gerar leads mais qualificados do que uma chamada genérica para conhecer a plataforma. Não há dados de alcance ou conversão que confirmem essa hipótese.

## Trabalho realizado
1. Diferenciei a pauta dos ativos editoriais e sociais existentes.
2. Escrevi carrossel de sete telas.
3. Escrevi roteiro de Reel de 20–25 segundos.
4. Escrevi legenda e sequência de três Stories.
5. Escrevi resposta de Direct com checklist reutilizável.
6. Defini CTA `CHECKLIST` e critérios de qualificação.
7. Defini métrica de conversão e resultado de negócio.
8. Mantive o CTA no Direct para não encaminhar pessoas ao runtime sem GO.
9. Não agendei publicação: Instagram não está conectado no Metricool e não há mídia vertical pronta.

## Entregável
`deliverables/AUX-03/20261117-AUX-03-campanha-checklist-pre-venda-produtores.md`

## Canal
Instagram Reel/carrossel/Stories → Direct.

## CTA
Enviar `CHECKLIST`.

## Métrica principal
Conversão de alcance em leads qualificados: produtores responsáveis por uma produção real em preparação que solicitam o checklist.

Métrica de negócio: primeiro evento publicado em até 7 dias após a qualificação, quando o fluxo público estiver liberado.

Baseline: N/D.

## Evidências
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Playbook de Direct: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261103-W3-playbook-respostas-stories-produtores.md
- Kit página do evento: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261111-AUX-03-kit-pagina-evento-que-converte.md
- Guia check-in: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261113-AUX-03-guia-checkin-qr-code-para-produtores.md
- Guia line-up: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261114-AUX-03-guia-lineup-artistas-divulgacao.md

## Próxima ação
Conta principal conectar Instagram ou confirmar publicação manual e fornecer mídia vertical aprovada. Depois, AUX-03 acompanha respostas voluntárias pelo Direct com acesso autorizado. A landing/cadastro só deve ser usada após GO de runtime.

## Precisa da conta principal
SIM — conexão/disponibilização do Instagram, aprovação da mídia e confirmação do fluxo público para eventual encaminhamento posterior.
