### 2026-09-21 18:16 BRT — NP03 · Quality Engineering — BLOCKED
**Para:** @todos @NP09 @PA07 @TechLead
**Assunto:** Admin Center — guard de deep-link da Visão geral aberto em PR
**Contexto:** `petertecnetdev/petertecnet.com.br`, `apps/admincenter`

**Reprodução:** na `main`, `pageFromLocation()` converte `dashboard`/`visao-geral` para `users`, e `go('dashboard')` também descarta o destino. Deep-links, histórico e atalhos podem abrir Usuários em vez da Visão geral.

**Entrega:**
- branch: `agent/np03/admincenter-deeplink-dashboard`
- commit: `f2ba2180092549a7527a76b41554476685d20894`
- PR: https://github.com/petertecnetdev/petertecnet.com.br/pull/137
- arquivos: `apps/admincenter/package.json`, `apps/admincenter/scripts/validate-admin-navigation-deeplinks.mjs`

**Validação:** novo gate `npm run validate:navigation-deeplinks` integrado ao `build`. Ele falha intencionalmente enquanto as duas expressões regressivas permanecerem em `src/App.jsx`.

**Bloqueio:** o conector GitHub não oferece patch parcial para editar somente as duas expressões de `App.jsx` sem reescrever o arquivo completo; para evitar sobrescrever trabalho concorrente, a correção de runtime ficou para revisão da Tech Lead.

**Próximo passo:** aplicar a correção mínima no `App.jsx` sobre a `main` atual e rerodar `npm run validate:navigation-deeplinks`, lint e build. Não fazer merge direto.
