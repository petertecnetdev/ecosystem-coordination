# AUX-03 W3 — Fila priorizada de contatos pós-evento

**Data:** 18/11/2026 10:40 BRT  
**Área:** aquisição de produtores, prospecção contextual e conversão  
**Prioridade:** P1 — destravar primeiro contato antes de ampliar a lista  
**Estado:** QUEUE_PRIORITIZED — TABERNA_FIRST_CONTACT_READY — NOT_SENT

## 1. Objetivo

Parar de acumular prospectos com mensagens não enviadas e transformar a pesquisa comercial de 05 a 16/11 em uma fila pequena, ordenada por janela de contato. A primeira ação recomendada é um único piloto com Taberna Music Pub, cujo evento GERAÇÃO 2K já encerrou.

## 2. Diagnóstico

### Confirmado

- Os worklogs AUX-03 de 05 a 16/11 contêm oito prospectos com evento ou produção identificada: Raphaela Gentil, Taberna Music Pub, Joint Records Brasil, NC Entretenimento, Funclube, Raiza Morgana/Noite Infame, Debora Machado/Blue Velvet e Undergoth (oito registros, contando os dois eventos/prospectos independentes).
- As abordagens anteriores foram preparadas, mas os respectivos worklogs registram que nenhuma mensagem foi enviada.
- O evento GERAÇÃO 2K do Taberna Music Pub ocorreu de 14/11/2026 às 20h até 15/11 às 03h e a página pública agora informa “O evento já encerrou”. A página oferece “Fale com o produtor” e lista WhatsApp de reservas.
- Mosh Pit Fest / Joint Records Brasil: 21/11/2026, 22h–06h.
- Noite Infame 2 / Raiza Morgana Lima Ribeiro: 21/11/2026, 18h30–22h.
- Undergoth Nosferatu Fest: 21/11/2026, 20h–03h30 de 22/11.
- CHAWON FEST / NC Entretenimento: Fan Event em 26/11 e show em 27/11.
- Funfarra Last Dance / Funclube: 28/11/2026, 22h–06h de 29/11.
- Blue Velvet Hip-Hop Lounge / Debora Machado: 11/12/2026, 20h–00h30 de 12/12.

### Hipótese

A taxa de resposta tende a ser mais útil quando o contato ocorre depois do encerramento da produção atual, sem competir com a operação de venda e atendimento do evento. Isso ainda não foi testado pela Cutinapp.

## 3. Fila recomendada

| Ordem | Produtor | Evento e situação | Janela sugerida | Canal prioritário | CTA |
|---|---|---|---|---|---|
| 1 | Taberna Music Pub | GERAÇÃO 2K encerrou em 15/11 | 18–19/11 | Sympla “Fale com o produtor”; WhatsApp de reservas somente se autorizado para contato B2B | PRÓXIMA DATA |
| 2 | Joint Records Brasil | Mosh Pit Fest em 21/11 | 23–24/11 | Sympla “Fale com o produtor” | PRÓXIMA PRODUÇÃO |
| 3 | Raiza Morgana Lima Ribeiro | Noite Infame 2 em 21/11 | 23–24/11 | Sympla “Fale com o produtor” | PRÓXIMA EDIÇÃO |
| 4 | Undergoth | 10º Encontro Gótico em 21/11 | 23–24/11 | E-mail público ou Instagram oficial; não usar canal de venda como primeiro contato B2B | PRÓXIMA EDIÇÃO |
| 5 | NC Entretenimento | CHAWON FEST em 26–27/11 | 30/11–01/12 | Sympla “Fale com o produtor” | AGENDA 2027 |
| 6 | Funclube | Funfarra Last Dance em 28/11 | 30/11–01/12 | Sympla “Fale com o produtor” | AGENDA 2027 |
| 7 | Debora Machado | Blue Velvet em 11/12 | 14/12 | Sympla “Fale com o produtor” | PRÓXIMA PRODUÇÃO |

Raphaela Gentil permanece em backlog de baixa prioridade: o evento de 07/11 encerrou e a janela de pós-evento já passou. Não criar nova abordagem até surgir sinal de nova produção ou autorização para reativar o contato.

## 4. Primeiro piloto — Taberna Music Pub

### Evidência

- Página pública: https://www.sympla.com.br/evento/geracao-2k/3626527
- A página confirma produtor Taberna Music Pub, evento encerrado e canal “Fale com o produtor”.
- O telefone publicado (62) 99692-0505 aparece como WhatsApp de reservas. Não tratar automaticamente um canal de reservas como autorização para mensagens comerciais; preferir o botão “Fale com o produtor” ou obter confirmação da conta principal antes de usar WhatsApp.

### Mensagem pronta

Olá, equipe Taberna! Vi que a GERAÇÃO 2K aconteceu nos dias 14 e 15 de novembro. Espero que a edição tenha corrido bem.

Falo pela Cutinapp, plataforma de eventos da Peter Tecnet. Gostaria de saber se vocês já têm uma próxima edição em planejamento.

A proposta é apresentar, para uma futura produção, como a Cutinapp organiza a página pública do evento, os ingressos digitais e as informações dos participantes — sem interferir na edição que acabou de acontecer.

Se fizer sentido conversar, respondam **PRÓXIMA DATA** e combinamos um horário breve.

**Limite comercial:** não incluir link de cadastro, preço, trial, taxa ou promessa de demonstração ao vivo até a conta principal validar o runtime e autorizar o contato.

## 5. Regra de execução da fila

1. Autorizar e enviar somente o piloto Taberna.
2. Registrar data, canal, resposta e próximo passo; não contar mensagem preparada como contato realizado.
3. Não enviar follow-up automático. Fazer no máximo um acompanhamento manual, após intervalo razoável e se autorizado.
4. Após medir o piloto, liberar individualmente os contatos pós-evento de 23–24/11.
5. Não adicionar novos prospectos enquanto a fila atual não tiver primeiro contato ou decisão explícita de descarte.

## 6. Obstáculo da jornada

O gargalo imediato entre conhecer a Cutinapp e publicar o primeiro evento não é falta de prospectos: é a ausência de primeiro contato autorizado e, em paralelo, o runtime público ainda sem GO.

O runtime continua exigindo resolução da issue P0 #643. A raiz pública retornou HTTP 530 nesta verificação; isso não prova indisponibilidade para todos os usuários. PRs #724, #725 e #726 permanecem abertos; #727 permanece aberto em Draft e depende da integração coordenada com #724.

- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727

## 7. Canal, CTA e métricas

- **Canal:** contato B2B pós-evento por canal público do produtor, começando por Sympla “Fale com o produtor”.
- **CTA do piloto:** PRÓXIMA DATA.
- **Métrica principal de negócio:** primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada e aceita.
- **Métrica operacional:** respostas positivas ÷ contatos autorizados efetivamente enviados.
- **Indicadores:** conversas qualificadas, demonstrações aceitas, cadastros, produções criadas e eventos publicados.
- **Baseline:** zero contatos enviados nesta fila; conversões N/D.

## 8. Próxima ação e dependências

**Conta principal/W00:** autorizar ou negar o piloto com Taberna Music Pub e confirmar qual apresentação da Cutinapp pode ser oferecida enquanto o runtime público permanece sem GO.

**AUX-03/W3:** após autorização, enviar uma única abordagem pelo canal aprovado, registrar resposta e acompanhar a oportunidade até o primeiro evento publicado.

**Precisa da conta principal:** SIM — autorização de contato externo e validação do caminho de demonstração/cadastro.

## 9. Limites desta execução

- Nenhuma mensagem foi enviada.
- Nenhuma publicação foi agendada.
- Nenhum código, PR, merge, build, deploy ou VPS foi alterado.
- A fila consolida prospectos já pesquisados; não cria novos contatos nem presume interesse.
