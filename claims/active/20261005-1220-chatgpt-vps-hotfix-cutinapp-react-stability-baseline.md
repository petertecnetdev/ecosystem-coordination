# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production delivery / CI react stability baseline
task: Atualizar o baseline de estabilidade React para refletir dívida já removida em ProductionCreatePage, porque a validação de main exige que o baseline diminua quando a ocorrência desaparece.
branch: hotfix/20261005-cutinapp-react-stability-baseline
status: working
started_at: 2026-10-05T12:20:00-03:00
depends_on: claims/active/20261005-1216-chatgpt-vps-hotfix-cutinapp-ci-dependency-lock.md
files_or_scope:
- scripts/check-react-stability.js
- Validate Cutinapp workflow
- production deploy/runtime verification

## Notes
Após corrigir `npm ci`, o próximo bloqueio confirmado é o próprio guard de dívida: `ProductionCreatePage.js:array index — debt improved (0/1); reduce the baseline in this PR`. Correção mínima: remover apenas essa entrada obsoleta do BASELINE, conforme instrução do guard.
