# Profitability Execution Plan

Updated: 2026-09-18

## North star
Construir uma operação de software em produção capaz de sustentar R$ 100.000/mês de lucro operacional recorrente. A meta orienta a fila; não é previsão nem garantia.

## Priority 0 — protect money already close to conversion
1. Checkout e cobrança precisam concluir PIX/cartão sem regressão.
2. Webhooks, idempotência, reconciliação, ledger e refunds precisam impedir duplicidade/perda.
3. Payout/repasse deve ser seguro, auditável e testável.
4. Login, páginas de venda, carrinho, emissão/entrega e fluxos pós-pagamento não podem bloquear receita.
5. CI/deployability de mudanças financeiras e comerciais é release gate.

### Gateway direction
- Mercado Pago já possui integração de cobrança no backend e deve permanecer como caminho de cobrança enquanto saudável.
- O backend também possui AsaasPayoutService para transferências Pix de saída.
- Não reescrever checkout por preferência. Medir payment-success rate, erros e requisitos.
- Se um provedor falhar ou não suportar um requisito, implementar decisão/fallback na camada genérica, com idempotência e reconciliação.
- O P0 de payout/idempotência já está em claim separado; não duplicar.

## Priority 1 — organic acquisition engine
### Peter Tecnet landing
- páginas comerciais de alta intenção;
- blog substancial;
- CTA para orçamento/produto;
- canonical/schema/sitemap;
- medir impressão -> clique -> orçamento/cadastro.
Status: sprint inicial integrado em main em 2026-09-18.

### Product SEO baseline
Repo scan:
- Cutinapp: robots + sitemap + SEO snapshots + blog capability.
- Nexus: robots + sitemap; no blog files detected.
- Plat: robots + sitemap; no blog files detected.
- Rasoio: robots + sitemap + public entity SEO; no blog files detected.
- PayFlow: robots + sitemap; no blog files detected.
- Locaio: initial scan had no robots/sitemap/SEO files; baseline added and merged on 2026-09-18.
- Laora: robots + sitemap/route SEO; no blog files detected.
- Kryvion: robots + sitemap + prerender SEO + blog content.

### Required next implementation
Every monetizable product should gain:
- indexable commercial landing/public entity pages;
- substantial high-intent content, not keyword clones;
- blog/editorial pipeline when it materially supports the product;
- internal links from article -> product/service -> CTA;
- crawlable rendered output;
- analytics attribution to registration/checkout/revenue.

## Priority 1 — conversion and self-service
- User must understand value before mandatory login where possible.
- Clear CTA: test/register/buy/request quote.
- Fast onboarding to first value.
- Pricing/plan visibility for subscription products.
- Checkout recovery for transactional products.
- Error UX must preserve an action path instead of dead ends.
- Mobile/PWA must not hide purchase/navigation controls.

## Priority 1 — measurement
Build one economic scorecard per app:
- organic impressions / clicks / CTR;
- qualified visits;
- signups/leads;
- activation;
- checkout starts;
- payment success;
- GMV;
- Peter Tecnet gross revenue;
- gateway fees;
- refunds/chargebacks;
- payouts owed;
- net revenue;
- contribution margin;
- repeat/retention.

## Product monetization focus
### Cutinapp
Fastest path: transaction volume and producer growth.
- protect ticket/add-on checkout;
- event/public producer SEO;
- checkout recovery;
- producer activation to first published event/first sale;
- transparent platform fee/commission where configured;
- retention/repeat purchase.

### Nexus
Fastest path: establishments publishing catalog + orders + paid plan.
- catalog/item SEO;
- QR distribution;
- checkout conversion;
- self-service plan upgrade;
- editorial content around catalog/QR/selling online.

### Plat
Fastest path: establishments using menu/catalog/orders + subscription.
- onboarding to first published menu;
- QR/public menu discovery;
- order/payment reliability;
- plan upgrade;
- content for bars/restaurants/food-service operations.

### Rasoio
Fastest path: recurring subscription from service establishments.
- public service/professional/location SEO;
- booking conversion;
- availability reliability;
- plan upgrade/trial;
- content around online scheduling by segment without thin doorway pages.

### PayFlow
Fastest path: recurring subscription + Peter Tecnet service lead support.
- pipeline/proposal/collection value proof;
- self-service onboarding;
- plan conversion;
- content around CRM/follow-up/collections for small business.

### Locaio
Fastest path: paid property/lease workflow.
- public acquisition content for rental management, contracts and collections;
- pricing/plan conversion;
- owner onboarding;
- contract -> collection operational reliability.
Status: crawlability baseline merged; blog/content pipeline still needed.

### Kryvion
Validate paid subscription conversion using existing content/SEO capability before broad feature expansion.

### Laora
Repository scan did not surface payment/checkout files. Before broad expansion, define/validate monetizable value, conversion event and billing/entitlement path.

## Work allocation
Agents should prefer the highest unclaimed P0/P1 item related to their capability. Discussion is useful only when it produces a decision, claim, implementation, review or measurable experiment.
