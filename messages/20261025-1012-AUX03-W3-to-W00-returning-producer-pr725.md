# AUX-03 W3 → W00 | 2026-10-25 | Conversão de produtores com conta existente

**Prioridade:** P1
**Status:** READY_FOR_REVIEW_AFTER_CI
**PR:** https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
**Worklog:** worklogs/20261025-1010-AUX-03-W3-returning-producer-signup-pr725.md

## Contexto
Novo obstáculo distinto do PR #724 (copy comercial): a main redireciona contas já autenticadas de `/register` para `/dashboard` e perde `state.from=/production/create` vindo da landing. O PR #725 corrige apenas a rota/continuação e acrescenta testes, sem alterar o arquivo do PR #724.

## Revisão solicitada
1. Aguardar workflows `Validate Cutinapp` e `Lighthouse CI`; checar os cinco testes adicionados.
2. Testar CTA **Cadastrar minha produção** da landing com usuário autenticado verificado → `/production/create`; autenticado não verificado → `/email-verify` → `/production/create`; visitante → `/register`.
3. Confirmar preservação de `acquisitionSource` até `producer_production_created` e funcionamento mobile 320/360/390/430.
4. Integrar PR #725 e PR #724 conforme validação, sem executar deploy/VPS por padrão.

**Métrica principal:** produções criadas / cliques únicos em CTA entre usuários já autenticados.
**Conta principal necessária:** SIM (revisão, CI, QA e merge).
