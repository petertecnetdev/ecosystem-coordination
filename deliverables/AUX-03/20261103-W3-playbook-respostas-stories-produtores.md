# AUX-03 W3 — Playbook de respostas aos Stories de pesquisa com produtores

**Data:** 03/11/2026  
**Objetivo:** converter respostas voluntárias aos Stories W1 de pesquisa em conversas qualificadas e próximos passos de ativação, sem disparo frio ou promessa de recurso ainda não liberado.  
**Área:** aquisição de produtores, Instagram Direct, qualificação e ativação.  
**Prioridade:** P1 para conversão da resposta em lead; execução operacional condicionada à publicação dos Stories.

## 1. Contexto confirmado

- O material W1 de 03/11 contém três Stories: identificação de produtores, enquete entre “Atrair público” e “Vender ingressos”, e caixa aberta sobre o principal obstáculo. O material está ASSET_READY — NOT_SCHEDULED — NOT_PUBLISHED no worklog W1.
- Metricool brand cutinapp (ID 7119630) retornou apenas gbpData, sem instagramData; a consulta de agendamentos 03/11–10/11 retornou vazia. Isso não prova ausência de publicação orgânica feita diretamente no Instagram.
- A configuração api.petertecnet.com.br/config/subscriptions.php em main define cutinapp.subscription_enabled=false, monetization_model=transaction_fee e plans=[]. Não há percentual de taxa nesse bloco; não citar taxa zero nem percentual por DM.
- PR #724 (copy visível da landing) está aberto e não integrado; PR #727 (metadados SEO) está em draft e depende do #724; PR #726 (CTA de primeiro evento no onboarding) está aberto e não integrado. Portanto, não comunicar que essas alterações já estão disponíveis na experiência publicada.
- A página de onboarding em main ainda não contém o CTA prioritário do PR #726. A nova experiência existe na branch do PR, não foi confirmada em produção.
- A busca pública realizada nesta execução não encontrou página de evento Cutinapp que pudesse ser confirmada como evento real publicado. Isso não comprova ausência de eventos no sistema; este playbook não depende de citar eventos específicos.

## 2. Oportunidade e hipótese

**Oportunidade:** W1 prepara a pergunta e gera a resposta; faltava um roteiro operacional específico para responder de forma diferente conforme o produtor escolhe atração de público, venda de ingressos ou descreve outro bloqueio.

**Hipótese:** uma resposta contextualizada, seguida de uma pergunta curta sobre a próxima produção, aumenta a proporção de respostas que viram leads qualificados. Ainda não há respostas ou conversões medidas.

## 3. Playbook de Direct

### A. Story 1 — “Sim, produzo”
> Que bom encontrar quem está fazendo os eventos acontecerem. Você já tem uma próxima data confirmada ou ainda está organizando a agenda?

Se houver data:
> Ótimo. Qual é o tipo de evento e em qual cidade será? Com isso consigo orientar o próximo passo para preparar a divulgação e a página do evento na Cutinapp.

Se ainda estiver planejando:
> Sem problema. Quando tiver uma data ou uma edição em preparação, podemos retomar e mapear o caminho de cadastro. Não precisa publicar nada antes de revisar as informações.

### B. Story 1 — “Estou começando”
> Bem-vindo ao mercado de eventos. Você está planejando qual tipo de produção e em qual cidade?

Após a resposta:
> Posso orientar a sequência de preparação: dados da produção, informações do evento, revisão e publicação autorizada. O primeiro passo é entender o que você já tem definido.

### C. Story 2 — “Atrair público”
> Entendi. Hoje, por onde as pessoas descobrem seus eventos: Instagram, WhatsApp, indicação ou outro canal?

Após a resposta:
> Para a próxima edição, posso ajudar a organizar uma mensagem de divulgação com as informações essenciais e um CTA claro. Você já tem data e página de evento definidas?

Não prometer alcance, venda, viralização ou distribuição automática.

### D. Story 2 — “Vender ingressos”
> Qual parte mais dificulta a venda hoje: apresentar as opções de ingresso, compartilhar o link, acompanhar os pedidos ou organizar a entrada?

Após a resposta:
> Obrigado por explicar. Vou considerar esse ponto antes de orientar o próximo passo. Qual é a próxima edição que você pretende colocar no ar?

Não prometer taxa, prazo de repasse, aprovação financeira ou método de pagamento sem conferir as condições vigentes.

### E. Story 3 — resposta aberta
> Obrigado por contar. Para entender se conseguimos orientar: esse obstáculo já está afetando uma próxima edição com data definida ou ainda é uma dificuldade geral da sua operação?

A resposta determina se o contato é oportunidade ativa ou relacionamento para acompanhar depois.

## 4. Convite de ativação

Usar somente depois de entender a necessidade e confirmar que a pessoa quer avançar:

> Se fizer sentido, podemos orientar você na preparação do primeiro evento na Cutinapp: organizar as informações, revisar a apresentação e indicar o caminho disponível para publicação. Você revisa tudo e decide quando autorizar a publicação.
>
> Se quiser avançar, responda **PREPARAR**.

**Importante:** este é um convite para orientação assistida, não uma promessa de que a equipe criará ou publicará o evento em nome do produtor. Qualquer operação em nome do produtor exige autorização explícita e validação das informações.

## 5. Objeções

**“Tem mensalidade?”**
> A configuração comercial atual consultada indica que a Cutinapp não exige assinatura obrigatória e trabalha com cobrança por transação. As taxas e condições aplicáveis precisam ser conferidas nos termos e na etapa comercial vigente; não vou informar um percentual sem confirmação.

**“Preciso publicar agora?”**
> Não. Primeiro organizamos as informações e você revisa. A publicação só deve ocorrer depois da sua confirmação e autorização.

**“Vocês garantem vendas ou público?”**
> Não prometemos quantidade de público ou vendas. Podemos orientar a apresentação e a divulgação do evento; os resultados dependem de vários fatores e precisam ser medidos.

**“Posso mandar meus documentos por aqui?”**
> Não envie documentos, selfies, dados bancários, chave Pix ou informações sensíveis pelo Direct. Use apenas os fluxos oficiais e seguros da plataforma quando forem necessários.

## 6. Qualificação mínima e estados do lead

Registrar somente informações comerciais necessárias:
- source: ig_story_pesquisa_produtores_20261103
- profile: produtor / iniciante / outro
- challenge: atração / venda / operação / outro
- event_status: data confirmada / planejando / sem evento definido
- city: cidade informada voluntariamente
- next_step: orientar / aguardar / não interessado

Estados sugeridos: RESPONDEU → QUALIFICADO → INTERESSADO → PREPARAÇÃO → PRODUÇÃO_CRIADA → EVENTO_PUBLICADO → PRIMEIRA_VENDA.

Não registrar dados sensíveis em planilha ou Direct. Não marcar como produtor ativado antes da publicação real do primeiro evento.

## 7. Cadência e limites

- Responder a quem interagir voluntariamente; não transformar visualização ou voto em autorização para disparo em massa.
- Fazer no máximo um follow-up, após 48 horas, somente se a pessoa iniciou conversa e demonstrou interesse.
- Encerrar o acompanhamento se a pessoa não responder ou pedir para não receber mensagens.
- Não encaminhar para landing/onboarding como se as alterações pendentes dos PRs #724/#726 já estivessem publicadas. A conta principal deve confirmar o caminho público e a experiência disponível antes de fornecer link.

## 8. CTA e métricas

- **CTA:** PREPARAR — pedir orientação para preparar o primeiro evento.
- **Métrica principal:** produtores que publicam o primeiro evento em até 7 dias ÷ produtores qualificados que responderam aos Stories.
- **Métrica intermediária:** leads qualificados ÷ respostas voluntárias aos Stories.
- **Métricas secundárias:** conversas iniciadas, produtores com data/cidade definidas, produções criadas e tempo entre primeira resposta e publicação.
- **Janela de leitura:** 7 dias após a resposta inicial.
- **Baseline:** N/D; Stories ainda não publicados e respostas não medidas.

## 9. Próxima ação

1. Conta principal publica os três Stories W1 e insere os stickers nativos.
2. AUX-03 responde às interações voluntárias com o roteiro correspondente, se houver acesso autorizado ao Direct.
3. Conta principal confirma o caminho de cadastro/publicação disponível; não usar CTAs dos PRs ainda não integrados como se estivessem ativos.
4. Registrar a sequência resposta → lead qualificado → produção criada → evento publicado.

**Precisa da conta principal:** SIM — publicar os Stories, conceder/confirmar acesso autorizado ao Instagram Direct e validar o caminho de cadastro/publicação atualmente disponível.

**Estado deste entregável:** PLAYBOOK_READY — NOT_PUBLISHED — NO_DM_SENT — NO_CONVERSION_MEASURED — NO_PRODUCT_CHANGE — NO_DEPLOY.
