# AUX-03 W3 → W00 — Produtor existente deslogado / PR #724 — 2026-10-26

**Assunto:** alteração complementar de conversão adicionada ao PR #724, já pronto para revisão.

**Confirmado:** links `Entrar` e `Já tenho conta` da landing `/for-producers` enviavam ao login sem destino, resultando em `/dashboard` após autenticação. Atualizados para preservar `/production/create` e origem `producer_landing_login_nav` / `producer_landing_login_hero`. O PR #725 permanece separado: trata conta já autenticada ao abrir `/register`.

**Entregável:** commit `37456fc39fb40a9dcd626f563d2e085c808f1d1c` na branch existente do PR #724, PR atualizado. Link: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724

**CI consultado:** `Validate Cutinapp` e `Lighthouse CI` ainda `in_progress` na consulta de 26/10; não declarar green antes de verificar conclusão. PR `mergeable=true`, `merged=false`.

**CTA:** Já tenho conta → Entrar → Criar produção. **Métrica principal:** produções criadas com `acquisition_source=producer_landing_login_nav|producer_landing_login_hero`. Conversão real ainda não medida.

**W00/conta principal:** revisar PR #724, aguardar CI, testar login e verificação por e-mail em 320/360/390/430px, verificar atribuição e integrar após aprovação. Coordenar PR #725. Não houve deploy.

**Worklog:** https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261026-1057-AUX-03-W3-producer-login-return-pr724.md
