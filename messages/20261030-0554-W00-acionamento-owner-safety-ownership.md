# [agent:W00] Independence — despacho de execução, 30/10/2026 05h54 BRT

## Evidência e decisão
**MERGE BLOQUEADO; SEM DEPLOY.** O impedimento deixou de ser somente diagnóstico: dois executores com escopo/claim válido tiveram a escrita de produto recusada por `OPENAI_SAFETY_CHECKS`, e outros arquivos seguem sob claims de terceiros. Não tentar contorno, alterar `main`, criar branches ou novas automações.

Fontes consultadas: `main/COMMANDS.md` blob `3f3e61ba797331cdf8833e0262aaeb1076ef2311`, issues #10/#12 e comentários até W4 05h46, **182** `claims/active` (incluindo novo W3), **4** `handoffs`, PR API #546/React #715/Admin #4 e CIs dos HEADs.

| Repositório/PR | HEAD exato | CI no SHA | Status |
|---|---|---|---|
| API #546 | `15645886ab0c26a810333465b338839be7dc4cff` | Actions #41014925977, validate 732 PASS/22 FAIL/3 SKIP, exit 1; arquitetura exit 1 | OPEN, merge vedado |
| API MySQL 8 dirigido | mesmo HEAD | Actions #41014919001, 36 PASS/358 assertions, exit 0, migração/rollback/remigração e 2 processos | Aprovado **somente** neste escopo por W4; `Http::fake`, não gateway real |
| React #715 | `f043781a896a2d90d4f10eb72630eb2e7d48a0f6` | Actions #41013520330, Jest 1689 PASS, build/lint exit 0; gerador SEO snapshot interno exit 1 | OPEN/DRAFT, QA browser pendente |
| Admin #4 | `c6846c618b89192074f18313bcb57efa3e3b5d45` | 48 PASS históricos, sem QA integrado novo | OPEN/DRAFT, somente segurança essencial |

Branches remotas verificadas: API **4→4**, React **9→9**, Admin **2→2**. Comparação `main...Independence`: API ahead 272/behind 0, React ahead 139/behind 0, Admin ahead 17/behind 0. Nenhum merge, deploy, edição da main ou commit de produto por W00. Testes locais W00 NÃO_EXECUTADOS (exit N/A).

## Decisão executiva: remover o gargalo de execução, não repetir inspeções

**A. Patch de proveniência self-service — owner W3 / mantenedor.** Novo claim exclusivo `claims/active/20261030-0531-W3-organization-selfservice-provenance.md` blob `8e565a59d575152616bef6f50f45934e49ca32d6`, sobre `app/Domain/Organizations/Services/OrganizationService.php` blob `139ba5441d5e3c09efa1785bae832afd5a498182` e novo teste `tests/Feature/Independence/OrganizationSelfServiceProvenanceW3Test.php` (404). Tentativa de escrita de W3 foi **recusada por OPENAI_SAFETY_CHECKS**; HEAD/blob intactos, teste inexistente, PHPUnit local N/A. **Ação exigida do mantenedor:** aplicar o patch autorizado diretamente ou habilitar fluxo de escrita permitido para W3 **sem contornar o bloqueio**. Aceite: `listing_source=organizer_self_service`, `published_by_user_id` do usuário autenticado no INSERT; payload não pode forjar `app_id`, legado, verificação ou autorização comercial; PHPUnit dirigido + CI novo no SHA + QA W4. **Não** criar autorização de venda automaticamente.

**B. PII da reivindicação — owner W2 / mantenedor.** `src/components/independence/UnverifiedListingPanel.js` blob `71e041d71d1c018049beabd70c59ce2e6576bd56`, teste blob `039434661a80ae7ab1cf1b3c16ea5559c3b3adb1`. O POST já falha fechado, mas o formulário de nome/telefone/consentimento pode ser renderizado antes de escopo canônico válido. Tentativa W2 **recusada por OPENAI_SAFETY_CHECKS**. **Ação do mantenedor:** aplicar patch autorizado ou providenciar fluxo permitido; exigir CTA desabilitado e ausência de campos/consentimento para app ausente/0/inválido/conflitante, entidade sem ID e usuário incompleto; Jest, build, CI novo no SHA, revisão W4. Não afirmar correção de epoch com esse patch.

**C. Pix payout — owner Ledger `account-main-revenue-financial`, depois W1.** Claim WORKING `claims/active/20260918-0136-account-main-revenue-financial-payout-idempotency.md` blob `3607278d586d2e813fe5ec7aeb781214ec5a0b6a` cobre `tests/Feature/FinancialPayoutSecurityTest.php` blob `fa7d6d84506b6cb468e6c048e1c19c7a4ccc29`. Teste linha 209 espera `CPF verificado`, runtime responde `documento verificado` (CPF/CNPJ), preservando HTTP 422 e zero destinos. **Ação Ledger:** `CEDO PARA W1 | agent_id | claim | HEAD | blob | SEM CONCORRÊNCIA` + `ACEITO POR W1`, **ou** patch direto com SHA/teste/CI. Não alterar proteção do serviço só para satisfazer string.

**D. Controller e auth — decisão nominal do mantenedor, sem ownership presumido.** `EventManagementController.php` blob `9c6eeac0f1f80700d79b07ac853fc8ad350d3998` sob Atlas+Genre: ambos cedem com HEAD/blob e W3 aceita, ou owner entrega patch; duplicação não pode herdar autorização comercial; autoria real, RBAC app-scoped, DELETE bulk com autorização transacional/lock e teste HTTP. React `AuthContext.js` blob `78917a5a`, `authTokenStorage.js` `25bbc63d`, `authSessionSync.js` `79b446dc`, `AuthService.js` `a188c9fa`: identificar owner/claim, CEDO+ACEITO W2 ou patch direto para epoch A→B→A e logout tardio.

## Trabalho não duplicado
- **W1:** segurança Pix/Asaas, checkout curatorial fail-closed; não repetir MySQL concorrente aprovado; sem tocar payout Ledger até cessão.
- **W2:** reivindicação/PII e auth; não repetir tentativas bloqueadas, obter via mantenedor patch permitido e QA.
- **W3:** somente CI/regressões Independence; preservar claim próprio, solicitar aplicação permitida, sem AgentChat e sem controller reservado.
- **W4:** QA independente dos novos SHAs, HTTP/checkout, browser mobile 320/360/390/430, auth, RBAC, rollback e contratos; manter veto enquanto houver falha.
- **W00:** coordenar decisões e PRs, sem merge até CI completo verde no SHA exato e QA independente. NP12 é escopo de produto: somente após gates P0 validar fontes autorizadas, deduplicação, fichas reais, ingressos informativos sem venda e operação; não desviar W1/W2 antes.

**Próximo passo executivo único — owner `petertecnetdev`:** providenciar **execução permitida** dos dois patches já preparados por W2/W3, sem bypass de safety; registrar SHAs/CI e entregar a W4. Em paralelo, exigir resposta binária Ledger e Atlas/Genre para as cessões. Se não houver patch autorizado, o bloqueio é operacional comprovado, não entrega concluída.
