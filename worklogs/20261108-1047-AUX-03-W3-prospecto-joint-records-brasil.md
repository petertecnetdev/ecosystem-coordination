# AUX-03 W3 — Worklog 2026-11-08 — Prospecto Joint Records Brasil

## Objetivo
Conquistar um novo produtor para a Cutinapp por meio de prospecção contextualizada baseada em um evento real publicado em Goiânia.

## Área
Aquisição de produtores, prospecção comercial e ativação.

## Oportunidade
A página pública do Mosh Pit Fest informa evento em 21/11/2026, das 22h às 06h, na Las Vegas - Casa de Show, Goiânia/GO, e identifica Joint Records Brasil como produtor. A página oferece o botão “Fale com o produtor”. Não há evidência suficiente para afirmar recorrência do festival; a abordagem se refere à próxima produção, sem pressupor nova edição.

Fonte: https://www.sympla.com.br/evento/mosh-pit-fest/3613539

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, claim ativo AUX-03-W3, orchestration/STATE.md, WORKER_REGISTRY.md, assignments/AUX-03/W3.md, o plano CUTINAPP_COLD_START_GROWTH.md e o worklog/entregável de 07/11.
- Confirmei que o assignment W3 anterior está DONE, com fallback para a função-base de aquisição e conversão.
- Verifiquei que a sequência lifecycle pós-cadastro de 07/11 já cobre a etapa produção criada → primeiro evento publicado; não repeti essa entrega.
- Evitei duplicar as abordagens já preparadas para Raphaela Gentil e Taberna Music Pub.
- Consultei Metricool: marca cutinapp, ID 7119630; `networksData` contém somente `gbpData`, sem Instagram conectado.
- Identifiquei novo prospecto e canal de contato na página pública do evento.
- Produzi uma mensagem específica para Joint Records Brasil, com CTA DEMO, propondo demonstração para uma próxima produção sem interferir na venda atual.
- Não enviei mensagem, não agendei contato, não publiquei conteúdo, não alterei código, não fiz merge/deploy e não acessei VPS.

## Entregável
deliverables/AUX-03/20261108-W3-prospecto-joint-records-mosh-pit-fest.md

## Canal
Botão público “Fale com o produtor” na página Sympla do Mosh Pit Fest.

## CTA
**DEMO** — aceitar uma demonstração breve do fluxo de criação de página pública, configuração de ingressos e compartilhamento.

## Métrica principal
Primeiro evento efetivamente publicado em até sete dias após a demonstração aceita, dividido pelo total de produtores qualificados que aceitaram a demonstração.

Baseline: N/D. Nenhum contato ou conversão foi realizado/medido.

## Evidências
- Evento e produtor: https://www.sympla.com.br/evento/mosh-pit-fest/3613539
- CURRENT_STATE.md consultado: SHA 5a531c3469945a62f589a4a8d4f228c733144a3a.
- PRIORITIES.md consultado: SHA fd4d80e89b89753bb68c53e2bbd631803e8b2d68.
- BLOCKERS.md consultado: SHA 3472cea057d2835ed7f151bae7f3ec404700f936.
- Orchestration registry: orchestration/WORKER_REGISTRY.md.
- Assignment W3: orchestration/assignments/AUX-03/W3.md.
- Sequência lifecycle anterior: worklogs/20261107-1003-AUX-03-W3-producer-post-signup-activation-sequence.md.
- Configuração Metricool: marca 7119630; somente gbpData retornado em networksData.

## Hipótese
A abordagem contextualizada a um evento em divulgação pode aumentar a taxa de resposta e gerar uma demonstração qualificada. Ainda não testada.

## Próxima ação
Conta principal: decidir autorização para contato externo e confirmar o fluxo público de cadastro/publicação em runtime. Se autorizado, enviar pelo botão “Fale com o produtor”, registrar a resposta e acompanhar a oportunidade até a publicação do primeiro evento.

## Precisa da conta principal?
SIM — autorização de contato e validação do fluxo público.

## Estado final
DELIVERABLE_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_SENT — NOT_SENT — NOT_PUBLISHED — NOT_DEPLOYED — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED.
