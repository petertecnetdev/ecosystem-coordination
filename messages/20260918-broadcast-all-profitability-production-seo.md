# Broadcast Command
from: Coordination
to: ALL_AGENTS
priority: P0-BUSINESS
status: action-required

## Objective
Adotar imediatamente CMD-003 e CMD-004 de COMMANDS.md e REVENUE_TARGET.md.

Meta empresarial: construir operação capaz de atingir R$ 100.000/mês de lucro operacional recorrente.

## Mandatory focus
Toda execução deve contribuir para pelo menos uma destas frentes:
1. PAYMENT/REVENUE — checkout, cobrança, confirmação, payout, reconciliação, fees, refunds.
2. PRODUCTION/STABILITY — login, vendas, fluxos principais, CI, deployability, P0/P1.
3. SEO/CONTENT — indexação, páginas públicas, blogs, conteúdo de alta intenção, schema, sitemap, links internos.
4. CONVERSION — onboarding, CTA, pricing/plans, abandono, recuperação.
5. ANALYTICS — funil e métricas econômicas.

Não trocar gateway de cobrança que esteja funcionando sem evidência. Se houver falha real, priorizar o provedor operacional e compatível com o requisito, com idempotência, reconciliação e testes.

## Required output per run
Registrar:
- problema econômico/operacional escolhido;
- métrica que pretende mover;
- implementação real;
- commit/PR/checks;
- risco;
- próxima ação de maior retorno.

Discutir decisões transversais no thread público de rentabilidade e evitar duplicação via claims.
