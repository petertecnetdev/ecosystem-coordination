# AUX-03 — Sequência de ativação pós-cadastro: produção → primeiro evento publicado

**Data:** 07/11/2026  
**Owner:** AUX-03-W3  
**Prioridade:** P1  
**Status:** COPY_READY — NOT_CONFIGURED — NOT_SENT

## Objetivo
Aumentar a proporção de produtores que publicam o primeiro evento nos sete dias seguintes ao cadastro da produção, trabalhando o trecho pós-cadastro que ainda não estava coberto pelo playbook de prospecção e pelos Stories.

## Confirmado — fluxo existente no código
A leitura do código da branch do PR #726 confirmou os seguintes caminhos e condições:

- Sem evento inicial: criar evento em /event/create?productionId={{production_id}}.
- Com evento inicial: revisar em /event/edit/{{event_id}}.
- Para publicar, é necessário assinar o termo vigente: /producer/contracts?productionId={{production_id}}.
- Para vender ingressos pagos, configurar recebimentos: /producer/finance?production={{production_id}}&focus=activation.
- O onboarding distingue produção cadastrada, evento inicial, contrato, identidade/documento, prova de vida quando exigida e recebimentos.
- O CTA de primeiro evento já está preparado no PR #726, mas o PR ainda não foi integrado.

**Importante:** os caminhos acima foram confirmados no código do PR #726, não em runtime de produção. A sequência não afirma que os links já estejam publicados/ativos na versão servida.

## Oportunidade / obstáculo escolhido
Depois que a produção é cadastrada, o produtor ainda precisa transformar o cadastro em evento. O fluxo apresenta requisitos diferentes para preparar, publicar e vender ingressos pagos. Uma mensagem genérica sobre “concluir o cadastro” pode confundir essas etapas.

**Hipótese:** lembretes acionados pelo estado real do onboarding, com um único próximo passo por mensagem, podem aumentar a publicação do primeiro evento e reduzir a desistência.

## Entregável — sequência pronta para configurar

### Regra de segurança da sequência
- Enviar somente para produtores com base legal/consentimento de contato aplicável.
- Respeitar descadastro e preferência de canal.
- Reavaliar o estado antes de cada envio.
- Cancelar mensagens futuras assim que o primeiro evento for publicado.
- Não solicitar dados pessoais, documentos, selfie ou chave Pix por WhatsApp/e-mail. Direcionar o produtor para a área autenticada.
- Não enviar a etapa de recebimentos a quem não pretende vender ingressos pagos.

### Mensagem 1 — 15 minutos após produção criada, se ainda não houver evento inicial
**Assunto:** Sua produção está cadastrada. Vamos criar o primeiro evento?

Olá, {{first_name}}.

Sua produção já está cadastrada na Cutinapp. O próximo passo é preparar o primeiro evento.

Você pode começar pelas informações principais e revisar a página antes de avançar para a publicação.

**CTA: Criar primeiro evento**  
Destino: https://cutinapp.petertecnet.com.br/event/create?productionId={{production_id}}

Se você já começou, continue de onde parou na sua conta.

### Mensagem 2 — após 24 horas, somente se continuar sem evento inicial
**Assunto:** Vamos tirar seu primeiro evento do papel?

Para começar, deixe à mão o nome do evento, data, horário, local ou formato, descrição e imagem autorizada. Se houver ingressos pagos, organize também tipos, quantidades e preços.

Não precisa resolver todas as etapas financeiras para começar a preparar o evento. A publicação exige a assinatura do termo vigente; a venda de ingressos pagos exige a configuração dos recebimentos.

**CTA: Continuar criando evento**  
Destino: https://cutinapp.petertecnet.com.br/event/create?productionId={{production_id}}

### Mensagem 3 — imediatamente após detectar evento inicial em rascunho e termo pendente
**Assunto:** Seu evento está preparado. Falta o termo para publicar.

Olá, {{first_name}}.

O primeiro evento já foi iniciado. Para avançar à publicação, leia e assine pessoalmente o termo vigente da Cutinapp.

**CTA: Ler e assinar termo**  
Destino: https://cutinapp.petertecnet.com.br/producer/contracts?productionId={{production_id}}

A assinatura deve ser feita pelo próprio responsável, dentro da plataforma.

### Mensagem 4 — somente quando houver intenção de vender ingressos pagos e recebimentos pendentes
**Assunto:** Prepare os recebimentos para vender ingressos pagos

Olá, {{first_name}}.

Se este evento terá ingressos pagos, conclua a configuração de recebimentos na área autenticada da Cutinapp. A validação pode incluir dados de identidade, documento, prova de vida quando exigida e chave Pix.

**CTA: Configurar recebimentos**  
Destino: https://cutinapp.petertecnet.com.br/producer/finance?production={{production_id}}&focus=activation

Se o evento não terá ingressos pagos, esta etapa não deve ser enviada como bloqueio para preparar a publicação.

### Mensagem 5 — no sétimo dia, somente se o primeiro evento ainda não estiver publicado
**Assunto:** Podemos ajudar a publicar seu primeiro evento?

Olá, {{first_name}}.

Queremos ajudar você a concluir a primeira publicação. Responda **AJUDA** e informe em qual etapa parou: criação do evento, termo ou recebimentos.

Nossa equipe poderá orientar o próximo passo. Não envie documentos ou dados financeiros nesta conversa.

**CTA:** Responder AJUDA.

## Regras de segmentação e parada
| Estado verificado | Próxima comunicação | Não enviar quando |
|---|---|---|
| Produção criada, sem evento inicial | Mensagem 1 | Já existe evento inicial ou primeiro evento publicado |
| Após 24h, ainda sem evento inicial | Mensagem 2 | Evento inicial criado, descadastro ou contato sem consentimento |
| Evento em rascunho + termo pendente | Mensagem 3 | Termo já assinado ou evento já publicado |
| Ingressos pagos pretendidos + recebimentos pendentes | Mensagem 4 | Evento gratuito/sem intenção de venda paga ou recebimentos prontos |
| 7 dias sem primeiro evento publicado | Mensagem 5 | Evento publicado, produtor respondeu, descadastro ou suporte já aberto |

A automação deve priorizar uma mensagem por estado, não disparar as cinco mensagens em sequência fixa. Se o produtor avançar, pular para a próxima etapa aplicável. Se publicar, encerrar a sequência.

## Canal
E-mail transacional/marketing com consentimento aplicável e WhatsApp apenas para contatos que aceitaram receber mensagens. Não configurado nem enviado nesta execução.

## CTA
Principal: **Criar primeiro evento**.  
CTAs condicionais: **Ler e assinar termo**, **Configurar recebimentos**, **Responder AJUDA**.

## Métrica principal
**Taxa de primeiro evento publicado em 7 dias** = produtores com primeiro evento efetivamente publicado até 7 dias após a criação da produção ÷ produtores com produção criada no período.

Não contar clique, rascunho, evento apenas criado ou cadastro como publicação.

## Métricas secundárias
- Produção criada → evento inicial criado.
- Evento em rascunho → termo assinado.
- Evento com ingresso pago → recebimentos prontos.
- Evento criado → primeiro evento publicado.
- Tempo mediano entre produção criada e primeiro evento publicado.
- Descadastros/reclamações por mensagem enviada.

Baseline: N/D. Não há dados de envio, clique ou conversão nesta execução.

## Evidências
- PR #726 — CTA do primeiro evento no onboarding: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- Arquivo no HEAD do PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/45ad350c45b8dd4d34a0634c792c8cedbc803b21/src/pages/production/ProducerOnboardingPage.js
- PR #725 — redirecionamento de cadastro para produtores autenticados: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #724 — oferta real da landing de produtores: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #727 — metadados SEO da landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727

## Hipótese
Mensagens acionadas por estado e com um próximo passo único reduzirão a confusão entre criar evento, assinar termo e habilitar recebimentos. O impacto só poderá ser confirmado após configurar e medir a sequência.

## Próxima ação
Conta principal/owner de CRM e integrações: validar os links no runtime, confirmar consentimento e provedor de envio, mapear os estados reais do onboarding para os gatilhos, implementar a sequência com idempotência e supressão após publicação/descadastro e fornecer relatório de coorte de sete dias.

## Precisa da conta principal?
**SIM** — aprovação da comunicação, validação dos links no runtime e integração autorizada com o canal de envio/telemetria.

## Estado final
COPY_READY — STATE_RULES_DEFINED — WORKLOG_PENDING_COMMIT — NOT_CONFIGURED — NOT_SENT — NOT_DEPLOYED.
