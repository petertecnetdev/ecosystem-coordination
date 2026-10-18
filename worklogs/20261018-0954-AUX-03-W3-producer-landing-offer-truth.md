# AUX-03 W3 — Producer Acquisition & Conversion — 2026-10-18

- objective: remover promessa de assinatura/trial incorreta antes de direcionar tráfego para a landing de produtores.
- area: landing pública `/for-producers` e atribuição de cadastro.
- opportunity: texto atual anuncia assinatura e 30 dias de trial; `api/config/subscriptions.php` declara `subscription_enabled=false` e `monetization_model=transaction_fee` para Cutinapp.
- work_done: leitura de CURRENT_STATE, PRIORITIES, BLOCKERS, claims/active, worklogs e assignment W3; leitura do React atual, registro e telemetria; composição de alteração no branch existente `fix/aux03-producer-offer-truth-20261015`.
- deliverable: copy corrigida + três CTAs `Cadastrar minha produção` + evento `producer_landing_cta_clicked` com acquisition_source, preservando `/register` -> `/production/create`.
- channel: landing orgânica, tráfego social e indicação.
- CTA: Cadastrar minha produção.
- metric: produções criadas / cliques únicos nos CTAs; resultado final: primeiros eventos publicados.
- evidence: `src/pages/ProducerLandingPage.js` SHA 10d8549; `config/subscriptions.php` SHA 380033c; teste estático de 5 condições passou; `update_file` foi BLOQUEADO por safety checks, portanto SEM commit/PR/deploy.
- hypothesis: corrigir expectativa comercial reduz abandono pré-cadastro (não medido).
- next_action: conta principal deve aplicar mudança na branch existente, rodar build/testes mobile, abrir PR e medir o funil.
- main_account_required: YES.
- owner: AUX-03-W3
- status: PATCH_PREPARED / GITHUB_WRITE_BLOCKED / NOT_MERGED / NOT_DEPLOYED.
