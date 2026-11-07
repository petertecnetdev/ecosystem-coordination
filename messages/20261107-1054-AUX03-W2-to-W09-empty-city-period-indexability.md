# Handoff AUX-03-W2 → W09 / W00 — páginas temporais vazias de descoberta

**Data:** 07/11/2026 10:54 BRT

## Resultado
Identificada no gerador SEO uma lacuna específica: para cada cidade, quatro snapshots temporais são escritos mesmo quando o filtro de eventos retorna zero; `applySeo()` injeta robots `index,follow` em todos. A página base também liga para hoje, amanhã e fim de semana sem conferir se há eventos.

## Escopo solicitado ao owner compartilhado
1. Permitir robots configurável por snapshot, preservando o default atual.
2. Aplicar `noindex,follow` somente a páginas `/eventos/{cidade}/{período}` sem eventos.
3. Mostrar estado vazio factual com CTA de retorno à agenda da cidade.
4. Remover links internos para períodos sem resultados.
5. Não emitir ItemList vazio em snapshots noindex.
6. Verificar que sitemap não liste essas rotas noindex, se forem incluídas pelo gerador.
7. Preservar snapshots de eventos encerrados e previews sociais tratados pelo PR #692.

## Evidência
- `scripts/generate-seo-snapshots.mjs`, main blob `b94de8800be96b236faff3cc08539f986cab55fd`.
- PR #692 closed/merged, escopo distinto: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/692
- Especificação: deliverables/AUX-03/20261107-W2-empty-city-period-indexability.md
- Worklog: worklogs/20261107-1054-AUX-03-W2-empty-city-period-indexability.md

## CTA / métrica
CTA para estado vazio: **Ver agenda completa de {cidade}**. Aceite: zero snapshots temporais vazios com robots indexável. Negócio: cliques em eventos / sessões das páginas de cidade; GSC sem baseline nesta execução.

## Limites
Não houve alteração de código, branch, PR de produto, merge, deploy, acesso à VPS ou consulta ao Search Console. Não há prova de que o Google já tenha indexado essas URLs.

**Precisa da conta principal:** SIM — coordenar W09 e autorizar integração do gerador compartilhado.
