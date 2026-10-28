# AUX-03 / W3 — 2026-10-28 — CTA de primeiro evento no topo do onboarding

owner: AUX-03-W3
date: 2026-10-28 10:23 America/Sao_Paulo
priority: P1
status: CODE_COMMITTED — PR_OPEN_DRAFT — CI_RUNNING — NOT_MERGED — NOT_DEPLOYED
area: aquisição → cadastro → produção → primeiro evento publicado
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Objetivo
Aumentar a proporção de produtores que chegam ao primeiro evento publicado após entrar no onboarding da produção, especialmente no mobile.

## Oportunidade / obstáculo único
A página `src/pages/production/ProducerOnboardingPage.js` apresentava progresso e **nove cartões de configuração** antes do card com os botões `Revisar primeiro evento` / `Criar evento`. No celular, a ação de ativação ficava abaixo do checklist. A inspeção de código confirma a ordem; **não há medição real de abandono ou teste mobile concluído**.

## Coordenação
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/active/`, `worklogs/`, `plans/CUTINAPP_COLD_START_GROWTH.md`, assignment AUX-03/W3 (DONE, fallback_to_base_role=true) e PRs #724/#725 (abertos e independentes). Claim próprio `claims/active/20261009-1600-AUX-03-W3.md` permanece working. Não alteradas landing, login, API, contratos ou escopo de outros workers.

## Trabalho realizado / entregável
- Branch `feat/aux03-first-event-cta-20261028` criada a partir da main.
- Commit `45ad350c45b8dd4d34a0634c792c8cedbc803b21` altera somente `src/pages/production/ProducerOnboardingPage.js`.
- Card de ativação inserido **antes** do progresso e dos nove cartões: CTA `Criar primeiro evento` (sem evento) ou `Revisar primeiro evento` (com `initial_event.id`).
- CTA secundário `Assinar termo para publicar` somente quando `steps.agreement` está pendente.
- Copy distingue termo necessário para publicação de recebimentos necessários para vendas pagas; sem contornar contrato, KYC ou regras financeiras.
- Título e subtítulo priorizam a jornada do primeiro evento à primeira venda.
- PR **#726** criado como draft para revisão e QA: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726

## Confirmado / evidências
- Comparação GitHub `main...feat/aux03-first-event-cta-20261028`: um commit à frente, zero atrás, um arquivo, 20 linhas adicionadas e três removidas.
- Verificações estáticas: CTA criar/revisar, contrato condicional, copy legal e ordem CTA antes do progresso = PASS.
- GitHub PR #726: open, draft=true, merged=false, mergeable=true após atualização de metadata.
- Workflows `Validate Cutinapp` e `Lighthouse CI`: in_progress na última leitura; **não declarar CI verde**.
- Código de origem: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProducerOnboardingPage.js
- Fluxo de contrato: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProducerContractsPage.js
- PRs complementares aguardando revisão: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724 e https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725

## Hipótese
Aumentar a visibilidade do CTA principal antes das etapas administrativas reduz a desistência no onboarding e aumenta a publicação do primeiro evento. **Sem uplift ou volume de conversão medidos.**

## Canal / CTA / métrica
- Canal: onboarding interno mobile-first, tráfego adquirido por landing, indicação e conteúdo.
- CTA principal: **Criar primeiro evento** / **Revisar primeiro evento**.
- Métrica principal: produtores únicos que publicam seu primeiro evento em até 7 dias da primeira visualização de onboarding / produtores únicos que visualizaram onboarding (coorte). Sem instrumentação comprovada, **não medido**.
- Métrica intermediária: cliques únicos no CTA principal / visualizações únicas do onboarding.
- Evento de sucesso: primeira publicação confirmada pela API; não contar mero clique, cadastro ou evento em rascunho.

## Próxima ação / responsável
W00/conta principal: aguardar CI, QA 320/360/390/430px, validar 4 estados (com/sem evento; contrato aceito/pendente), verificar ausência de scroll horizontal, revisar PR #726 e decidir merge. Testar publicação real e atribuição quando ambiente estiver disponível. **Não fazer deploy VPS por padrão**.
Conta principal necessária: SIM (QA E2E, aprovação e merge).
NEXT_ACTION: CI + QA mobile + revisão W00. Estado de produção: NOT_DEPLOYED / RUNTIME_NOT_VERIFIED.
