# AUX-03 W3 — prospecção HYPE 62 Produções / piloto de próxima edição

**Data:** 2026-11-27 09:59 BRT  
**Objetivo:** qualificar um produtor com recorrência de eventos e preparar uma abordagem comercial específica para uma próxima edição, sem interferir na venda atualmente anunciada.

## Área
Aquisição B2B de produtores, prospecção, relacionamento comercial e conversão para primeiro evento publicado.

## Oportunidade

### Confirmado
- A página pública da Shotgun identifica **HYPE 62 Produções** como organizadora de **Treta**, anunciada para **12/12/2026, das 22h às 06h**, em local secreto no Setor Marista, Goiânia.
- A descrição da edição informa que a TRETA completa um ano e menciona a parceria entre TRETA Goiânia, BANGERZ e HYPE62.
- A página do organizador e eventos anteriores mostram outras produções associadas à HYPE 62, incluindo WKND 062 (19–21/11/2026), Garoto Equilibrivm (05/09/2026) e edições anteriores da TRETA.
- A página pública do evento atual informa que o lineup e outros detalhes ainda seriam divulgados. Não inferir capacidade, público presente, vendas ou receita a partir de interesse na plataforma.
- Um diretório empresarial consultado lista HYPE 62 PRODUÇÕES LTDA como ativa e apresenta e-mail e WhatsApp de contato. O registro informa atualização cadastral em 11/07/2026; os canais são **dados de diretório secundário**, não confirmação direta da empresa, e devem ser reconfirmados antes do uso.

### Hipótese
A recorrência de eventos e a construção de marcas/séries (TRETA e WKND 062) podem tornar a HYPE 62 um prospecto de maior valor potencial do que um produtor de evento isolado. Isso ainda não comprova interesse, necessidade de trocar de plataforma ou adequação operacional à Cutinapp.

## Trabalho realizado
1. Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md` e assignment AUX-03 W1/W2/W3.
2. Confirmei que o assignment anterior de W3 está DONE com fallback à função-base; W1 está BLOCKED e W2 AVAILABLE. Não havia override W00 READY/CLAIMED no assignment W3 consultado.
3. Consultei o entregável e worklog AUX-03 de 26/11 para não repetir o kit de compartilhamento de participantes.
4. Revalidei diretamente os PRs #724, #725, #726 e #727: todos continuam OPEN e não merged; #727 continua Draft. Revalidei a issue #643, que permanece aberta e descreve divergência entre o release no filesystem e o release servido pelo Nginx.
5. Pesquisei eventos atuais publicados e selecionei HYPE 62 pela recorrência observável de produções e pela edição TRETA anunciada para 12/12/2026.
6. Preparei uma abordagem pós-evento focada em calendário de 2027 e piloto de uma única próxima edição. Nenhum contato foi enviado.

## Entregável — abordagem comercial específica

**Assunto:** Conversa sobre a próxima agenda da HYPE 62

Olá, equipe HYPE 62!

Acompanhei algumas das produções de vocês em Goiânia, incluindo o WKND 062 e a edição de um ano da TRETA anunciada para 12 de dezembro.

Não quero interferir na divulgação ou na venda dessa edição. Meu contato é para conhecer como vocês estão planejando as próximas datas e entender se faria sentido avaliar uma próxima produção de 2027 como piloto na Cutinapp, plataforma de eventos da Peter Tecnet.

A ideia é começar por uma conversa breve sobre o formato dos eventos, divulgação, venda de ingressos e operação de entrada. Só depois dessa conversa, e com a compatibilidade do produto confirmada, faria sentido avaliar uma data-piloto.

Se houver abertura, podemos conversar por 15 minutos na semana de 14 de dezembro?

**CTA:** CONVERSAR SOBRE 2027.

### Qualificação para a conversa
1. Quais marcas/séries e datas estão previstas para o primeiro trimestre de 2027?
2. Como a equipe decide qual plataforma utilizar em cada produção?
3. Quais etapas da divulgação, venda e entrada mais exigem trabalho manual?
4. Há interesse em testar uma plataforma em apenas uma próxima edição, sem alterar eventos já em venda?
5. Quais requisitos operacionais e comerciais seriam indispensáveis para considerar o piloto?

### Guardrails comerciais
- Não sugerir migração da venda da TRETA de 12/12.
- Não prometer taxas, trial, repasses, integrações, recursos ou resultados ainda não validados.
- Não encaminhar link de cadastro enquanto o runtime público não tiver GO.
- Não usar os dados do diretório como canal oficial sem reconfirmação.
- Não enviar mensagem sem autorização da conta principal.

## Canal
E-mail empresarial ou WhatsApp comercial listado em diretório secundário, somente após reconfirmação. Alternativa: perfil público de HYPE 62 Produções na Shotgun para identificar o canal institucional apropriado.

**Referências públicas:**
- Evento TRETA: https://shotgun.live/pt-pt/events/treta
- Perfil do organizador: https://shotgun.live/pt-pt/venues/hype-62-producoes
- Evento WKND 062: https://shotgun.live/pt-br/events/wknd-062-main-party
- Registro empresarial: https://casadosdados.com.br/solucao/cnpj/hype-62-producoes-ltda-63668071000187

## CTA e métrica
**CTA primário:** CONVERSAR SOBRE 2027.

**Métrica principal:** primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada, aceite do piloto, confirmação de compatibilidade e liberação do runtime.

**Métrica operacional:** respostas positivas qualificadas / contatos autorizados efetivamente enviados.

**Baseline:** 0 contatos enviados nesta oportunidade; taxa de resposta N/D.

Não tratar interessados em página de evento como ingressos vendidos ou participantes confirmados.

## Evidências
- Shotgun — página TRETA: organizador HYPE 62 Produções, 12/12/2026, 22h–06h, Setor Marista, edição de um ano e parceria TRETA/BANGERZ/HYPE62.
- Shotgun — perfil HYPE 62: histórico de produções, incluindo WKND 062 e eventos TRETA.
- Shotgun — WKND 062: evento passado em 19–21/11/2026, organizado por HYPE 62.
- Casa dos Dados — registro empresarial: situação cadastral e canais listados; atualização indicada em 11/07/2026.
- GitHub Cutinapp: PRs #724–#727 OPEN; #727 Draft; issue #643 OPEN.
- Coordenação: CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/STATE.md, WORKER_REGISTRY.md e assignments AUX-03.

## Próxima ação
1. Conta principal autorizar ou negar o contato.
2. Reconfirmar o canal empresarial antes do envio.
3. Se autorizado, aguardar a edição de 12/12 e abordar entre 14 e 16/12/2026.
4. Fazer a conversa de qualificação e registrar objeções/requisitos.
5. Só oferecer piloto quando runtime, página pública, condições comerciais e fluxo de publicação estiverem validados.
6. Acompanhar até o primeiro evento efetivamente publicado.

## Precisa da conta principal
**SIM.** Autorização para contato, reconfirmação do canal e confirmação do caminho de apresentação comercial permitido enquanto o runtime público não recebeu GO.

## Estado
PROSPECT_QUALIFIED_FOR_REVIEW — OUTREACH_DRAFT_READY — CONTACT_NOT_SENT — RUNTIME_GO_NOT_VERIFIED — NOT_PUBLISHED — NOT_DEPLOYED.
