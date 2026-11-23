# AUX-03 — Sequência de ativação: produção criada → primeiro evento publicado

**Data:** 23/11/2026 10:39 BRT  
**Objetivo:** reduzir o abandono entre o cadastro/criação da produção e a publicação do primeiro evento.  
**Área:** ativação de produtores, onboarding, lifecycle e conversão.  
**Estado:** COPY_READY — TRIGGER_SPEC_READY — NOT_IMPLEMENTED — NOT_SENT.

## 1. Confirmado

- A assignment AUX-03 W3 para landing foi concluída em 24/10 e retorna à função-base de aquisição/conversão.
- PR #724 permanece aberto, com CTA "Cadastrar minha produção", preservação de origem de aquisição e referência à telemetria producer_production_created; o fluxo proposto segue cadastro → produção → evento.
- PR #725 permanece aberto e trata da preservação da intenção de produtor para contas já autenticadas.
- PR #726 permanece aberto e antecipa o CTA "Criar primeiro evento" / "Revisar primeiro evento" acima do checklist.
- O PR #726 identifica os caminhos:
  - criação: /event/create?productionId=<id>;
  - edição: /event/edit/<id>;
  - termo: /producer/contracts?productionId=<id>.
- O PR #726 descreve a regra de publicação: termo vigente necessário para publicar; para vender ingressos pagos, configurar também os recebimentos.
- PR #727 está aberto e em Draft; depende de #724 ou do mesmo release para manter metadados e copy visível coerentes.
- Issue #643 continua aberta. O runtime público não recebeu GO verificável nesta execução.
- O comentário W2 de 23/11 sobre o snippet SEO e o artigo W2 de 22/11 sobre escolha de plataforma foram consultados. Esta entrega não repete SEO, artigo evergreen ou pauta social.

## 2. Hipótese

Parte dos produtores pode criar a produção e interromper o fluxo antes de criar o evento, ou iniciar um evento e não concluir as condições de publicação. Uma sequência curta e condicionada ao estado real pode recuperar parte desses produtores sem depender de anúncios ou de uma demonstração pública.

Não há dados de volume, abandono, entrega de mensagens ou conversão que comprovem o tamanho desse segmento. A sequência é uma hipótese a testar.

## 3. Recomendação: sequência de até três contatos

### Regra geral

- Iniciar somente após a criação de uma produção e consentimento/base de contato aplicável.
- Máximo de três mensagens em sete dias por produtor/produção.
- Reavaliar o estado antes de cada envio; não usar apenas um timer fixo.
- Interromper imediatamente após primeiro evento publicado, descadastro, revogação de consentimento ou endereço inválido.
- Preferir e-mail. WhatsApp somente quando houver opt-in válido; não reutilizar telefone de reserva ou contato público de terceiros como autorização de marketing.
- Não enviar enquanto o runtime/rotas de destino não forem validados em mobile e após login.

### D+1 — produção criada, ainda sem evento

**Condição:** produção criada; initial_event.id ausente; nenhum evento publicado.

**Canal:** e-mail.

**Assunto:** Sua produção está criada. Vamos preparar o primeiro evento?

**Mensagem:**

Olá, {{first_name}}.

Sua produção já está cadastrada na Cutinapp. O próximo passo é criar o primeiro evento.

Acesse sua conta, abra sua produção e selecione **Criar primeiro evento**. Você pode começar a preparar o evento e avançar pelas etapas necessárias para publicá-lo.

**CTA:** Criar meu primeiro evento.

**Destino autenticado proposto:** /event/create?productionId={{production_id}}.

### D+2 — evento iniciado, termo ainda pendente

**Condição:** existe initial_event.id; termo vigente ainda não está aceito; evento não publicado.

**Canal:** e-mail.

**Assunto:** Falta concluir uma etapa para publicar seu evento

**Mensagem:**

Olá, {{first_name}}.

Seu primeiro evento já foi iniciado. Para publicá-lo na Cutinapp, é necessário concluir a assinatura do termo vigente.

Acesse a etapa de contrato, revise as condições e conclua a assinatura quando estiver de acordo.

Se o evento tiver ingressos pagos, lembre-se de configurar também os recebimentos antes de abrir as vendas.

**CTA:** Assinar termo para publicar.

**Destino autenticado proposto:** /producer/contracts?productionId={{production_id}}.

### D+4 — termo aceito, evento ainda não publicado

**Condição:** existe initial_event.id; termo aceito; evento não publicado.

**Canal:** e-mail. WhatsApp pode substituir este contato somente com opt-in válido.

**Assunto:** Revise seu primeiro evento e avance para a publicação

**Mensagem:**

Olá, {{first_name}}.

Seu primeiro evento continua em preparação. Abra a edição, confira as informações e conclua as etapas pendentes para avançar à publicação.

Se a produção for vender ingressos pagos, confira também se os recebimentos estão configurados.

**CTA:** Revisar meu primeiro evento.

**Destino autenticado proposto:** /event/edit/{{event_id}}.

### Alternativa WhatsApp — somente com opt-in

Olá, {{first_name}}. Sua produção já está na Cutinapp. Você conseguiu avançar com o primeiro evento? Se ficou alguma etapa pendente, responda **EVENTO**, **TERMO** ou **RECEBIMENTOS** para identificarmos o próximo passo.

Não enviar esta alternativa se já houve contato recente por e-mail ou se o produtor não autorizou WhatsApp.

## 4. Lógica de supressão e segurança

- Evento publicado: suprimir todos os próximos contatos.
- Produção excluída ou desativada: suprimir.
- Termo já aceito: não enviar D+2.
- Evento ainda inexistente: não enviar D+4.
- Ingressos gratuitos ou sem venda paga: não inferir que configuração de recebimentos seja necessária.
- Falha de login/deep link: não enviar CTA até corrigir e validar o retorno ao destino.
- Um único fluxo ativo por produtor/produção; evitar duplicidade entre e-mail e WhatsApp.
- Não incluir dados pessoais, valores de venda ou dados financeiros na mensagem.

## 5. Métrica

**Métrica principal:** percentual de produtores da coorte de primeira produção criada que publicam seu primeiro evento em até sete dias.

Numerador: produtores com primeiro evento publicado em até 7 dias.  
Denominador: produtores únicos com primeira produção criada na coorte.

Métricas intermediárias:
- evento criado em até 48 horas;
- clique no CTA por mensagem;
- termo aceito após D+2, quando aplicável;
- evento publicado após D+4;
- descadastro, bounce e reclamação;
- tempo mediano entre produção criada e primeiro evento publicado.

**Baseline:** N/D. Não foi possível consultar eventos de analytics ou dados de produtores nesta execução.

### Instrumentação necessária — proposta, não confirmada

- producer_activation_nudge_sent
- producer_activation_nudge_clicked
- producer_first_event_created
- producer_first_event_published

A referência producer_production_created aparece no PR #724 como evento cuja origem deve ser validada; a captura real e disponibilidade para automação não foram comprovadas. Não criar uma trilha paralela de atribuição: coordenar com issue #637, já claimada para persistência de aquisição.

## 6. Evidências e dependências

- PR #724 — landing, CTA e origem de aquisição: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725 — intenção de produtor para contas autenticadas: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726 — primeiro evento, termo e rotas: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727 — metadados SEO, Draft e dependência de #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Issue #643 — release público/Nginx sem GO: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Issue #637 — atribuição orgânica já claimada: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/637
- Revisão W2 do snippet em 23/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261123-1011-AUX-03-seo-snippet-landing-produtores.md
- Artigo W2 de seleção de plataforma, consultado para evitar duplicação: https://github.com/petertecnetdev/ecosystem-coordination/commit/39ba43c7543ccadb6659423ba6c69508fe2eb74e

## 7. Limites desta entrega

- Copy e especificação de gatilhos preparadas.
- Não há confirmação de provedor de e-mail/CRM, consentimento, eventos de analytics ou scheduler disponíveis para esta jornada.
- Não foram criados fluxos de automação nem disparados contatos.
- Rotas precisam ser testadas com sessão autenticada e após login.
- Não houve alteração de código, PR, merge, build, deploy ou VPS.

## 8. Próxima ação

1. W00/conta principal confirmar provedor e fonte de consentimento para e-mail/WhatsApp.
2. Validar deep links autenticados nas rotas de criação, contrato e edição.
3. Confirmar captura dos eventos de produção criada, evento criado e evento publicado.
4. Se não houver instrumentação de publicação, encaminhar requisito ao owner do produto sem duplicar issue #637.
5. Pilotar com uma coorte pequena e comparar publicação em sete dias; não declarar uplift sem baseline/controle.

## 9. Precisa da conta principal

**SIM** — aprovação do canal e consentimento, validação das rotas/runtime, escolha do provedor e autorização para eventual envio.

COPY_READY — TRIGGER_SPEC_READY — METRICS_DEFINED — INSTRUMENTATION_UNVERIFIED — NOT_IMPLEMENTED — NOT_SENT — NOT_DEPLOYED
