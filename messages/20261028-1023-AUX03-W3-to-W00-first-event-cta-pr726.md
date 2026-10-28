# AUX-03 W3 → W00 — PR #726 — Primeiro evento acima do checklist

date: 2026-10-28
priority: P1
owner: AUX-03-W3
status: REVIEW_REQUESTED — CI_RUNNING — NOT_MERGED

## Decisão solicitada
Revisar https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726 e decidir integração depois de CI e QA mobile.

## Por que agora
No onboarding de produtor, a ação de criar/revisar primeiro evento aparecia depois de nove cartões de configuração, dificultando a descoberta do CTA no celular. PR #726 adiciona CTA principal antes do checklist, mantém a assinatura do termo e separa recebimentos de publicação, sem alterar a API.

## QA mínimo
1. Mobile 320/360/390/430: CTA visível acima do progresso e sem overflow.
2. Sem `initial_event.id`: botão abre `/event/create?productionId=<id>`.
3. Com `initial_event.id`: botão abre `/event/edit/<id>`.
4. Com `steps.agreement=false`: mostrar `Assinar termo para publicar` e abrir contrato da produção.
5. Com `steps.agreement=true`: esconder CTA de contrato.
6. Confirmar criação/publicação real e política de recebimentos, sem prometer publicação/venda sem requisitos.
7. CI Validate Cutinapp + Lighthouse green antes de sair do draft.

## Coordenação
PRs #724 (oferta da landing) e #725 (retorno pós-login) continuam independentes. Nenhum deploy VPS.

## CTA / métrica
CTA: Criar primeiro evento / Revisar primeiro evento.
Métrica principal: primeiros eventos publicados em até 7 dias da primeira visita ao onboarding / produtores únicos visitantes da tela.
Sem conversões medidas.
Worklog: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261028-1023-AUX-03-W3-first-event-onboarding-cta-pr726.md

NEXT_ACTION: W00 validar CI, QA mobile e aprovar/mesclar PR #726 se aprovado.
