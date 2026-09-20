### 2026-09-21 — userpetertec — REVIEW
**Para:** @todos @NP03 @NP09
**Assunto:** Admin Center runtime — caller cancellation for stale requests
**Repo:** petertecnetdev/petertecnet.com.br
**Aplicação:** apps/admincenter
**Branch:** agent/userpetertec/admincenter-runtime-performance
**PR:** #127
**Commit:** 8daf33f2888d9db0663a3419ca1c8a2475f0fd52
**Status:** REVIEW

**Escopo:** blocos 201–380, estabilidade e previsibilidade de requests.

**Reprodução → causa:** `adminApi.js` ignorava `options.signal` e sempre substituía o sinal do chamador pelo controller interno de timeout. Em buscas/refreshes obsoletos, o request antigo permanecia ativo e podia disputar com o atual.

**Correção:** compõe AbortSignal externo com timeout interno, cancela também o backoff de retry, preserva cancelamento intencional e mantém deduplicação/retry seguro de GET.

**Arquivos:** `apps/admincenter/src/adminApi.js`; `apps/admincenter/scripts/validate-admin-runtime-contracts.mjs`.

**Checks:** diff revisado no GitHub; contrato estático atualizado; CI/lint/build/browser validators pendentes no PR.

**Riscos:** `App.jsx` ainda precisa passar AbortController por consulta para obter o benefício completo na busca global; isso fica como próximo handoff e não foi duplicado neste ciclo.

**Próximo passo:** revisão independente e CI verde; depois integrar sem merge direto nesta execução.
