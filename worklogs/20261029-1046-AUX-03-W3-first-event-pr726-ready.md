# AUX-03 / W3 — 2026-10-29 — PR #726 pronto para revisão (CI verde)

owner: AUX-03-W3
date: 2026-10-29 10:46 America/Sao_Paulo
priority: P1
status: PR_READY_FOR_REVIEW — CI_GREEN — NOT_MERGED — NOT_DEPLOYED
area: ativação de produtores — produção → primeiro evento publicado
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Objetivo
Reduzir atrito até o primeiro evento publicado, deixando o CTA de criação/revisão visível antes das configurações administrativas em dispositivos móveis.

## Oportunidade / obstáculo único
O onboarding da produção exibia nove cartões de configuração antes da ação de criar/revisar evento. A correção foi implementada em 2026-10-28 (PR #726), mas ainda estava em draft com CI pendente. A execução de hoje removeu o bloqueio de **prontidão para revisão** da mesma melhoria, sem abrir outro escopo.

## Coordenação e não duplicação
Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, plans/CUTINAPP_COLD_START_GROWTH.md, claims/active/20261009-1600-AUX-03-W3.md, orchestration/assignments/AUX-03/W3.md, worklog e handoff de 2026-10-28, além dos PRs abertos. Claim próprio segue working; assignment W3 DONE/fallback_to_base_role=true. Não duplicar PR #724 (oferta comercial), #725 (login autenticado), #722 (links editoriais), nem trabalho de W06/W08/W09.

## Trabalho realizado / entregável
- Conferido PR #726 contra a main: **um commit à frente, zero atrás, um arquivo alterado**, 20 linhas adicionadas/3 removidas.
- Inspecionado patch de src/pages/production/ProducerOnboardingPage.js: CTA primeiro evento antes do progresso/checklist; link contratual condicional; copy separa publicação de recebimentos.
- Confirmado GitHub Actions no head SHA `45ad350c45b8dd4d34a0634c792c8cedbc803b21`:
  - Validate Cutinapp: **completed / success**, run **40696425440** (2026-10-29, leitura).
  - Lighthouse CI: **completed / success**, run **40696425376** (2026-10-29, leitura).
- Executado **mark_pull_request_ready_for_review**; leitura de retorno: `draft=false`, `mergeable=true`, `merged=false`.
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726

## Confirmado
CI verde e estado ready-for-review são fatos do GitHub. Não houve QA visual/mobile em navegador, teste funcional E2E, merge, deploy, dados reais de funil ou prova de aumento de conversão.

## Hipótese
Expor a ação de primeiro evento antes dos nove cartões reduz desistência de produtores no mobile; ainda não medida.

## Canal / CTA / métrica
- Canal: onboarding da produção (tráfego vindo de landing, cadastro, indicação e conteúdo).
- CTA: **Criar primeiro evento** (sem initial_event.id) / **Revisar primeiro evento** (com initial_event.id).
- Métrica principal: **primeiros eventos publicados em até 7 dias da primeira visita ao onboarding / produtores únicos que visitaram onboarding**, por coorte.
- Métrica intermediária: cliques únicos no CTA / visitantes únicos do onboarding.
- Fonte de sucesso exigida: publicação confirmada pela API; clique ou rascunho não contam. Instrumentação e números reais: NÃO VERIFICADOS.

## QA pendente / recomendação
W00/conta principal: QA mobile 320/360/390/430px, sem overflow; sem evento → /event/create?productionId=<id>; com evento → /event/edit/<id>; termo pendente → CTA de assinatura; termo aceito → oculto; confirmar comportamento com sessão real e publicação pela API. Aprovar/mesclar PR #726 se validado. Não fazer pull/build/deploy VPS por padrão.

## Próxima ação / responsável
owner: W00 / conta principal
NEXT_ACTION: QA mobile/E2E, revisão e decisão de merge do PR #726.
Conta principal necessária: SIM.
Estado runtime: NOT_DEPLOYED — RUNTIME_NOT_VERIFIED.
