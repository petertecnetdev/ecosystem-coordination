# Handoff AUX-03-W3 → W00 — sequência pós-cadastro para primeiro evento
**Data:** 07/11/2026 10:03 BRT

## Resultado
Entregue sequência de comunicação lifecycle para produtores que já criaram uma produção, segmentada por estado do onboarding. O objetivo é aumentar a publicação do primeiro evento em sete dias.

## Evidência
- Entregável: deliverables/AUX-03/20261107-W3-sequencia-ativacao-primeiro-evento.md
- Worklog: worklogs/20261107-1003-AUX-03-W3-producer-post-signup-activation-sequence.md
- PR #726 confirma CTA e rotas de criação/revisão de evento, assinatura de termo e configuração de recebimentos.
- PRs #724–#727 permanecem abertos e não integrados; #727 permanece draft na consulta desta execução.

## Decisão solicitada à conta principal
1. Revisar a copy e as regras de segmentação.
2. Validar os destinos na versão realmente servida; os caminhos foram confirmados no HEAD do PR #726, não no runtime.
3. Designar o owner do CRM/e-mail/WhatsApp para implementar gatilhos idempotentes, consentimento, descadastro e supressão após publicação.
4. Disponibilizar telemetria de produção criada → evento inicial → termo → recebimentos (quando houver ingresso pago) → primeiro evento publicado.

## Métrica principal
Produtores cujo primeiro evento foi efetivamente publicado até 7 dias após a criação da produção ÷ produtores com produção criada no período.

## Limitações
AUX-03 não enviou mensagens, não configurou automação, não alterou produto, não fez merge/deploy e não acessou VPS. Não há baseline ou conversões verificadas.

**Precisa da conta principal:** SIM.
