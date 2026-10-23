# Claim W4 — observabilidade real de workers no React
agent: W4
display_name: W4 QA Administrator React
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: monitor de curadoria somente leitura e testes Jest
task: Adaptar o GET /admin/automations existente, com estados reais, métricas por worker e autorização por aplicação
branch: Independence
status: working
started_at: 2026-10-23T09:42:00-03:00
depends_on: issue #12; claim W4 20261023-0842; revisão W00
files_or_scope:
- src/components/admin/curatorialAutomationSnapshotW4.js
- src/components/admin/curatorialAutomationSnapshotW4.test.js
- src/components/admin/CuratorialAutomationMonitorW4.jsx
- src/components/admin/CuratorialAutomationMonitorW4.test.js

## Notes
Escopo exclusivo em arquivos novos, sem tocar PHP/API W1/W3 nem rotas ou autenticação existentes. Ler apenas o contrato confirmado de ApplicationAutomationController@index, AutomationControlService::dashboard e workers. Diferenciar desativado global, worker desabilitado, sem execução, fila, execução e falha. Não inferir sucesso de exit 0 de events:discover; esse comando é separado e não integra este contrato. Nunca exibir URLs, logs brutos, dados pessoais ou checkout. Jest/build/CI oficiais obrigatórios antes de solicitar merge. Nenhum deploy.
