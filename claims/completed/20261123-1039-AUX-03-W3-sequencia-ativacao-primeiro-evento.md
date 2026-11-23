# Claim — AUX-03 W3 — sequência de ativação do primeiro evento

agent: AUX-03-W3
status: completed
area: producer activation / onboarding / lifecycle conversion
repository: petertecnetdev/ecosystem-coordination
deliverable: deliverables/AUX-03/20261123-1039-AUX-03-sequencia-ativacao-primeiro-evento.md
worklog: worklogs/20261123-1039-AUX-03-W3-sequencia-ativacao-primeiro-evento.md

## Objetivo
Reduzir abandono entre produção criada e primeiro evento publicado com mensagens condicionadas ao estado real do onboarding.

## Feito
- Consultados estados de coordenação, assignment W3, claims/worklogs recentes e PRs de crescimento.
- Preparada sequência D+1/D+2/D+4 com e-mails, CTAs e deep links baseados nas rotas descritas no PR #726.
- Preparada alternativa WhatsApp apenas com opt-in.
- Definidas regras de supressão, consentimento, deduplicação e parada após publicação.
- Definida métrica de primeiro evento publicado em até sete dias.

## Guardrails
- Não duplicar issue #637 de atribuição, já claimada.
- Não tratar nomes de eventos propostos como telemetria já existente.
- Não enviar mensagens sem consentimento/base válida e autorização.
- Não usar rotas até validar runtime e comportamento após login.
- Não afirmar trial, gratuidade comercial, taxas específicas ou promessa de vendas.
- Não fazer merge/deploy ou acessar VPS.

## Próxima ação
W00/conta principal validar provedor, consentimento, rotas autenticadas e telemetria; depois autorizar piloto.

## Estado
completed — copy e especificação prontos; automação não implementada; mensagens não enviadas.
