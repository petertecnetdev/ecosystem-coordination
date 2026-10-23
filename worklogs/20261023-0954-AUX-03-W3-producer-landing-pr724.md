# AUX-03 W3 — Producer acquisition / landing offer truth — 2026-10-23

Owner: AUX-03-W3
Priority: P1
Status: PR_OPEN_DRAFT — MERGEABLE — NOT_MERGED — NOT_DEPLOYED

## Objective
Aumentar aquisição e ativação de produtores, removendo comunicação comercial contraditória entre landing pública e modelo comercial configurado na API.

## Área e oportunidade
Landing pública para produtores → cadastro → criação da produção → primeiro evento publicado. A main de `src/pages/ProducerLandingPage.js` ainda anuncia assinatura/trial de 30 dias. Trabalho anterior já tinha corrigido copy na branch `fix/aux03-producer-offer-truth-20261015`, commit `212cb5abbd7c36869e3b8558e3a736adf769ddd8`, mas não havia PR.

## Trabalho realizado
1. Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/active/`, `worklogs/` e assignment W3. Claim W3 existente reutilizado.
2. Comparados arquivos `src/pages/ProducerLandingPage.js` da main e da branch; apenas esse arquivo modificado (10 linhas adicionadas, 10 removidas).
3. Pesquisados PRs existentes para a branch: nenhum encontrado.
4. Aberto **PR #724** em draft para revisão, usando branch e commit existentes. Confirmado depois como **mergeable=true** pelo GitHub.
5. Nenhum deploy/VPS realizado.

## Entregável e canal
PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
Canal: landing pública de produtores / aquisição orgânica e social.

## CTA e métrica
CTA: **Cadastrar minha produção**, destino `/register` com `state.from=/production/create` e `acquisitionSource` por posição (nav, hero, bottom).
Métrica principal: **primeiros eventos publicados em até 30 dias / produtores cadastrados pela landing**.
Métrica intermediária: **produções criadas / cadastros originados pela landing**.
Baseline/conversão: não medidos; instrumentação ponta a ponta ainda requer validação.

## Evidências
- Main e branch lidas diretamente em 2026-10-23.
- Compare: 1 commit à frente, 41 atrás; somente `ProducerLandingPage.js` alterado.
- PR #724 aberto e mergeable=true após atualização do status no GitHub.
- A API com modelo de monetização por transação havia sido verificada em execuções anteriores; revalidar com responsável comercial antes do merge.

## Hipótese
Eliminar promessas não suportadas de assinatura/trial reduz abandono de visitantes qualificados.

## Recomendação / próxima ação
Conta principal necessária: **SIM** para revisão comercial, CI, QA mobile 320/360/390/430, verificação do fluxo cadastro → produção → evento e merge do PR #724. Não declarar runtime verificado sem teste em produção. W00 deve consumir este handoff e atualizar assignment W3 quando apropriado.
