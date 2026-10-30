# Claim W2 — regressões de sessão root do Admin Center
agent_id: W2
display_name: W2 — Administrator / segurança
assigned_by: CMD-008 — ordem direta do proprietário, 30/10/2026
aceite: ACEITO W2 (escopo novo, disjunto; não há cessão implícita de arquivos existentes)
repository: petertecnetdev/admincenter.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-30T14:23:00-03:00
issue: petertecnetdev/ecosystem-coordination#12
pr: petertecnetdev/admincenter.petertecnet.com.br#4
head_at_claim: c6846c618b89192074f18313bcb57efa3e3b5d45
files_or_scope:
- src/__tests__/AdminRootSessionW2.test.jsx (arquivo novo, confirmado ausente no HEAD)
exclusions:
- src/App.jsx (blob d40c52289ec2b6fd4f24f222f24baacdcf7ecb3a, ownership histórico NP11; SEM CEDO+ACEITO)
- src/adminApi.js, src/AutomationCenter.jsx e testes já sob claim W4
- API Laravel, arquivos W1, main, deploy, migrations

## Objetivo e segurança
Registrar regressões executáveis para impedir que login/validação antigos limpem ou assumam token de outra sessão em abas concorrentes. Inspeção estática no HEAD mostrou `Login.submit().catch` e callback Google usando `localStorage.removeItem(TOKEN_KEY)` sem comparar snapshot, e `App.validate().catch` removendo token sem epoch; nenhum desses módulos será editado por W2 sem cessão formal. Testes podem ser RED no estado atual, como gate P0 explícito; não alegar sucesso. W00 deve negociar owner NP11 ou patch direto do mantenedor.

## Critérios
- somente novo arquivo de testes;
- publicar commit real na Independence com SHA, Actions e resultado exato;
- preservar OPENAI_SAFETY_CHECKS; se escrita recusada, não contornar;
- handoff owner NP11 / W00 para corrigir App.jsx; QA independente antes de merge.

## Entrega 30/10/2026 — 14h26 BRT
- Código/teste real publicado no Admin Center Independence: `fd1ad3d99b43e3455a5a963a0d19efb82fe19363`.
- Arquivo criado: `src/__tests__/AdminRootSessionW2.test.jsx`, blob `5511c83337cb0fc2f19ba7f5de3e1383ec02f1d6`.
- Validate PR `41098709307` e push `41098700251`: FAILURE no SHA exato; `npm ci` PASS; Jest 48 PASS/2 FAIL, exit 1; lint/build SKIPPED. Ambos falham por `Expected: sessao-B; Received: null`.
- Evidência reproduzida: 401 antigo de `/auth/me` A e erro tardio de login A apagam token B de outra aba. Google callback análogo apenas por inspeção.
- Handoff nominal: [PR #4 comentário 6529033708](https://github.com/petertecnetdev/admincenter.petertecnet.com.br/pull/4#issuecomment-6529033708) e [issue #12 comentário 6529036708](https://github.com/petertecnetdev/ecosystem-coordination/issues/12#issuecomment-6529036708).
- Estado: `bloqueado` para correção do runtime por falta de CEDO+ACEITO de `src/App.jsx` (owner NP11, blob `d40c5228`); testes red intencionais preservados como gate.
- Próxima ação única: W00 obter CEDO+ACEITO NP11 para W2 no HEAD/blob atuais ou exigir patch direto do owner, depois Jest/lint/build/CI/QA. Nenhum merge/deploy.
