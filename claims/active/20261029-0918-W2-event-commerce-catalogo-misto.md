# Claim exclusivo — W2 catálogo misto sem venda de ingresso informativo

agent: W2
display_name: Cutinapp Independence React
repository: petertecnetdev/cutinapp.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-29T09:18:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
source: messages/20261029-0858-W00-to-W1-W2-atribuicao-condicional-p0.md
scope:
- src/components/event/EventCommercePanel.js
- src/components/event/EventCommercePanel.curatorialW2.test.js (arquivo novo, exclusivo)

## Aceite da atribuição condicional W00
**ACEITO POR W2 | claim `20261029-0918-W2-event-commerce-catalogo-misto.md` | HEAD `a94255d5dfdf44e3c24b239d9199d5d2a5e1ccb0` | blob `ef3b90eb8ae7bf06b824e548aba91c9b03e29e41` | SEM CONCORRÊNCIA identificada.**

Inspeção: 178 claims ativos, handoffs pertinentes, issue #10, decisão W00 de 08h58 e PR React #715. Nenhum claim ativo nomeia especificamente `EventCommercePanel.js` ou o teste novo; autoria histórica não é cessão. O teste existente `EventCommercePanel.test.js` e o helper `checkoutSelectionRecovery.js` ficam fora do escopo. A oferta condicional W00 exige esta reserva antes de editar.

## Escopo estrito
Vetar no componente seleção, stepper, restauração e checkout de `informational_only`, `curatorial_information_only`, `price_known=false`, preço nulo, ausente ou não numérico. Gratuitos explícitos `price=0` continuam válidos. Filtrar restauração recebida do helper legado, sem editar helper alheio; sanitizar persistência e payload. Criar testes Jest do componente em arquivo novo, com CI push no SHA exato.

**Proibido:** `EventViewPage.js` (ViewForge/W01 e Nocturne/W07), auth/sessão W03, utilitários, teste legado, main, branches novas, force-push, merge, deploy e produção. API é autoridade final.

## Gates
Registrar commit real [agent:W2], Jest, lint/build/perf e CI exato; W4 QA independente; SEO snapshots e browser não presumidos. Em conflito de claim/HEAD/blob, interromper edição e escalar nominalmente.
