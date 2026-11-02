# AUX-03 W2 — Metadados SEO da landing de produtores

**Data:** 02/11/2026  
**Área:** SEO editorial, landing pública, aquisição e conversão de produtores  
**Prioridade:** P1

## Oportunidade confirmada

A configuração real da API em `config/subscriptions.php` define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e `plans=[]`. Porém, em `main` SHA `9b5502cdf2dca098bc73a465d58d7274b596d0a4`, o bloco `PRODUCER_SEO` de `src/components/SeoManager.js` ainda dizia “30 dias grátis” e assinatura após o trial no title, na meta description e no JSON-LD.

O PR #724 corrige a copy visível de `ProducerLandingPage.js`, mas não altera os metadados do `SeoManager.js`. Sem a correção, o snippet de busca e os dados estruturados continuariam comunicando uma oferta incompatível.

## Metadados propostos e implementados no PR #727

- **Title:** Plataforma para produtores de eventos | Cutinapp
- **Meta description:** Crie sua produção, publique eventos e organize ingressos e participantes. Comece sem assinatura obrigatória; taxas por transação podem se aplicar.
- **Canonical:** https://cutinapp.petertecnet.com.br/for-producers
- **Schema.org:** WebPage + Service, sem trial, assinatura obrigatória, preço ou percentual inventado.
- **CTA da página:** Cadastrar minha produção (copy visível tratada pelo PR #724).

A descrição tem 146 caracteres e comunica o modelo sem ocultar a possibilidade de taxas.

## Trabalho realizado

- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims ativos, worklogs e entregas AUX-03 recentes.
- Verifiquei diretamente o código da main, a configuração comercial da API e o PR #724.
- Confirmei que o escopo W09 cobre SEO da rota pública de produção e snapshots globais; a alteração aqui é somente o bloco `PRODUCER_SEO` de `/for-producers`. Nenhuma função de SEO de evento/produção ou gerador de snapshot foi modificada.
- Criei branch própria `fix/aux03-producer-seo-offer-truth-20261102`.
- Alterei somente `src/components/SeoManager.js`.
- Abri PR #727 como draft. CI Validate Cutinapp e Lighthouse CI iniciaram; resultado ainda pendente nesta gravação.

## Dependência e segurança editorial

**Não integrar antes do PR #724 ou no mesmo release.** A copy visível de `/for-producers` em main ainda anuncia trial/assinatura; integrar somente os metadados criaria divergência entre snippet e conteúdo visível.

Não publicar ou solicitar indexação com base apenas no commit. A validação de runtime/crawler e a publicação dependem de integração e ambiente servido.

## Canal, CTA e métricas

- **Canal:** Google orgânico → landing de produtores → cadastro → produção → primeiro evento publicado.
- **CTA:** Cadastrar minha produção.
- **Métrica intermediária:** cadastros atribuídos à landing / sessões únicas de `/for-producers`.
- **Métrica de negócio:** produtores que publicam o primeiro evento em até 7 dias / produtores cadastrados pela landing.
- **Baseline:** N/D; nenhuma conversão foi medida nesta execução.

## Evidências

- API: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php
- Frontend antes da alteração: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/9b5502cdf2dca098bc73a465d58d7274b596d0a4/src/components/SeoManager.js
- PR #724 (copy visível): https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #727 (metadados): https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Branch HEAD: `b745b97ecfe1753cddb6aa34d3f3da6ffe1ca72e`
- W09 workstream: escopo de SEO público de produção distinto, sem alteração de suas funções.

## Próxima ação

1. Aguardar CI Validate e Lighthouse no SHA do PR #727.
2. Revisar o diff e marcar pronto para revisão se ambos passarem.
3. Integrar PR #724 e #727 na mesma janela/release, com QA mobile da landing.
4. Após publicação real, verificar title, description, canonical, JSON-LD, snippet e compartilhamento.
5. Medir cadastros e primeiro evento publicado; não inferir conversões sem telemetria.

**Precisa da conta principal:** SIM — revisão/integração dos PRs #724 e #727 e validação da landing servida.