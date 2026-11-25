# AUX-03 W3 — bloco de transparência comercial para produtores

**Data:** 2026-11-25 10:48 BRT  
**Objetivo:** reduzir incerteza comercial antes do cadastro de produtores, sem inventar preços, percentuais, trial ou condições não confirmadas.

## Área e oportunidade

Aquisição de produtores, copy da landing `/for-producers`, qualificação comercial e conversão.

### Confirmado

Fonte de configuração consultada diretamente em `petertecnetdev/api.petertecnet.com.br`, branch `main`, arquivo `config/subscriptions.php`, blob `380033cdb502c34896b907ae2209c91e31f7f14f`:

- Cutinapp: `subscription_enabled=false`.
- `monetization_model=transaction_fee`.
- `plans=[]`.
- O arquivo não informa percentual/valor da taxa, responsável pelo pagamento, tarifas adicionais ou prazo de repasse.

PRs de crescimento consultados em 25/11:
- [#724 — oferta da landing](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724): aberto; copy remove trial/assinatura obrigatória e usa CTA “Cadastrar minha produção”.
- [#725 — intenção de cadastro para conta autenticada](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725): aberto.
- [#726 — CTA de primeiro evento](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726): aberto.
- [#727 — metadados SEO da landing](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727): aberto; depende de #724 ou do mesmo release.
- Nenhum review registrado nos PRs #724–#727 nesta consulta.
- [Issue #643 — release público servido pelo Nginx](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643): permanece aberta.

Metricool:
- Marca `cutinapp`, ID `7119630`.
- `networksData` retornou apenas `gbpData`; Instagram não consta como rede conectada no retorno.
- Agenda consultada de 25/11 a 02/12/2026 retornou vazia.

### Hipótese

A ausência de clareza sobre como a taxa por transação funciona pode gerar objeção antes do cadastro. Não há entrevistas, analytics ou dados de conversão que comprovem que preço seja o maior gargalo. O gate público da issue #643 continua sendo um bloqueio mais fundamental para aquisição distribuída.

## Trabalho realizado

1. Consultada a coordenação: `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md`, assignment AUX-03 W3, claim e worklog mais recentes.
2. Confirmado que o assignment W3 anterior está DONE e permite retorno à função-base; W1 está BLOCKED e W2 AVAILABLE. Nenhuma atribuição W00 READY/CLAIMED para W3 foi encontrada no arquivo de assignment.
3. Validada a configuração comercial diretamente na API.
4. Reconfirmados os estados abertos dos PRs #724–#727 e ausência de reviews.
5. Preparado bloco de FAQ e resposta comercial, sem alterar código ou publicar copy.

## Entregável — copy proposta

### FAQ para a landing de produtores

**Existe mensalidade para começar?**

A Cutinapp não exige uma assinatura mensal obrigatória. O modelo de monetização é por transação. Antes de abrir as vendas, consulte as condições comerciais vigentes para o seu evento.

**Como funciona a taxa por transação?**

A Cutinapp utiliza um modelo de monetização por transação. O percentual e eventuais tarifas aplicáveis precisam ser confirmados nas condições comerciais vigentes para a sua operação. Não informe valores sem validação.

**Há um período de teste grátis?**

Não anunciar “30 dias grátis” ou qualquer trial até que exista configuração comercial e autorização explícita que comprovem essa oferta.

### Resposta para objeção comercial — WhatsApp/Direct

“Boa pergunta. A Cutinapp não exige uma assinatura mensal obrigatória; o modelo é por transação. Prefiro não te passar um percentual sem confirmar as condições atuais da sua operação. Antes de abrir as vendas, precisamos deixar claras as taxas e demais condições aplicáveis para que você decida com segurança.”

### CTA

- Em conversa comercial: **QUERO CONFIRMAR AS CONDIÇÕES DO MEU EVENTO**.
- Na landing, manter o CTA já previsto no PR #724: **CADASTRAR MINHA PRODUÇÃO**. Não criar rota ou destino novo nesta entrega.

### Condição para publicação

Antes de publicar a FAQ, a conta principal/W00 precisa confirmar e documentar:
1. percentual ou valor da taxa por transação;
2. quem paga a taxa (produtor, comprador ou combinação);
3. tarifas do meio de pagamento, se houver e se são separadas;
4. prazo e regras de repasse;
5. tratamento de cancelamentos/estornos que afete o custo do produtor.

Se algum item não estiver definido, a copy deve continuar sem número e não pode sugerir uma condição específica.

## Canal e métrica

**Canal:** FAQ da landing `/for-producers` e resposta a objeção em WhatsApp/Direct.

**CTA:** “Cadastrar minha produção” (landing) e “Quero confirmar as condições do meu evento” (conversa).

**Métrica principal:** produtores únicos originados na landing que publicam o primeiro evento em até 7 dias após criar a produção.

**Métrica intermediária proposta:** cliques únicos no CTA de cadastro após abrir a FAQ de taxas / aberturas únicas da FAQ. Eventos sugeridos, ainda não implementados: `producer_fee_faq_opened` e `producer_fee_conditions_cta_clicked`.

**Baseline:** N/D. Não há dados de uplift ou conversão comprovados.

## Evidências

- [Configuração comercial da API — config/subscriptions.php](https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php), blob `380033c`.
- [PR #724 — copy e CTA da landing](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724).
- [PR #727 — metadados SEO](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727).
- [PR #725 — retorno de conta autenticada](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725).
- [PR #726 — primeiro evento no onboarding](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726).
- [Issue #643 — gate de runtime público](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643).
- Metricool brand 7119630: somente GBP no retorno de redes; agenda 25/11–02/12 vazia.

## Próxima ação

W00/conta principal deve confirmar as condições comerciais exatas e decidir se incorpora a FAQ ao PR #724 antes de integrar #727 no mesmo release. Depois do GO público, validar mobile, consistência de copy/metadados e medir FAQ → CTA → cadastro → primeira publicação.

## Precisa da conta principal

**SIM.** É necessária validação das taxas e condições comerciais. Não enviar a resposta comercial nem publicar a FAQ antes dessa confirmação.

## Estado

COPY_DRAFT_READY — COMMERCIAL_FACTS_PARTIALLY_CONFIRMED — FEE_DETAILS_UNVERIFIED — PRS_OPEN — RUNTIME_GO_NOT_VERIFIED — NOT_PUBLISHED — NOT_DEPLOYED.
