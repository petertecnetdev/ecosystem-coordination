# AUX-03 W3 — Piloto de aquisição para produtores com agenda recorrente

**Data:** 01/11/2026  
**Área:** aquisição e ativação de produtores  
**Objetivo:** abrir conversas qualificadas com casas e pubs cuja programação se repete, usando como proposta de valor a redução de retrabalho na organização de edições recorrentes.

## 1. Por que este piloto existe

O histórico AUX-03 já cobre:
- convite genérico a produtores;
- chamada temporal para eventos de novembro;
- qualificação por cidade, tipo e data;
- preparação das informações do primeiro evento;
- bio e checklist de divulgação.

Esta peça não repete esses materiais. Ela testa uma proposta específica: **agenda recorrente e reaproveitamento de edições**.

## 2. Confirmado

- A configuração da API em `config/subscriptions.php` define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e `plans=[]`.
- A versão atual de `main` em `src/pages/ProducerLandingPage.js` ainda anuncia trial de 30 dias, assinatura e CTA “Iniciar trial grátis”. A oferta está contraditória com a API. O PR #724 corrige essa mensagem, mas permanece aberto e sem merge.
- O código atual contém `ProductionAgendaManager` e `EventSeriesLauncher`, com fluxos de agenda semanal, criação de séries e duplicação de edição. Isso comprova presença no código de `main`, não valida disponibilidade no ambiente de produção.
- O site oficial do Luxury Club informa funcionamento recorrente em quarta, sexta e sábado e está com atualização de experiência em andamento. A página também mostra uma edição em 24/10/2026, data passada nesta execução; ela **não** é apresentada como evento futuro.
- A ficha pública consultada para La Fyesta Pub identifica o estabelecimento como bar com entretenimento em Goiânia. Nenhum próximo evento específico foi validado nesta execução.
- Metricool identifica a marca `cutinapp` (7119630), mas `networksData` retorna somente `gbpData`; não há integração publicadora do Instagram confirmada. A consulta de agendamentos de 01/11 a 08/11 retornou lista vazia.
- A home pública abriu no navegador de pesquisa apenas com o shell “Ative o JavaScript”; a rota `/for-producers` não pôde ser carregada pela ferramenta. Isso não comprova indisponibilidade global para visitantes reais.

## 3. Hipótese a testar

Casas com programação semanal ou mensal podem perceber mais valor em uma ferramenta que reduza o retrabalho de estruturar cada edição do que em uma mensagem genérica sobre “divulgar eventos”.

Ainda não há dados de resposta, cadastro ou ativação que comprovem essa hipótese.

## 4. Entregável — abordagem individual

### A. Luxury Club — primeira mensagem

> Olá, equipe Luxury Club. Vi que vocês trabalham com programação recorrente ao longo da semana.  
>   
> Estou entrando em contato pela Cutinapp porque estamos selecionando casas para um piloto de agenda recorrente: organizar uma edição-base e reaproveitar a estrutura nas próximas datas, reduzindo o retrabalho de preparar cada edição.  
>   
> Quem cuida da programação poderia conhecer esse fluxo? Se fizer sentido, responda **AGENDA** e seguimos por aqui.

**Nota de precisão:** não citar a edição de 24/10 como próxima data; ela já passou. Não afirmar que a Cutinapp já está operando a agenda do estabelecimento.

### B. La Fyesta Pub — primeira mensagem

> Olá, equipe La Fyesta Pub. Estamos conversando com pubs e casas de entretenimento de Goiânia que organizam eventos e programações ao longo do mês.  
>   
> A Cutinapp está apresentando um fluxo de agenda recorrente e reaproveitamento de edições para reduzir o trabalho de preparar cada nova data. Gostaríamos de entender como vocês organizam a programação e avaliar se um piloto faria sentido.  
>   
> Quem é a pessoa responsável pela agenda de eventos? Se puder encaminhar esta mensagem, agradeço. Para continuar, responda **AGENDA**.

**Nota de precisão:** não mencionar evento, artista, preço, lotação ou data da La Fyesta Pub sem validação com a produção responsável.

### C. Resposta quando o contato enviar AGENDA

> Obrigado! Para entender se o piloto serve para a rotina de vocês, me diga só:
> 1. A programação se repete semanalmente, quinzenalmente ou mensalmente?
> 2. Qual é a próxima data já confirmada?
> 3. Em qual cidade acontece?
> 4. A entrada será gratuita, paga ou terá os dois formatos?
>
> Não precisa enviar documentos nem dados pessoais por aqui.

### D. Próximo passo para lead qualificado

> Perfeito. Podemos fazer uma conversa rápida para entender a próxima edição real e mostrar o fluxo de criação da produção, configuração do evento e reaproveitamento das próximas datas. Antes de encaminhar cadastro ou link público, vamos confirmar que o acesso mobile está funcionando e que a oferta exibida está correta.

### E. Follow-up único após 72 horas

> Olá! Retomo uma única vez a conversa sobre agenda recorrente da Cutinapp. Se fizer sentido avaliar o piloto, responda **AGENDA**. Se não for prioridade agora, não envio novos lembretes.

## 5. Regras do piloto

1. Enviar apenas individualmente a um canal oficial verificado e a um contato comercial adequado.
2. Não enviar em massa, não insistir após recusa e não presumir autorização para publicar eventos.
3. Não encaminhar a landing de produtores enquanto PR #724 não for integrado e o fluxo mobile não for validado.
4. Não prometer isenção de taxas, trial, venda garantida, alcance, público ou resultado financeiro.
5. Só cadastrar/publicar evento após receber informações confirmadas e autorização explícita do responsável.
6. Não usar a edição de 24/10/2026 como evento futuro; não inventar programação para nenhum prospecto.

## 6. Canal, CTA e métrica

- **Canal:** WhatsApp comercial ou Instagram Direct oficial, contato individual.
- **CTA:** responder **AGENDA**.
- **Métrica principal:** leads qualificados que criam uma produção e publicam o primeiro evento em até 7 dias ÷ leads qualificados que responderam AGENDA.
- **Métricas intermediárias:** respostas AGENDA; contatos qualificados; conversas com responsável pela programação; produções criadas; eventos publicados.
- **Definição de lead qualificado:** responsável ou representante autorizado + cidade + frequência da programação + próxima data confirmada.
- **Baseline:** N/D. Nenhuma mensagem foi enviada nesta execução; não registrar zero como resultado de campanha.

## 7. Bloqueios e próxima ação

**Bloqueio P1:** a landing em `main` ainda contém trial/assinatura obrigatória, incompatíveis com a configuração da API. PR #724 permanece aberto.

**Próxima ação da conta principal:**
1. Revisar/integrar PR #724 após CI e QA mobile.
2. Confirmar acesso real a `/for-producers` em 4G/5G e Wi-Fi.
3. Verificar os perfis/canais oficiais e autorizar o contato comercial.
4. Executar o piloto individual com os dois prospectos e registrar cada etapa até primeiro evento publicado.

**Precisa da conta principal:** SIM — integração da correção comercial, validação do acesso e autorização/acesso aos canais de contato.

**Estado:** COPY_READY — PROSPECTS_RESEARCHED — NOT_SENT — NOT_PUBLISHED — NOT_DEPLOYED.
