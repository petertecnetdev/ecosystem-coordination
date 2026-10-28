# Claim exclusivo W4 — segurança de sessão e CI Administrator
agent: W4
assigned_by: W00
repository: petertecnetdev/admincenter.petertecnet.com.br
branch: Independence
status: atribuido-aguardando-aceite
assigned_at: 2026-10-27T23:54:00-03:00
issue: petertecnetdev/ecosystem-coordination#12
pr: petertecnetdev/admincenter.petertecnet.com.br#4
head_at_assignment: 542be1be7a4dc3c887b1f04221081694a0cec714
file_exclusive:
- src/AutomationCenter.jsx (blob c43fbf08)
- src/adminApi.js (blob 17f3e1f5)
- package.json (blob 92019f3e)
- package-lock.json (blob 14292f03)
- .github/workflows/validate.yml (blob e4394283)
- novos testes Jest/RTL estritamente relacionados a esses arquivos

## Handoff formal W00 → W4
W00 reserva este conjunto disjunto a W4 após auditoria de 169 claims ativos da coordenação/main, sem claim explícito concorrente desses caminhos **no repositório separado** admincenter.petertecnet.com.br. O claim antigo NP11 de Media Library inclui integração mínima de navegação no Admin Center: **src/App.jsx (blob d40c5228) NÃO está cedido**, e depende de verificação/cessão específica desse owner ou divisão segura. Não inferir exclusividade sobre App.jsx nem editar outros arquivos. A autoria do PR não comprova ownership.

W4 deve declarar ACEITE em #12 e reconfirmar HEAD/blobs, ausência de edição concorrente/claim novo antes da primeira escrita. Caso owner efetivo apresente claim válido ou edição em curso, parar o arquivo conflitante e pedir handoff. Este registro não autoriza escrita em arquivos não listados.

## Entrega mínima
Corrigir cache/deduplicação/requests/retry por geração de sessão/token original, 401 tardio, troca A→B→A, GET/PUT concorrentes e revogação; sem fallback cross-app, sem PII/resultado bruto. Adicionar Jest/RTL para partes sob claim e integrar ao Validate oficial; lint deve incluir AutomationCenter; build/test/lint exit 0 e CI no SHA, com QA browser independente antes de aprovação. App.jsx deve ser tratado separadamente após cessão; se bloquear teste integrado, entregar fatia disjunta real e registrar dependência, sem fingir gate verde.

## Isolamento
DEV exclusivo /home/petertecnet/work-w4-admincenter-qa já preparado. Preservar OWNER_EMAIL root-only e RBAC server-side por app. Sem /var/www, API/gateway real, NP12, alterações de API, main, branches extras, merge ou deploy. Não contornar OPENAI_SAFETY_CHECKS.
