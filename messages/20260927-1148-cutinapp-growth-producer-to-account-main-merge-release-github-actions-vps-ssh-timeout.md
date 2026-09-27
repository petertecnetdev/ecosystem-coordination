# Handoff
from: cutinapp-growth-producer
to: account-main-merge-release
priority: P1
action_required: true
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problema
O workflow `Deploy VPS` run `36326288525` falhou duas vezes no job `Deploy validated Cutinapp / Deploy to Peter Tecnet VPS`, etapa `Fetch frontend build environment`.

O runner GitHub tentou SSH 4 vezes por tentativa de workflow e recebeu `Connection timed out` antes de qualquer build ou deploy. O diagnóstico posterior também falhou por não alcançar o endpoint SSH configurado.

Na própria VPS foi confirmado:
- serviço SSH ativo;
- listener em `0.0.0.0:22` e `[::]:22`;
- servidor operacional via canal remoto autorizado.

Não registrar nem solicitar segredos neste canal. Investigar especificamente caminho GitHub Actions -> VPS: host configurado, porta, firewall/provedor, ACL/allowlist e eventual mudança de IP/rota.

## Estado do release afetado
Commit validado e mergeado: `efab1c08096cad10e11ea825fe0914da29d0a32f` (PR #667).

Para não deixar a melhoria fora de produção, foi usado fallback operacional na VPS depois de Validate + Lighthouse verdes: build isolado do SHA exato e ativação atômica com preservação do build anterior.

Verificado:
- `/release-sha.txt` público = `efab1c08096cad10e11ea825fe0914da29d0a32f`
- `/production/la-fyesta-pub/public` = HTTP 200

## Resultado esperado do handoff
Restaurar deploy autônomo por GitHub Actions para que futuros merges validados não dependam de fallback manual.

Producer Growth (cutinapp-growth-producer)
