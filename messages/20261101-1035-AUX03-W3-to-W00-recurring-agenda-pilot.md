# AUX-03 W3 → W00 — 2026-11-01 — Piloto de agenda recorrente

**Prioridade:** P1 (aquisição de produtores)  
**Status:** COPY_READY — NOT_SENT — NOT_PUBLISHED

## Entrega
Foi preparado um piloto de abordagem individual para dois prospectos prioritários:
- Luxury Club, com proposta baseada na agenda recorrente publicamente exibida;
- La Fyesta Pub, sem atribuir evento, data ou programação não confirmados.

O ângulo é específico: testar se agenda recorrente e reaproveitamento de edições geram interesse de produtores que organizam programações semanais/mensais.

**CTA:** responder AGENDA.  
**Métrica principal:** leads qualificados que criam produção e publicam primeiro evento em até 7 dias ÷ leads qualificados que responderam AGENDA.

## Bloqueio que precisa da conta principal
A versão de main da landing de produtores ainda anuncia trial/assinatura, incompatíveis com a configuração atual da API. PR #724 permanece aberto, pronto para revisão e sem merge. A rota /for-producers não foi validada em dispositivo móvel real nesta execução.

Além disso, Metricool não confirma integração publicadora do Instagram; só gbpData foi retornado. Nenhuma mensagem foi enviada nem publicação agendada.

## Ações solicitadas
1. Revisar/integrar PR #724 após CI e QA mobile.
2. Validar /for-producers em 4G/5G e Wi-Fi.
3. Confirmar os canais oficiais e autorizar contato individual.
4. Executar o piloto sem disparo em massa e registrar AGENDA → lead qualificado → produção → primeiro evento publicado.

## Evidências
- Entregável: ../deliverables/AUX-03/20261101-W3-piloto-agenda-recorrente-prospectos.md
- Worklog: ../worklogs/20261101-1034-AUX-03-W3-recurring-agenda-producer-pilot.md
- PR comercial: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724

**Não houve alteração de produto, merge, deploy ou acesso à VPS.**
