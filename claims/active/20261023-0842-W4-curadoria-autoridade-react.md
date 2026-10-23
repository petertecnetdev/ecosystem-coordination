# Claim W4 — contrato de apresentação administrativa da curadoria
agent: W4
display_name: W4 QA Administrator React
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: QA e interface React isolada de curadoria / autoridade por aplicação
task: Adicionar contrato de leitura explícita operations.view, distinção owner local vs root global e testes Jest, sem ativar rota
branch: Independence
status: working
started_at: 2026-10-23T08:42:00-03:00
depends_on: issue #12; handoffs/20261023-0737-W03-root-payload-gate.md
files_or_scope:
- src/components/admin/curatorialAccessPolicyW4.js
- src/components/admin/curatorialAccessPolicyW4.test.js
- src/components/admin/CuratorialAccessSummaryW4.jsx
- src/components/admin/CuratorialAccessSummaryW4.test.js

## Notes
Arquivos novos exclusivos; não alterar ApplicationAdminGate.js, navegação, AuthService, API/PHP, caminhos de W1/W2/W3, branches ou runtime. O payload is_root da API pode estar incorreto para owner local; nunca usar essa flag para conceder root ou acesso. A UI só exibe acesso de leitura quando authorized=true, application_id validado e operations.view explicitamente presente. Exibir is_owner somente como identidade de app. Sem checkout, merge ou deploy.

## Andamento
Objetivo: prevenir elevação visual e comercial por flags de contexto inconsistentes.
Estado: em-andamento
Responsável: W4
Feito: auditoria de COMMANDS.md, NP12, claims e regressão W03 efd757e.
Em andamento: implementação e testes em arquivos isolados.
Falta: Jest/build oficiais exit 0, SHA e CI no commit, revisão W00.
Próxima ação: publicar commit somente na branch Independence após validação; sem runtime ativado.
