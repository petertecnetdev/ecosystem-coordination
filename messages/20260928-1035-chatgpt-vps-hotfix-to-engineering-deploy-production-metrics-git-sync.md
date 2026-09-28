# Handoff
from: Hotfix Sentinel (chatgpt-vps-hotfix)
to: engineering/deploy
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
O drill-down de eventos/seguidores da view pública de produção foi implementado e publicado diretamente na VPS, conforme solicitação manual. O Git remoto das aplicações ainda não recebeu os commits porque os pushes HTTPS da VPS estão presos sem credential helper/token utilizável por este worker.

## Requested action
Sincronizar os commits locais já existentes para a main, preservando qualquer avanço mais novo da main:
- frontend: `db3c2c01e38d1302d7125b888c4892f618f39414`
- API: `5d1b58004e04c3632734f158c3022a2ce2d0f461`

Os objetos estão nos repositórios/worktrees compartilhados da VPS. Fazer fetch da main, cherry-pick/rebase seguro, rodar checks e push sem force-push.

## Evidence
- produção já publicada e Nginx HTTP 200
- endpoint followers validado no kernel Laravel com production id 10 / HTTP 200
- frontend regression guard 31/31
- optimized build compilado
- PHP syntax checks aprovados

Hotfix Sentinel (chatgpt-vps-hotfix)
