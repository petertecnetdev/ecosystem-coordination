# Worklog — Cutinapp transactional email inline logo

agent: Postmaster (chatgpt-mail-reliability)
date: 2026-10-01
repository: petertecnetdev/api.petertecnet.com.br
priority: P1

## Problem
Emails transacionais da Cutinapp referenciavam a logo por URL publica do frontend. O Gmail exibiu o alt text no lugar da imagem; logs de producao mostraram que `/images/logo.png` teve resposta 404 transitoria em um momento anterior, embora atualmente responda 200. Proxies de imagem de clientes de email podem manter a falha em cache.

## Implementation
- adicionada copia versionada da logo Cutinapp em `resources/mail/brands/cutinapp/logo.png`;
- `ApplicationMailBrandingService` agora fornece `logo_inline_path` apenas quando a identidade configurada padrao esta em uso;
- caminhos locais sao validados com `realpath`, legibilidade e confinamento ao `base_path`;
- layout compartilhado de email tenta `message->embed()` e usa CID inline, com fallback para a URL publica;
- branding dinamico/override remoto continua usando a propria URL, sem ser substituido pelo asset bundled;
- adicionados testes unitarios para o branding e para renderizacao da notificacao.

## Evidence
- commit: `0e03275d7d187efaadbe65bb0f816afad267aef8`
- PR: #538
- CI: API CI run `36863413212` iniciado
- local checks: PHP syntax OK; `git diff --check` OK
- MIME capture: Content-ID presente; Content-Type image/png; Content-Disposition inline; HTML referencia `cid:`; URL remota da logo ausente
- asset SHA-256 igual ao logo atualmente publicado no frontend: `127dfdaac61fa5ea98412ca1b6ec341d702acc17d1a9c6c6e446d8cbd6dc42f0`

## Runtime state
Nao houve merge nem deploy em producao nesta execucao. A correcao esta pronta para integracao apos CI/release.

## Expected impact
Elimina a dependencia do Gmail/GoogleImageProxy, Cloudflare e disponibilidade momentanea do frontend para renderizar a logo padrao nos emails da Cutinapp, reduzindo regressao visual e perda de confianca em comunicacoes transacionais.
