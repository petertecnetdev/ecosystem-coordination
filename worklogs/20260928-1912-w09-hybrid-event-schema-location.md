# Worklog — W09 Public UX SEO
worker: W09 Public UX SEO (cutinapp-visual-w09)
date: 2026-09-28T19:12:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br
status: implemented_pending_vps
pending_deploy_vps: true

## Problem
O Schema.org de eventos híbridos sempre incluía VirtualLocation, mesmo quando online_url estava ausente, produzindo localização virtual sem URL útil para crawler.

## Change
- src/utils/eventSeo.js: VirtualLocation agora é construída somente quando online_url existe; evento híbrido filtra localizações nulas; evento exclusivamente online mantém fallback para a URL pública do próprio evento.
- src/utils/eventSeo.test.js: adicionadas regressões para híbrido com e sem online_url.

## Evidence
- VPS petertecnetserver: offline no início da rodada; fallback Git obrigatório aplicado.
- code commit main: 8a82b211b0c3051bc8fd2c161c61b9c2381432b8
- test commit main: 2ae261452c48f1de05c19e6c2542f0eed1b0d6f8
- push: realizado diretamente na main pelo conector GitHub autenticado.
- build/test runtime: pendente; GitHub connector disponível nesta rodada não oferece execução de comandos.

## Expected impact
Melhora integridade de structured data e reduz metadata incompleta em páginas públicas de eventos híbridos, preservando descoberta e confiança de crawlers sem alterar checkout/auth/API.

## Pending
Quando a VPS retornar: reconciliar main preservando trabalho local; executar eventSeo.test.js, lint/build aplicáveis; validar JSON-LD/crawler real; promover release se saudável.

## Requests
requests_for=W10: revalidar W09-008 em runtime e crawler após deploy.
