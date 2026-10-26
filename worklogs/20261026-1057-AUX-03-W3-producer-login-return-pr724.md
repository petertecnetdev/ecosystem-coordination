# AUX-03 W3 — Login de produtor existente preserva criação da produção — 2026-10-26

Owner: AUX-03-W3
Prioridade: P1
Estado: CODE_COMMITTED — PR_UPDATED — NOT_MERGED — NOT_DEPLOYED

## Objetivo
Aumentar a ativação de produtores que já possuem cadastro, mas estão deslogados ao visitar a landing `/for-producers`.

## Área e oportunidade — obstáculo único
Área: conversão/ativação, `/for-producers` → `/login` → `/production/create` → `/event/create`.
Confirmado por inspeção da main e da branch do PR #724: os links **Entrar** (navbar) e **Já tenho conta** (hero) enviavam para `/login` sem `location.state.from`. O `LoginFormComponent` usa `/dashboard` como destino padrão sem contexto; assim, o produtor deslogado que escolhia entrar perdia a intenção de cadastrar a produção. Esta fricção é distinta do PR #725, que corrige usuário **já autenticado** ao abrir `/register`.

## Coordenação e antiduplificação
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/assignments/AUX-03/W1.md`, `W2.md`, `W3.md`, worklog AUX-03 de 25/10, PRs #724/#725 e busca por PRs relacionados. Tentativa de abrir diretórios `claims/active/` e `worklogs/` pela integração retornou erro de diretório, mas o worklog conhecido e os commits recentes foram lidos. Reaproveitada a branch existente do PR #724 porque a alteração é no mesmo arquivo, sem criar PR conflitante.

## Trabalho realizado
1. Inspecionados `ProducerLandingPage.js` (main e branch #724), `LoginFormComponent.js`, `RegisterPage.js`, `ProductionCreatePage.js` e regras de rota em `App.js`.
2. No arquivo `src/pages/ProducerLandingPage.js` da branch `fix/aux03-producer-offer-truth-20261015`, criado `producerLoginState(acquisitionSource)` que envia destino interno `/production/create?acquisitionSource=...`.
3. Links **Entrar** e **Já tenho conta** passaram a transportar respectivamente `producer_landing_login_nav` e `producer_landing_login_hero`.
4. Mantidos os três CTAs **Cadastrar minha produção** e suas fontes existentes.
5. Commit remoto `37456fc39fb40a9dcd626f563d2e085c808f1d1c` confirmado por leitura da branch; PR #724 atualizado com escopo, QA e métrica.

## Entregável e canal
Entregável: correção frontend direta de navegação/atribuição em landing pública; PR #724 atualizado.
Canal: landing pública mobile-first / tráfego orgânico, social e indicação.
CTA: **Já tenho conta** / **Entrar** → autenticar → **Criar produção**.

## Métrica
Principal: quantidade de **produções criadas** com `acquisition_source` em `producer_landing_login_nav` ou `producer_landing_login_hero`.
Secundária: taxa de produções criadas por cliques nos dois links, após instrumentar/validar o denominador.
Negócio: primeiros eventos publicados em até 30 dias por produtores dessa origem.
Baseline/uplift: NÃO MEDIDOS.

## Confirmado, hipótese e recomendação
**Confirmado:** os dois links descartavam `state.from`; o login usa destino do state ou dashboard; `ProductionCreatePage` aceita `acquisitionSource` na query; commit e atualização do PR foram gravados.
**Hipótese:** levar o produtor existente deslogado diretamente ao cadastro de produção pode reduzir abandono entre login e ativação.
**Recomendação:** revisar e testar a jornada real em mobile, inclusive e-mail não verificado e login Google/Instagram, antes do merge; não confundir código commitado com runtime verificado.

## Evidências
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Commit: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/37456fc39fb40a9dcd626f563d2e085c808f1d1c
- Fonte login: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/auth/LoginFormComponent.js
- Fonte produção: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProductionCreatePage.js
- PR complementar, sem duplicação: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725

## Próxima ação / conta principal
**Conta principal necessária: SIM**, para CI/build, QA funcional 320/360/390/430px, revisão e merge do PR #724, integração coordenada com PR #725 e validação da versão realmente servida. Não houve testes locais React, teste E2E, publicação de conteúdo, envio de mensagens, deploy ou alteração na VPS.
