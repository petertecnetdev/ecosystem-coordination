# AUX-03 W3 — Revalidação da fila: Undergoth como próximo contato pós-evento

**Data:** 20/11/2026 10:37 BRT  
**Objetivo:** atualizar a prioridade de contato sem ampliar a fila nem repetir a mensagem comercial já preparada.

## Objetivo e área
Aquisição de produtores, relacionamento B2B e conversão para primeiro evento publicado na Cutinapp.

## Oportunidade
A fila de 18/11 tinha Taberna Music Pub como primeiro piloto, com janela sugerida de 18–19/11. O worklog de 19/11 confirma que a janela terminou sem autorização e sem envio. Entre os eventos da fila marcados para 21/11, a Undergoth é escolhida para o próximo contato pós-evento por estar realizando o 10º Encontro Gótico e por sua página pública registrar 99 pessoas interessadas.

**Evento confirmado:** Undergoth Nosferatu Fest — 10º Encontro Gótico, sábado, 21/11/2026, das 20h às 03h30, De Leon Music Pub, Rua 86, 605, Setor Sul, Goiânia. Organizador exibido: Undergoth. A página mostra 99 interessados. Esse número representa interesse na plataforma, não ingressos vendidos nem presença confirmada.

Fonte: https://shotgun.live/pt-br/events/undergoth

## Confirmado
- A mensagem para Taberna Music Pub foi preparada, mas não enviada; a janela recomendada 18–19/11 expirou sem autorização.
- A Undergoth já possui entregável de prospecção e mensagem inicial registrados em 16/11. Esta execução não cria uma nova mensagem nem duplica o prospecto.
- A página atual da Shotgun identifica a Undergoth como organizadora do evento de 21/11 e mostra 99 interessados.
- A página descreve o evento como 10º Encontro Gótico, com início às 20h de 21/11 e término às 03h30.
- A issue Cutinapp #643 continua OPEN. A consulta desta execução à raiz pública retornou HTTP 530; /for-producers e /events não puderam ser abertas por esta ferramenta. Isso não prova indisponibilidade para todos os visitantes.
- PRs #724, #725, #726 e #727 continuam OPEN; #727 está em Draft. Não há evidência de integração ou release público dessas alterações.
- Metricool brand Cutinapp (7119630) retorna somente gbpData, sem instagramData. A agenda de 20–27/11/2026 está vazia.
- Nenhuma mensagem comercial foi enviada nesta execução.

## Hipótese
A recorrência de dez edições e o sinal público de interesse podem justificar priorizar a Undergoth entre os prospectos com evento em 21/11. Não indicam, por si só, intenção de migrar, insatisfação com fornecedores ou volume de vendas.

## Recomendação
- Marcar Taberna como **JANELA EXPIRADA — REVALIDAR TIMING**, sem follow-up automático.
- Manter Joint Records e Raiza na fila de 23–24/11, conforme o registro de 18/11.
- Elevar Undergoth para **PRIMEIRO CONTATO PÓS-EVENTO SUGERIDO — 23/11**, por e-mail público ou Instagram Direct, após autorização expressa.
- Não usar o WhatsApp de venda/reservas como canal B2B inicial.
- Não encaminhar cadastro nem prometer demonstração funcional enquanto o runtime não receber GO.

## Trabalho realizado
1. Consultei CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/STATE.md, WORKER_REGISTRY.md e assignments AUX-03 W1/W2/W3.
2. Li o worklog, claim e entregável de 19/11 e a fila de 18/11.
3. Confirmei que W3 está em função-base de Producer Acquisition & Conversion; a atribuição específica de landing está DONE. W1 segue BLOCKED por mídia e W2 está AVAILABLE em SEO/blog.
4. Revalidei o evento da Undergoth na Shotgun em 20/11.
5. Revalidei issue #643 e PRs #724–#727 diretamente no repositório Cutinapp.
6. Revalidei a marca e a agenda Metricool.
7. Atualizei a prioridade operacional sem adicionar novo prospecto e sem duplicar a copy de 16/11.

## Entregável existente reutilizado
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261116-1017-AUX-03-prospecto-undergoth-10-encontro-gotico.md

Mensagem já preparada: abordagem pós-evento com CTA **PRÓXIMA EDIÇÃO**. Reutilizar o texto existente; não criar cadência paralela.

## Canal e CTA
- Canal: e-mail público undergothgynoficial@gmail.com; Instagram @undergothgynofc como alternativa.
- Momento sugerido: 23/11/2026, após o evento de 21/11 e mediante autorização.
- CTA para o produtor: **PRÓXIMA EDIÇÃO** — conversa breve sobre o planejamento da próxima produção.
- CTA interno para W00/conta principal: **AUTORIZAR PILOTO — UNDERGOTH**.

## Métrica
- **Métrica principal de negócio:** primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada e aceita.
- **Métrica operacional:** respostas positivas ÷ contatos autorizados efetivamente enviados.
- **Baseline:** zero contatos enviados nesta fila; conversões N/D.
- Não contabilizar os 99 interessados da Shotgun como leads, ingressos ou vendas.

## Evidências
- Evento atual: https://shotgun.live/pt-br/events/undergoth
- Prospecto e mensagem já preparados: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261116-1017-AUX-03-prospecto-undergoth-10-encontro-gotico.md
- Fila anterior: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261118-1040-AUX-03-fila-contatos-produtores-pos-evento.md
- Worklog de conversa sem demo: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261119-1044-AUX-03-W3-roteiro-conversa-diagnostica-sem-demo.md
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs #724–#727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pulls

## Próxima ação
**Conta principal/W00:** autorizar ou negar um único contato pós-evento com a Undergoth por e-mail ou Instagram e confirmar qual apresentação comercial é permitida enquanto o runtime permanece sem GO.

**AUX-03/W3:** somente após autorização, enviar uma mensagem pelo canal aprovado, registrar resposta e qualificar a próxima produção. Se não houver autorização, manter NOT_SENT e não disparar automaticamente.

## Precisa da conta principal
**SIM** — autorização de contato externo e confirmação do caminho de apresentação/cadastro.

## Limites
Nenhuma mensagem foi enviada. Nenhuma publicação foi agendada. Não houve alteração de código, PR, merge, build, deploy ou VPS.
