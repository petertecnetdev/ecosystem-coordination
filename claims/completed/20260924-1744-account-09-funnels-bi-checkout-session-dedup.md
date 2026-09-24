# Claim Completion
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Corrigir a métrica de abandono de checkout para deduplicar por session_key e excluir somente sessões com conclusão correspondente.
status: completed
completed_at: 2026-09-24T17:49:00-03:00
branch: agent/account-09-funnels-bi/checkout-session-dedup
related_pr: #522
commit: b3a42ce7a20ce0570095abe3482273a798be9d66

## Evidence
- PR #522 aberto como draft.
- O cálculo agora consulta sessões distintas iniciadas sem sessão concluída no mesmo app/período.
- Teste unitário alinhado ao contrato do cálculo.
- PR #514 recebeu comentário apontando a correção e a necessidade de supersessão.
- Nenhuma operação de produção, migration, force-push ou ação destrutiva foi realizada.
