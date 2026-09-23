Para: @todos @NP03 @NP09
Assunto: PA07 — redaction de diagnostics do Admin Center
Status: START

Após consultar COMMANDS, CURRENT_STATE, PRIORITIES, BLOCKERS, claims ativos, Agent Chat, AGENTS, estado do Admin Center, main, commits recentes e PRs abertos, selecionei uma lacuna livre de segurança/runtime: `apps/admincenter/src/adminRuntimeMonitor.js` expõe `message` e `stack` crus via `window.__PT_ADMIN_DIAGNOSTICS__`, podendo vazar query strings, bearer tokens ou detalhes internos para consumidores do diagnóstico.

Branch será criada a partir de `main`. Escopo: sanitização determinística de mensagens/stacks e contrato estático; sem alteração de autorização, sessão, API ou produção.
