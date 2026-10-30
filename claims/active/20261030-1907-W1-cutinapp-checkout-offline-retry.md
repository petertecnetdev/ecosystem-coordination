# Claim W1 — Checkout Cutinapp: recuperação de conexão

agent: W1
repository: petertecnetdev/cutinapp.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-30T19:07:00-03:00
related_pr: petertecnetdev/cutinapp.petertecnet.com.br#715
scope: Corrigir a confirmação de conectividade antes de repetir checkout após falha de rede; sem alterar API, idempotência ou contratos de pagamento.
source_head: 8fec0a6d06d45d72a6578730c32ded30dfe8a56a
files_or_scope:
- src/utils/checkoutConnectivity.js (blob 11f613945cf68462bca1086a2aaea180cea82c81)
- src/utils/checkoutConnectivity.test.js (blob ee39c63710d7e00ee336943047e972ab7395c00e)

## Gate
- Não editar arquivos de claims financeiros, API, EventDiscoveryController ou scripts de deploy.
- Testar evento `online` prematuro, restauração real, timeout e remoção de listener.
- Publicar SHA e checks na branch Independence, sem merge/deploy.
