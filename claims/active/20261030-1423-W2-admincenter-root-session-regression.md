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
