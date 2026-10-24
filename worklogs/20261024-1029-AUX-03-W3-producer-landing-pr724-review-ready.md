# AUX-03 W3 — Producer landing: PR #724 pronto para revisão — 2026-10-24

Owner: AUX-03-W3
Priority: P1
Status: PR_READY_FOR_REVIEW — MERGEABLE — NOT_MERGED — NOT_DEPLOYED

## Objetivo
Aumentar a aquisição e a ativação de produtores da Cutinapp eliminando a promessa comercial incorreta de assinatura/trial na landing pública.

## Área e oportunidade
Canal: landing pública `/for-producers` → `/register` → criação da produção → primeiro evento publicado.
Obstáculo atacado: mensagens de assinatura e trial de 30 dias em `main` divergiam da configuração comercial da API.

## Trabalho realizado
1. Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, assignment `orchestration/assignments/AUX-03/W3.md` e worklog AUX-03 de 23/10. Evitada nova branch e duplicação da correção.
2. Revalidado em 24/10 o contrato comercial da API em `api.petertecnet.com.br/config/subscriptions.php`: `cutinapp.subscription_enabled=false`, `monetization_model=transaction_fee`, `plans=[]`.
3. Inspecionados `main`, branch `fix/aux03-producer-offer-truth-20261015` e patch do PR #724: somente `src/pages/ProducerLandingPage.js`, 10 adições e 10 remoções. Copy da branch retira trial e assinatura obrigatória, ressalva taxas e preserva 3 CTAs com `state.from=/production/create` e fontes de aquisição.
4. Confirmado PR #724 aberto, mergeable=true, sem reviews ou threads até a consulta. Branch 1 commit à frente e 42 atrás da `main`. Consulta a commit statuses retornou lista vazia; isso **não** comprova CI aprovado nem ausência de GitHub Actions checks.
5. Alterado o PR #724 de **draft** para **ready for review**, confirmado pelo GitHub (`draft=false`). Nenhum merge, build, QA mobile ou deploy foi realizado.

## Entregável
PR pronto para revisão: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
Commit da correção: `212cb5abbd7c36869e3b8558e3a736adf769ddd8`

## CTA e métrica
CTA: **Cadastrar minha produção** (3 posições: navegação, hero, final).
Métrica principal: **produtores adquiridos pela landing que publicam o primeiro evento em até 30 dias / produtores cadastrados pela landing**.
Métricas intermediárias: cadastro iniciado, cadastro concluído, produção criada, primeiro evento publicado, com origem preservada. Nenhum baseline ou resultado de conversão confirmado.

## Evidências
- Configuração API: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php
- Diff e estado do PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Main da landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ProducerLandingPage.js
- Coordenação: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/orchestration/assignments/AUX-03/W3.md

## Hipótese
Alinhar oferta comercial ao modelo real pode reduzir abandono pré-cadastro. Impacto não medido.

## Recomendação / próxima ação
**Conta principal necessária: SIM.** Revisar PR #724, executar CI/build, QA mobile 320/360/390/430, validar passagem real de `location.state` até cadastro e produção, confirmar política comercial, integrar na `main` e medir o funil. W00 deve consumir o handoff; não declarar `RUNTIME VERIFIED` antes de verificar versão servida.
