# AUX-03 — Gate de liberação do funil público de produtores
**Data:** 09/11/2026  
**Owner:** AUX-03-W3  
**Prioridade:** P1  
**Status:** GROWTH_GATE_DOCUMENTED — ACCOUNT_MAIN_ACTION_REQUIRED

## Objetivo
Remover o principal bloqueio verificável antes de direcionar novos produtores à Cutinapp: confirmar que a entrada pública e a landing de produtores abrem e conduzem ao cadastro/produção no ambiente realmente publicado.

## Área
Aquisição de produtores, landing pública, conversão e ativação.

## Oportunidade
Já existem materiais de prospecção, Stories, Reel, playbook de Direct e sequência pós-cadastro. Continuar produzindo novas peças sem validar o destino público aumenta o estoque de conteúdo, mas não demonstra aquisição. Esta execução não cria outra campanha; estabelece um gate objetivo para liberar o tráfego e aproveitar o pipeline comercial existente.

## Confirmado — evidências verificadas em 09/11/2026

### 1. Acesso público
- A abertura de `https://cutinapp.petertecnet.com.br/` pelo navegador de pesquisa retornou **HTTP 530**.
- A rota `/for-producers` não pôde ser carregada pela mesma ferramenta.
- A rota `/events` também não pôde ser carregada.
- Isso confirma a falha nas consultas realizadas; **não prova, isoladamente, indisponibilidade para todos os usuários ou redes**. É necessária validação em smartphone real, Wi-Fi e rede móvel.

### 2. Correções de conversão ainda não integradas
Consulta direta ao GitHub em 09/11:
- PR #724 — landing/oferta e CTA de produtor: **OPEN, NOT MERGED**.
- PR #725 — retorno de conta autenticada para criação de produção: **OPEN, NOT MERGED**.
- PR #726 — CTA de primeiro evento no onboarding: **OPEN, NOT MERGED**.
- PR #727 — metadados SEO da landing: **OPEN, DRAFT, NOT MERGED**; depende de #724 ou do mesmo release.

Não declarar que essas melhorias estão disponíveis no ambiente publicado. A existência de PR e commit não comprova build, deploy ou runtime.

### 3. Distribuição
- Metricool brand `cutinapp`, ID `7119630`, timezone `America/Sao_Paulo`.
- `networksData` retornou somente `gbpData`; não há `instagramData` nessa conexão.
- Agendamentos consultados de 09/11/2026 a 16/11/2026: lista vazia.
- Isso não comprova ausência de posts publicados diretamente no Instagram; comprova apenas que a integração consultada não apresenta Instagram conectado e não retornou agendamentos para o intervalo.

### 4. Coordenação
- `CURRENT_STATE.md` SHA `5a531c3469945a62f589a4a8d4f228c733144a3a`; último commit do arquivo em 30/10/2026 20:56 UTC. O documento está desatualizado em relação aos worklogs existentes até 08/11.
- `PRIORITIES.md` SHA `fd4d80e89b89753bb68c53e2bbd631803e8b2d68`.
- `BLOCKERS.md` SHA `3472cea057d2835ed7f151bae7f3ec404700f936`.
- Li o worklog W3 de 08/11 (Joint Records), W2 de 08/11 (agenda pública), W2 de 07/11 (páginas temporais vazias), W1 de 04/11 (distribuição bloqueada) e os ativos W3 anteriores.
- Claims ativos AUX-03: W2 SEO/public discovery e W3 aquisição genérica. Esta entrega é um gate operacional de crescimento; não altera código nem reivindica arquivos de produto.

## Hipótese
O maior obstáculo demonstrável no momento está antes da conversão: não há evidência suficiente de que o visitante consiga abrir a entrada pública e concluir o caminho até a criação da produção. A falha HTTP 530 observada e os PRs ainda não integrados justificam bloquear campanhas com link direto até a validação. O impacto sobre usuários reais e a taxa de abandono ainda não foram medidos.

## Trabalho realizado
1. Consultei os documentos de coordenação, claims, assignment W3 e entregas recentes para evitar duplicação.
2. Verifiquei diretamente os estados e dependências dos PRs #724–#727.
3. Verifiquei as configurações da marca e os agendamentos atuais do Metricool.
4. Testei a abertura pública da raiz, da landing de produtores e da rota de eventos pelo navegador de pesquisa.
5. Consolidei um gate de liberação e preservei os materiais de aquisição já preparados, sem criar outra peça redundante.

## Entregável — critérios GO/NO-GO

**NO-GO para campanhas com link de cadastro** até todos os itens abaixo serem confirmados pela conta principal:

1. Abrir raiz, `/for-producers` e uma página pública real em smartphone nas larguras 320/360/390/430px, por Wi-Fi e rede móvel.
2. Confirmar que a landing apresenta a oferta comercial correta, sem trial/assinatura obrigatória contraditórios.
3. Testar CTA de produtor: visitante novo → cadastro → retorno à criação de produção.
4. Testar conta existente: login → retorno à criação de produção, sem cair no dashboard e perder a intenção.
5. Testar produção criada → primeiro evento → revisão → assinatura do termo → publicação, distinguindo publicação de habilitação de recebimentos para ingressos pagos.
6. Confirmar que o link público do evento abre, apresenta dados reais e pode ser compartilhado no celular.

**Sequência de integração a revisar:** #724 e #727 no mesmo release (ou #727 após #724); #725 e #726 após CI e QA mobile próprios. A decisão de merge pertence à conta principal/revisor responsável. Este documento não autoriza merge ou deploy.

## Pipeline comercial preservado — não duplicar
- Raphaela Gentil: evento de 07/11 já passou; abordagem pós-evento existe, mas permanece NOT_SENT.
- Taberna Music Pub: GERAÇÃO 2K anunciado para 14/11; abordagem existente sugere contato após o evento, sem envio.
- Joint Records Brasil: Mosh Pit Fest anunciado para 21/11; abordagem existente com CTA DEMO, sem envio.
- La Fyesta Pub e Luxury Club: kit de agenda recorrente de 01/11 já existe; nenhum contato confirmado.

Nenhum prospecto foi contatado nesta execução. Não inferir autorização comercial.

## Canal
Landing pública `/for-producers` → cadastro/login → criação de produção → primeiro evento → página pública → compartilhamento.

## CTA
**VALIDAR ACESSO PÚBLICO** — a conta principal deve confirmar o gate GO/NO-GO e devolver evidência de abertura em smartphone/rede móvel antes de liberar tráfego.

## Métrica principal
**Produtores que publicam o primeiro evento em até 7 dias ÷ produtores únicos que iniciam o cadastro pela landing.**

Métrica de diagnóstico imediata: sessões qualificadas na landing que chegam à produção criada. Baseline: N/D; telemetria/ambiente publicado não foram consultados nesta execução.

## Evidências
- Landing pública consultada: https://cutinapp.petertecnet.com.br/for-producers
- Raiz consultada: https://cutinapp.petertecnet.com.br/
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Worklog W3 08/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261108-1047-AUX-03-W3-prospecto-joint-records-brasil.md
- Worklog W2 08/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261108-1027-AUX-03-W2-public-production-agenda-discovery.md
- Worklog W1 04/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261104-1031-AUX-03-W1-social-growth-go-live-blocked.md
- Metricool: brand 7119630; somente GBP em `networksData`; agendamentos 09–16/11 vazios.

## Próxima ação
Conta principal valida o acesso público em smartphone, Wi-Fi e rede móvel e decide a revisão/integração dos PRs de crescimento. Após o gate GO, retomar o pipeline já preparado e medir cadastro → produção → primeiro evento publicado.

## Precisa da conta principal?
**SIM** — acesso/validação do ambiente publicado e decisão de integração dos PRs; também é necessária autorização para qualquer contato comercial externo.

## Estado final
GROWTH_GATE_DOCUMENTED — PUBLIC_ACCESS_NOT_VERIFIED — PRS_NOT_MERGED — INSTAGRAM_NOT_CONNECTED_IN_METRICOOL — NO_NEW_CONTENT_DUPLICATED — NO_OUTREACH_SENT — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS — CONVERSION_NOT_MEASURED.
