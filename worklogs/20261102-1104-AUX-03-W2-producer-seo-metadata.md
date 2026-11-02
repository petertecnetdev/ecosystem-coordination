# AUX-03 W2 — Worklog 2026-11-02

## Objetivo
Corrigir a mensagem SEO e os dados estruturados da landing de produtores para refletir a oferta comercial real da Cutinapp e evitar aquisição com expectativa de trial/assinatura inexistentes.

## Área
SEO de landing pública, aquisição e conversão de produtores.

## Oportunidade
A configuração da API define Cutinapp como transacional, sem assinatura obrigatória. O `SeoManager.js` em main ainda comunicava “30 dias grátis” e assinatura após trial no title, meta description e JSON-LD. O PR #724 corrige a copy visível da landing, mas não corrige seus metadados.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims ativos, worklogs e entregas AUX-03 recentes.
- Verifiquei os últimos ativos AUX-03 de 02/11 (Reel de primeiro evento e Reel de organização de participantes) para não duplicar conteúdo social.
- Inspecionei os PRs #722, #724, #725 e #726. Permanecem abertos e sem merge na consulta; #724 corrige a copy visível de produtores.
- Consultei `config/subscriptions.php`: `subscription_enabled=false`, `monetization_model=transaction_fee`, `plans=[]`.
- Consultei a main do frontend no SHA `9b5502cdf2dca098bc73a465d58d7274b596d0a4` e confirmei os metadados desatualizados em `src/components/SeoManager.js`.
- Consultei o workstream W09: seus pontos tratam `/production/:slug/public`, `SeoHead.js` e snapshots; a mudança AUX-03 limita-se ao bloco `PRODUCER_SEO` de `/for-producers`, sem alterar os blocos de Produção/Eventos ou os geradores.
- Criei branch própria `fix/aux03-producer-seo-offer-truth-20261102`, alterei somente `src/components/SeoManager.js` e abri PR #727 em draft.
- PR #727 tem dois commits, um arquivo alterado (+4/-4). CI Validate Cutinapp e Lighthouse CI foram iniciados e estavam `in_progress` na última consulta; não declarar testes aprovados.

## Entregável
- Código: PR #727 — https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Especificação: deliverables/AUX-03/20261102-W2-seo-metadados-landing-produtores.md

## Canal
Google orgânico → /for-producers → cadastro → produção → primeiro evento publicado.

## CTA
“Cadastrar minha produção” (copy visível no PR #724).

## Métrica
- Intermediária: cadastros atribuídos a /for-producers / sessões únicas da landing.
- Negócio: produtores que publicam primeiro evento em até 7 dias / produtores cadastrados pela landing.
- Baseline e conversões: N/D; não medidos nesta execução.

## Evidências
- API config: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php
- Main frontend: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/9b5502cdf2dca098bc73a465d58d7274b596d0a4/src/components/SeoManager.js
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- HEAD PR #727: `b745b97ecfe1753cddb6aa34d3f3da6ffe1ca72e`
- CI Validate #41459268768 e Lighthouse #41459268813: ambos `in_progress` na última consulta.
- O site público abre no crawler de pesquisa apenas com o shell “Ative o JavaScript”; isso não comprova falha para visitantes reais nem indexação. Não houve QA de runtime/crawler nesta execução.

## Próxima ação
Aguardar CI; revisar; liberar PR #727 para revisão se os checks passarem. Integrar #724 e #727 juntos ou em sequência coordenada. Depois validar a landing em mobile e conferir metadados/Schema no ambiente servido. Medir cadastros e primeiro evento publicado somente com telemetria disponível.

## Precisa da conta principal?
SIM — revisão e integração dos PRs #724/#727, QA mobile e validação do ambiente publicado.

## Estado final
`COMMITTED — PUSHED — PR_OPEN_DRAFT — CI_IN_PROGRESS — DEPENDS_ON_PR_724 — NOT_MERGED — NOT_DEPLOYED — CONVERSION_NOT_MEASURED`.
