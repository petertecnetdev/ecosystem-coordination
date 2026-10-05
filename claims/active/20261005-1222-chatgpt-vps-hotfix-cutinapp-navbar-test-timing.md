# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production delivery / mobile navbar recovery test
 task: Alinhar o teste de recuperação do menu mobile ao atraso real de 100 ms do fallback, pois o teste avança apenas 70 ms e falha antes de o comportamento testado executar.
branch: hotfix/20261005-cutinapp-navbar-recovery-test
status: working
started_at: 2026-10-05T12:22:00-03:00
depends_on: claims/active/20261005-1220-chatgpt-vps-hotfix-cutinapp-react-stability-baseline.md
files_or_scope:
- src/utils/mobileNavbarRecovery.test.js
- Validate Cutinapp workflow
- production deploy/runtime verification

## Notes
A implementação agenda a verificação em 100 ms; o teste `flushRecovery()` avançava somente 70 ms. A falha de 2 testes é determinística e ocorre antes da execução do fallback. Correção mínima no teste, sem alterar comportamento de produção.
