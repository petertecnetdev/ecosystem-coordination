# AUX-03 W3 — Retorno do CTA para produtor já autenticado — 2026-10-25

Owner: AUX-03-W3
Priority: P1
Status: CODE_COMMITTED — PR_DRAFT_OPEN — MERGEABLE — CI_RUNNING — NOT_MERGED — NOT_DEPLOYED

## Objetivo
Aumentar ativação de produtores que já possuem conta e entram na landing pública para criar sua primeira produção/evento.

## Área / oportunidade / obstáculo único
Área: conversão e ativação, jornada `/for-producers` → `/register` → `/production/create` → `/event/create`.
Obstáculo confirmado por inspeção do código da main: `guestRoute` em `src/App.js` redireciona **qualquer** usuário autenticado que chega a `/register` para `/dashboard`, mesmo quando o CTA da landing define `state.from=/production/create`. A intenção de criar produção se perde para contas existentes.

## Coordenação / antiduplificação
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/active/`, `orchestration/assignments/AUX-03/W3.md` e worklogs recentes. O assignment W3 anterior foi concluído em 24/10 com handoff do PR #724; este trabalho é uma fricção **diferente** do mesmo funil. O PR #724 altera somente `ProducerLandingPage.js`; esta correção altera `App.js` e novo utilitário/testes. Sem tocar no PR #724.

## Trabalho realizado / entregável
1. Inspecionados `src/App.js`, `RegisterPage.js`, `EmailVerifyPage.js`, `ProductionCreatePage.js`, `AuthContext.js` e rotas da landing.
2. Criada branch `fix/aux03-producer-logged-in-signup-20261025` a partir da main.
3. Implementado `producerRegistrationRedirect` para respeitar intenção de produtor em `location.state.from`, `?from=/production/create` e `?role=producer`, sem aceitar destinos externos.
4. Ajustado `guestRoute`: conta já autenticada com intenção de produtor segue para criação da produção; se ainda precisar verificar e-mail, segue para `/email-verify` com retorno e `acquisitionSource` preservados; rotas de login e cadastro normal continuam com comportamento anterior.
5. Criados cinco testes unitários cobrindo contexto, verificação, deep links/UTM e rejeição de entradas inválidas.
6. Commit final `eb2fb6880d524dbe726134a8d98b634f1e716705`; PR #725 aberto como draft, verificado como mergeable=true. Na consulta inicial, workflows Validate Cutinapp e Lighthouse CI estavam `in_progress`; sem declarar testes aprovados.

## Canal / CTA / métrica
Canal: landing pública e tráfego social/orgânico de retorno.
CTA: **Cadastrar minha produção**.
Métrica principal: **produções criadas / cliques únicos no CTA da landing entre usuários já autenticados**, por `acquisition_source`.
Métrica de negócio: primeiros eventos publicados em até 30 dias por esse grupo.
Baseline, conversão e uplift: **não medidos**.

## Confirmado / hipótese / recomendação
Confirmado: redirecionamento incondicional ao dashboard para usuários autenticados em `/register` na main; branch e PR #725 criados.
Hipótese: remover o desvio pode recuperar produtores que já têm conta e querem começar a produzir.
Recomendação: validar CI e percurso mobile completo antes de integrar.

## Evidências
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #724 (copy, sem sobreposição): https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Main de App.js: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js
- Commit final: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/eb2fb6880d524dbe726134a8d98b634f1e716705

## Próxima ação / conta principal
**Conta principal necessária: SIM.** W00 revisar PR #725, aguardar/inspecionar CI, testar em mobile 320/360/390/430 com conta verificada/não verificada e com visitante, conferir telemetria `producer_production_created` com origem, integrar quando aprovado e verificar versão realmente servida. Coordenar integração do PR #724 sem duplicar trabalho.

Nenhum deploy, build local, alteração na VPS ou teste funcional de runtime foi executado.
