# Cutinapp — Operação P0: duas branches (12/10/2026)

owner: W00
repository: petertecnetdev/cutinapp.petertecnet.com.br
policy: COMMANDS.md CMD-005
state: IN_PROGRESS
target: 2 remote branches (main + one shared)

## Resultado verificado pelo GitHub em 12/10

- Inicial: 20 branches remotas
- Excluídas de verdade: 14; três runs GitHub Actions com sucesso
- Restantes: 6 (main, shared e quatro refs históricas congeladas)
- Fonte de trabalho ÚNICA: `cycle/mobile-nav-runtime-validation-20261007`; último SHA consolidado conhecido `ba7c1d714b7c6080617b3e6f6f8c7eb361b18722` (revalidar antes de modificar)
- `main` último SHA após cleanup: `afce1fdf5255bbf0d402e128063ba881f5f4d54a`; commits de manutenção alteraram apenas o workflow branch cleanup
- Primeiro cleanup: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38274070114
- Segundo cleanup: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38274620785
- Terceiro cleanup: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/38274917440
- Todos os workers W0-W4 receberam atualização de automação; AUX recebe regra por CMD-005.
- AUX-01 W1/W2 receberam assignments P0 READY. W3 assignment write bloqueado por OPENAI_SAFETY_CHECKS: não contornar, CMD-005 global continua valendo.

## Integrações de preservação já executadas na shared

1. Campanha encontros `docs/growth/community-meetups-launch-20261008.md`: 42dd39b4fadd14b03889b7515658e8f0c502e663 (blob exato)
2. Worklog encontros `docs/growth/WORKLOG-20261008-aux01-w3-community-meetups.md`: d0ea707387f4b7ee63474211ff31dca055b90b32 (blob exato)
3. Blog `src/pages/blog/BlogArticlePage.js`: 8b7a7eafcd12f2c6db96444451d43ed7a1c5aab3 (blob exato source)
4. Teste de links do blog: ba7c1d714b7c6080617b3e6f6f8c7eb361b18722 (blob exato source)
5. PR #710 e PR #711 fechados como SUPERSEDED (não como merged); suas contribuições são preservadas/equivalentes na shared. Não alegar QA/runtime PASS.

## Quatro branches históricas restantes — NENHUMA pode receber novo trabalho

1. `aux-01/w1-event-ticket-price-label-guard-20261012` — HEAD inicial 337c9ba22a4b97f9bd8d48f09b695105a954f43f, 0/0 contra main anterior. **CLAIM WORKING** AUX-01 W1 20261012-1015; preservar até transferência formal para shared. Correção: Number(null) e Number('') devem ser preço desconhecido, não Grátis; testes null/undefined/whitespace/nonfinite/free_available/zero.
2. `aux-01/w1-item-catalog-promotion-price-parity` — HEAD 037ca10562ce92aeb251ddf140b16c5342e8f289, 4 caminhos exclusivos. `eventItemPricing.js` valida promoção mas preço regular null/blank/NaN ainda arriscado e cart/checkout/API diferem. W1 principal + AUX W1 recuperam seletivamente na shared; W4 QA real + backend authoritative antes de fechar/deletar.
3. `fix/social-preview-entity-images` — HEAD 78f53d696cc61a6247554dce26fa95fac5d93fdf; 5 arquivos alterados (.github/workflows/refresh-seo-sitemap.yml, public/index.html, scripts/generate-seo-snapshots.mjs, src/components/SeoHead.js e SeoManager.js). W3 recuperar OG/image por tipo de entidade e fallback sem sobrescrever alterações recentes de SEO; W4 preview WhatsApp/og validação; deletar após preservação.
4. `refactor/brand-palette-lock` — HEAD 1ac9fd7183dd3bfac8e8b03f2e5a1da61b4ab2e4, PR #707 OPEN e com conflitos: 111 arquivos, scripts check-brand-colors.js/check-overlay-policy.js, package lint:brand, validate workflow; NÃO merge global CSS bruto. W3 extrair guardrails válidos sem desfazer marca vermelha, W4 lint/CI; fechar PR como superseded após integração e deletar source com SHA.

## Regras de entrega dos workers

- **TODOS** implementam na shared, claim exclusivo por arquivo e handoff explícito; nenhuma branch por demanda/worker/AUX.
- W0 único autoridade GitHub merges/deletes, change cycle. Ao concluir e testar: merge shared->main, validar; excluir shared; só depois abrir próxima branch compartilhada derivada de main.
- W4 exige Jest/lint/build reais e QA browser 320/360/390/430 + event/producer auth/cart/QR/checkout. Não considerar sucesso sem execução.
- GitHub validate não roda automaticamente em push `cycle/**` no estado anterior; destravar checks via fluxo permitido sem contornar bloqueio OPENAI_SAFETY_CHECKS.
- O workflow de limpeza de branches no frontend exige HEAD SHA exato e proíbe explicitamente main/shared.
- A criação/edição do workflow na main pode disparar CI/deploy automático; sempre verificar Actions e não declarar deploy sem evidência.
- A cada ciclo: atualizar BRANCH_COUNT_BEFORE/AFTER, PR, SHA, CLAIMS, QA, merges, deletions confirmed, blockers e next action. Nunca parar work streams.

## Critério de encerramento da operação

Verificação remota retorna exatamente `main` + uma shared branch; todas as quatro source refs legadas desapareceram, com entregas exclusivas recuperadas/validadas; nenhum claim ou PR com ref histórica indefinida; CI e QA documentados.
