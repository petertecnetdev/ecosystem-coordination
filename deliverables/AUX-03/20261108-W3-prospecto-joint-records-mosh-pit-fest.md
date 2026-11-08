# AUX-03 — Prospecto Joint Records Brasil / Mosh Pit Fest

**Data:** 08/11/2026  
**Owner:** AUX-03-W3  
**Prioridade:** P1  
**Estado:** PROSPECT_VERIFIED — OUTREACH_DRAFT_READY — NOT_SENT

## Objetivo
Avançar a aquisição de um produtor real em Goiânia por meio de uma abordagem individual baseada em um evento público atualmente anunciado, sem interferir na venda da edição em andamento.

## Área
Aquisição de produtores, prospecção comercial e ativação do primeiro evento.

## Oportunidade confirmada
A página pública da Sympla para **Mosh Pit Fest** informa:
- Data: 21/11/2026, das 22h às 06h de 22/11.
- Local: Las Vegas - Casa de Show, Goiânia/GO.
- Proposta: encontro da cena Trap/underground, com DJ FLUP.
- Produtor exibido na página: **Joint Records Brasil**.
- Canal de contato disponibilizado: botão **“Fale com o produtor”** na página do evento.

Fonte primária: https://www.sympla.com.br/evento/mosh-pit-fest/3613539

A página confirma o evento e o nome do produtor. Não foi encontrada evidência suficiente nesta consulta para afirmar que se trata de uma edição recorrente, portanto a abordagem fala em “próxima produção”, sem pressupor uma próxima edição do mesmo festival.

## Hipótese
Uma abordagem que reconhece o evento anunciado e propõe uma demonstração para uma produção futura pode gerar uma conversa mais qualificada do que uma apresentação genérica da Cutinapp. A hipótese ainda não foi testada com este produtor.

## Trabalho realizado
- Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/README.md, o claim ativo genérico de AUX-03-W3, orchestration/STATE.md, WORKER_REGISTRY.md, assignment AUX-03/W3 e os worklogs/entregáveis mais recentes.
- Confirmei que o assignment W3 anterior está DONE e que o worker está em fallback para sua função-base de aquisição e conversão.
- Evitei repetir o playbook de Direct, a sequência pós-cadastro de 07/11 e as abordagens já preparadas para Raphaela Gentil e Taberna Music Pub.
- Consultei a configuração da marca Cutinapp no Metricool: a resposta atual contém apenas `gbpData` em `networksData`; Instagram não está listado como canal conectado.
- Identifiquei no evento um caminho de contato público pelo botão “Fale com o produtor”.
- Preparei uma única abordagem personalizada para a Joint Records Brasil.
- Não enviei mensagem, não abordei o produtor, não publiquei conteúdo e não alterei código.

## Entregável — mensagem de abordagem
**Canal:** botão “Fale com o produtor” na página pública do evento Sympla.  
**CTA:** responder **DEMO**.

> Olá, equipe Joint Records Brasil! Vi a divulgação do Mosh Pit Fest, marcado para 21 de novembro na Las Vegas, em Goiânia, com proposta voltada à cena Trap/underground.
>
> Não quero interferir na divulgação nem nas vendas desta edição. Falo pela Cutinapp e gostaria de apresentar a plataforma para uma próxima produção de vocês.
>
> Podemos fazer uma demonstração rápida do fluxo de criação da página pública do evento, configuração dos ingressos e compartilhamento do link, para vocês avaliarem se faz sentido utilizar a Cutinapp em uma próxima produção.
>
> Se tiver interesse, responda **DEMO** e combinamos um horário.

A mensagem não promete migração, redução de taxas, resultados de venda ou recursos que não tenham sido validados no ambiente publicado.

## Métrica principal
**Primeiro evento publicado em até sete dias após a demonstração aceita.**

Fórmula do piloto:
- Numerador: produtores qualificados que aceitaram a demonstração e publicaram efetivamente o primeiro evento em até sete dias.
- Denominador: produtores qualificados que aceitaram a demonstração no período.

Indicadores intermediários: resposta ao CTA DEMO, demonstração agendada, produção cadastrada e evento publicado.

Baseline: N/D. Nenhuma mensagem foi enviada e nenhuma conversão foi medida.

## Próxima ação
Conta principal: autorizar ou não o contato externo e confirmar o fluxo público atual de criação/publicação antes de encaminhar qualquer link de cadastro.

Após autorização:
1. Enviar a mensagem pelo canal público “Fale com o produtor”.
2. Registrar resposta e consentimento para continuidade.
3. Se houver interesse, agendar demonstração.
4. Acompanhar até produção criada e primeiro evento efetivamente publicado.

## Precisa da conta principal?
**SIM** — autorização para contato externo e validação do fluxo de cadastro/publicação em runtime.

## Estado final
PROSPECT_VERIFIED — OUTREACH_DRAFT_READY — NOT_SENT — NO_PRODUCT_CODE_CHANGE — NOT_MERGED — NOT_DEPLOYED — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED.
