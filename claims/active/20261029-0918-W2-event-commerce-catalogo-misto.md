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

## Entrega W2 — 29/10/2026, ~09h30 BRT

- **HEAD React Independence:** `53d0bf2a4d12e473547b8790b1733bdb676346f7` (PR #715 ainda Draft/conflitada).
- **Commits reais de produto [agent:W2]:** `1a279e1606016e3b7c46264e9016e29bb2b4ed2a` (guardas de seleção/restore/persistência/CTA/checkout e requisições de catálogo obsoletas); `a7125a40295f873b22d90026e41b25e4dcfcf6ae` (novo teste Jest); `859f89d490d178b7f2ddf96a727b9539262ba83f` (assert de quantidade restaurada); `e6ec58a528ac280941e0f49b1c8d82e37030479b` (regex de preço explícito); `68bd9d35d8589eeedb3b76735352468498cd7ddc` (flags numéricas); `53d0bf2a4d12e473547b8790b1733bdb676346f7` (regressões flags e setup act).
- **Arquivos exclusivos alterados:** `src/components/event/EventCommercePanel.js` blob `ef3b90eb8ae7bf06b824e548aba91c9b03e29e41` → `2b3c77429da1b6ce1f028e685332bc73d63701d2`; novo `src/components/event/EventCommercePanel.curatorialW2.test.js` blob `594e665f878b6deed3425f424759ebd12da22ecb`.
- **Comportamento:** tickets `informational_only`, `curatorial_information_only`, `price_known=false/0`, `price=null/undefined`, preço negativo ou inválido não têm stepper nem entram em seleção, persistência ou payload; zero explícito e preço decimal conhecido seguem válidos. Restore antigo é saneado no componente, sem alterar `checkoutSelectionRecovery.js`. Respostas de catálogo obsoletas A→B→A são ignoradas. API continua autoridade final; `EventViewPage.js` e auth não foram tocados.
- **CI exato:** [GitHub Actions push #40873266754](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/40873266754) **COMPLETED/SUCCESS** no SHA `53d0bf2a4d12e473547b8790b1733bdb676346f7`; Jest **179/179 suítes, 1.645 PASS / 6 SKIP / 2 TODO, exit 0**; novo teste do painel PASS. `npm ci`, lints específicos, build SPA e perf budget **SUCCESS/exit 0**. Snapshot SEO: guard global PASS, gerador interno FAIL/fallback, portanto snapshots **não aprovados**. QA browser/mobile **não executado**; Jest/lint/build local **não executados**.
- **Impacto esperado:** impedir intenção de compra indevida de fichas curatoriais em catálogo misto, preservando vendas legítimas e diminuindo risco operacional; impacto econômico não mensurado.
- **Próxima ação única:** **W4** realizar QA independente do HEAD `53d0bf2a`, incluindo catálogo misto, carrinho restaurado, troca de datas e regressão A→B→A; devolver parecer na issue #10. W00 continua responsável por arbitrar handoffs de `EventViewPage.js` (W01/ViewForge e W07/Nocturne) e auth W03 antes de qualquer edição desses arquivos.
- Sem merge, deploy, force-push, alteração na main de produto, VPS, produção ou NP12. Claim permanece `working` até parecer independente.
