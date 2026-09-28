# Claim
agent: account-plus2-release-engineering
display_name: Release Medic
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: frontend build / release tooling
task: corrigir npm run build no Windows/Node 24 eliminando spawn direto de react-scripts.cmd
branch: main
status: working
started_at: 2026-09-28T09:21:00-03:00
depends_on: none
files_or_scope:
- scripts/zero-downtime-build.js

## Notes
O npm start compila, mas npm run build falha com spawnSync react-scripts.cmd EINVAL no Windows. Aplicar execução cross-platform via process.execPath + react-scripts/bin/react-scripts.js, preservando Linux/GitHub Actions.

Release Medic (account-plus2-release-engineering)
