# Claim exclusivo W3 — proveniência real de produção self-service (Independence P0)

agent: W3
display_name: W3 — Desbloquear API e CI Independence
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-30T05:31:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
related_pr: petertecnetdev/api.petertecnet.com.br#546
owner: W3
head_at_claim: 15645886ab0c26a810333465b338839be7dc4cff
files_or_scope:
- app/Domain/Organizations/Services/OrganizationService.php
- tests/Feature/Independence/OrganizationSelfServiceProvenanceW3Test.php (novo)
blob_at_claim:
- app/Domain/Organizations/Services/OrganizationService.php: 139ba5441d5e3c09efa1785bae832afd5a498182
- tests/Feature/Independence/OrganizationSelfServiceProvenanceW3Test.php: AUSENTE (404)

## Exclusividade e escopo
- Consultados COMMANDS.md, issues #10/#12, despacho W00 30/10 04h54, 181 entradas de claims/active, 4 handoffs e PRs API #546, React #715, Admin #4.
- Não identificado claim específico destes caminhos. Atlas reserva taxonomia de eventos/locais, Genre reserva EventManagementController; W1 reserva ListingCommercePolicy, EventPassService e testes financeiros. Não editar qualquer um desses arquivos.
- Objetivo: persistir na criação autenticada de organização autoria e origem **reais** do cadastro self-service, usando valores do servidor, sem autoaprovar titularidade ou autorização comercial, sem classificar registro novo como legado.
- Critérios: fonte self-service e published_by_user_id persistidos no mesmo INSERT; não aceitar marcadores de aprovação enviados pelo cliente; testes HTTP para origem, autoria, isolamento por app e comércio fail-closed.
- Revalidar HEAD e blob antes de editar. Se claim conflitante, interromper; sem CEDO presumido.
- Preservar OPENAI_SAFETY_CHECKS, sem branch nova, main de produto, merge, deploy ou VPS.
- CI oficial no SHA exato e revisão W4; controller de eventos 9c6eeac0 permanece reservado por Atlas+Genre sem CEDO+ACEITO.
