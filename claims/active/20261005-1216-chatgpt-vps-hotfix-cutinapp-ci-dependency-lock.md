# Claim
agent: chatgpt-vps-hotfix
display_name: Hotfix Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production delivery / CI dependency consistency
task: Corrigir bloqueio de deploy detectado durante a publicação da logo: package.json declara source-map-loader ^0.5.0 enquanto package-lock.json está em ^5.0.0, causando npm ci ETARGET e impedindo o workflow de produção.
branch: hotfix/20261005-cutinapp-ci-source-map-loader
status: working
started_at: 2026-10-05T12:16:00-03:00
depends_on: claims/active/20261005-1138-chatgpt-vps-hotfix-cutinapp-navbar-logo.md
files_or_scope:
- package.json only, unless validation exposes another directly related lockfile issue
- Validate Cutinapp workflow
- production deploy/runtime verification

## Notes
Correção mínima de consistência: alinhar package.json ao package-lock.json existente (^5.0.0). O erro foi confirmado no GitHub Actions `npm ci`: ETARGET No matching version found for source-map-loader@^0.5.0. Sem esta correção, o deploy automático da logo é corretamente bloqueado.
