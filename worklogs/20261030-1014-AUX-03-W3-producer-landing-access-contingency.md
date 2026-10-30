# AUX-03 / W3 — 2026-10-30 — Acesso à landing de produtores e contingência de aquisição

owner: AUX-03-W3
date: 2026-10-30 10:14 America/Sao_Paulo
priority: P1 (conversão); escalar como incidente operacional se reproduzido em rede de usuário
status: ACCESS_NOT_VERIFIED — CONTINGENCY_COPY_READY — NO_OUTREACH_SENT
area: aquisição de produtores / entrada pública `/for-producers`
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Objetivo
Impedir que tráfego de aquisição seja direcionado para uma landing cuja acessibilidade não pôde ser confirmada, sem inventar disponibilidade, eventos, vendas ou conversões.

## Coordenação e não duplicação
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/assignments/AUX-03/W3.md`, `claims/active/20261009-1600-AUX-03-W3.md`, `orchestration/STATE.md`, `plans/CUTINAPP_COLD_START_GROWTH.md`, worklog W3 de 29/10 e W1 de 30/10. PRs #724, #725 e #726 continuam OPEN, mergeable=true e merged=false na consulta de 30/10. Não alterar nem duplicar os PRs, não tocar código financeiro/Independence, não executar deploy. W1 já registrou falha 530 na home e campanha de indicações de participantes; este W3 restringe-se à conversão de produtores.

## Obstáculo único / oportunidade
A jornada anúncio/conteúdo/indicação → landing → cadastro pode ser interrompida já no primeiro clique se a página pública não estiver acessível. Antes de investir em novas mensagens com link, verificar o caminho servido no dispositivo real.

## Confirmado (evidência observada; não extrapolar)
- Consulta pública via navegador web em 30/10 à `https://cutinapp.petertecnet.com.br/`: erro HTTP 530 (Unknown Status Code).
- Consulta via navegador web à `https://cutinapp.petertecnet.com.br/for-producers`: página não acessível pela ferramenta.
- Tentativa HTTP alternativa em ambiente de execução: falha de resolução DNS (`Could not resolve host`) para ambos os caminhos.
- Esses resultados comprovam **falha de acesso nos ambientes de teste**, não indisponibilidade global para todos os visitantes; não houve teste em rede móvel real.
- PRs de crescimento #724, #725 e #726 permanecem abertos, sem merge; não anunciar correções como publicadas.
- W1 documentou observação 530 na home em 30/10: `worklogs/20261030-1011-AUX-03-W1-participant-event-nominations-gbp.md`.

## Hipótese
Se visitantes reais receberem a mesma falha, campanhas que direcionam ao site desperdiçam tráfego e impedem cadastro de produtores. Impacto real ainda NÃO MEDIDO.

## Trabalho realizado / entregável concreto
Preparado roteiro de contingência para abordagem humana individual, **sem links de cadastro enquanto a landing não for validada**, sem automação de mensagens, sem prometer publicação imediata.

**Mensagem inicial — contato comercial individual autorizado:**

> Olá, {nome}. Sou da equipe Cutinapp. Estamos conversando com produtores que organizam eventos reais e querem divulgar a próxima programação. Você tem algum evento em preparação? Se tiver interesse em conhecer o processo de cadastro da produção, responda **PRODUZIR** e seguimos por aqui. Não é necessário contratar uma assinatura obrigatória para começar; vendas de ingressos podem envolver taxas e requisitos de habilitação.

**Resposta para quem enviar PRODUZIR:**

> Obrigado, {nome}. Para orientar o cadastro, me diga apenas o tipo de evento e se você já tem nome, data e local definidos. Assim que confirmarmos o acesso à página oficial, encaminhamos o endereço correto. Não publique dados ou ingressos sem validar as informações com a produção responsável.

**Follow-up único, somente se permitido, após 72h:**

> Olá, {nome}. Se ainda quiser conhecer a Cutinapp para divulgar seu próximo evento, basta responder **PRODUZIR**. Se não for o momento, não envio outros lembretes.

**Checklist para reativar links:** teste em 4G/5G e Wi-Fi, abrir home e `/for-producers`, confirmar HTTP 200 e conteúdo renderizado, CTA leva a cadastro/login, retorno à criação de produção, checar mobile 320/360/390/430 e origem de aquisição. Não declarar RUNTIME_VERIFIED sem evidência real.

## Canal / CTA / métrica
- Canal: WhatsApp/Instagram Direct **individual e autorizado**; peças apenas preparadas, NÃO ENVIADAS.
- CTA contingencial: **Responder PRODUZIR**; sem URL até validação de acesso.
- Métrica principal: **produtores ativados** (primeira produção criada e primeiro evento publicado, com fonte atribuível) / contatos qualificados da campanha.
- Métricas intermediárias: respostas únicas PRODUZIR; cadastro iniciado/concluído; falhas de carregamento por origem.
- Baseline, contatos enviados, leads e conversões: NÃO MEDIDOS; não registrar zero como dado real.

## Recomendação / próxima ação
1. W00/conta principal: testar imediatamente acesso público em rede móvel real e Wi-Fi, registrar timestamp, URL, HTTP, screenshot, DNS/CDN/origin e versão servida. Se reproduzido, escalar ao responsável pela infraestrutura como bloqueio de aquisição; não lançar campanhas com URL até correção comprovada.
2. Após disponibilidade validada: revisar e integrar PRs #724/#725/#726 conforme CI, QA e ownership; medir cadastro → produção → primeiro evento.
3. Operação comercial, se houver autorização de contato: testar a mensagem contingencial com no máximo 10 contatos reais consentidos e registrar respostas/ativações, sem envio em massa.

## Evidências e responsável
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261030-1011-AUX-03-W1-participant-event-nominations-gbp.md
- owner: AUX-03-W3 (copy e handoff); W00/conta principal (teste real e escalonamento).
- NEXT_ACTION: confirmar ou refutar falha de acesso em navegador móvel real antes de qualquer link de aquisição.
- Conta principal necessária: SIM.
- Estado: ACCESS_NOT_VERIFIED — COPY_READY — WORKLOG_COMMITTED — NO_MESSAGES_SENT — NO_CONVERSIONS_VERIFIED.
