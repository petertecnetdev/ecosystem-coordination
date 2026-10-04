# W08 → repo admin — API cleanup batch F

Redução física concluída: 25 refs removidas e inventário API 466 → 441. Admin Center segue com duas refs; PR #2 source ausente e PR #1 em KEEP por API #534.

A Branches API continua retornando `protected=false` para Admin Center `main`.

## Resultado

- ADMINCENTER_COUNT: 2
- API_BRANCH_COUNT_BEFORE: 466
- DELETED_VERIFIED_THIS_RUN: 25
- API_BRANCH_COUNT_AFTER: 441
- NET_REDUCTION: 25
- HIGH_RISK_SECOND_REVIEWS: 11
- DELETE_READY_REMAINING: 0 (no shard executado)
- UNIQUE_USEFUL: 0
- NEW_BRANCHES_CREATED: 0

## Execução verificável

- Workflow commit: `a9d9d5bbb5d5a62186cbb0709e6792578d48d2ce`
- Run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37168514307
- Job: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37168514307/job/111336454435
- Conclusão: `success`
- Log: `deleted=25 already_absent=0 changed=0 failures=0`
- Pós-verificação: todas as 25 refs ausentes; inventário live 441.

## Admin Center

- Refs live: `main`, `feat/media-library-admin`.
- PR #2 mergeado; source permanece ausente.
- PR #1 permanece KEEP: aberto, enquanto API #534 está aberto e não mergeável.
- A Branches API continua reportando `protected=false` para `main`; ação administrativa permanece pendente.

## Refs excluídas

- `feat/payflow-mvp-complete` @ `2893e420d92925043c2eb09cfb5e2cc4a4a37696`
- `feat/payment-recovery-state` @ `ac40c2cbbf0c4fd6390fdcfb22eab566fd05a752`
- `feat/peter-platform-v1-architecture` @ `f0f9bc8bc9f52d6914d083b39d0cbed495d808b6`
- `feat/plat-plan-entitlements` @ `bc55f013581fe070f51d4860de381813bb6ac358`
- `feat/plat-production-ready` @ `867989175f306ef794f22d6a04928942c8a40de9`
- `feat/production-owner-transfer-20260904` @ `4d89a16aba631149c31eecc285217fc70838b3fd`
- `feat/profitability-risk-priority` @ `e5a397b6ecbec01f62f5d7644d505053d2f0662a`
- `feat/recovery-channel-observed-economics` @ `e09df958a78b57e9639f0de1c2d324520ba9d940`
- `feat/profitability-break-even-revenue-gap` @ `9870ec5db9fb9ad597553505173dc2d73fa95842`
- `feat/public-catalog-hardening-20260903` @ `1706c0af31fc17fa2070fa6c9b8a2eeb15095f37`
- `feat/recovery-surface-revenue-economics` @ `e64aab9d8c3708e414365205d6efd27d5607e232`
- `perf/ecosystem-hardening-20260908` @ `ab31c5a8c0311d08c81991e9651b95cd7744d12a`
- `production/rasoio-20260902` @ `11e92922beac7cb9f390edd00b999f549efd6707`
- `profit/recovery-surface-economics-20260909` @ `f43e3b0c494dbe165931d3df4ce713ec14972451`
- `profit/recovery-surface-maturity` @ `9e42e04cc76e47fe6d648076b7696b506c716f3f`
- `profitability/checkout-recovery-deeplink` @ `62ea8c99fa599bbd18d6abeaced8aca2c80b6380`
- `profitability/pix-recovery-timing-experiment` @ `36e8c950264e8ee155cee60f26053287335fe6bd`
- `revenue/enforce-staff-entitlement-plat` @ `dc571588420338813a0527ae0990e2c3c0fba014`
- `revenue/recover-subscription-intent` @ `d9ea1a6776a931013d55d0ada9461aed4f833e81`
- `revenue/subscription-pix-email-recovery` @ `9c24c4113b53b64cf02fa93e69fe11e92ca964c4`
- `review/api-core-hardening` @ `dc4325c70ab724b6d60b924741e91e0c6bbb4b80`
- `security/dependency-audit-20260904` @ `449878d11cfea629dea4b636b703aabc0446b512`
- `seo/dynamic-sitemap-20260908` @ `5bdc08f724769082c5057f83c3451e23cf84a7ab`
- `tmp-noop` @ `78e3d91baec5f179b2be2ebd46d90d2006e08792`
- `w08/artist-claim-relations` @ `2533a1d54ea2aacd04f34eb66ff58a2d17066e9e`

## Segunda revisão high-risk

- `feat/payment-recovery-state`: 2 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `feat/peter-platform-v1-architecture`: 19 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `feat/plat-plan-entitlements`: 1 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `perf/ecosystem-hardening-20260908`: 1 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `production/rasoio-20260902`: 2 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `profitability/checkout-recovery-deeplink`: 2 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `profitability/pix-recovery-timing-experiment`: 3 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `revenue/enforce-staff-entitlement-plat`: 2 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `revenue/recover-subscription-intent`: 4 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `revenue/subscription-pix-email-recovery`: 1 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.
- `review/api-core-hardening`: 3 arquivo(s) sensível(is); integração canônica, supersessão ou obsolescência confirmada na auditoria e revalidação.

## Controles

- Comparação fresca contra `main` e diff merge-base→branch nos divergentes.
- Revalidação imediata e trava pelo SHA antes de cada exclusão.
- Nenhum ref W07, UNIQUE_USEFUL, implementação ativa ou FIN-P0 incluído.
- Nenhum branch auxiliar, deploy/VPS, force-push, reset ou `update_ref` de exclusão.

