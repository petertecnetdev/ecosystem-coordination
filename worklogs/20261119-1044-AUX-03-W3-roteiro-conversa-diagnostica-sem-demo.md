# AUX-03 W3 — Worklog 2026-11-19 — conversa diagnóstica sem demo

## Objetivo
Remover uma objeção operacional da prospecção: preparar uma primeira conversa comercial que possa qualificar um produtor sem depender de demo ao vivo, cadastro ou landing pública ainda não validada.

## Área
Aquisição de produtores, qualificação, relacionamento comercial e conversão.

## Oportunidade
A fila de 18/11 tem sete prospectos ativos e Taberna Music Pub como piloto. O worklog anterior registra zero contatos enviados e exige autorização da conta principal. A janela original sugerida para Taberna era 18–19/11; 19/11 é o último dia dessa janela.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, COMMANDS.md.
- orchestration/STATE.md, orchestration/WORKER_REGISTRY.md e assignments AUX-03 W1/W2/W3.
- Worklog, claim e entregável de 18/11.
- Issue #643 e PRs #724–#727 diretamente no repositório Cutinapp.
- W1 permanece BLOCKED por dependência de mídia pública; W2 está AVAILABLE no papel SEO/blog/public discovery; W3 assignment específico de landing está DONE e retorna à função-base de aquisição/conversão.

## Confirmado
- Taberna GERAÇÃO 2K encerrou em 15/11; mensagem pós-evento foi preparada em 18/11, mas não enviada.
- A janela 18–19/11 era recomendação de contato, não autorização.
- Issue #643 permanece aberta e descreve divergência entre o release validado no filesystem e o release servido por Nginx/HTTPS.
- PRs #724, #725, #726 e #727 continuam abertos na consulta desta execução; #727 está em Draft.
- Nenhum contato externo foi enviado por esta execução.

## Hipótese
Uma conversa consultiva de 10 minutos, sem prometer demo, pode qualificar necessidade e timing enquanto o runtime não recebe GO. A hipótese ainda não foi testada com produtores.

## Trabalho realizado
1. Releitura da fila comercial para não criar prospecto ou mensagem duplicada.
2. Revisão do estado da coordenação e da atribuição específica de W3.
3. Criação de roteiro de conversa de descoberta com duração de 10 minutos.
4. Inclusão de cinco perguntas de qualificação e critérios para considerar o lead qualificado.
5. Revisão da mensagem Taberna para convidar a conversa de descoberta, sem sugerir demo ao vivo.
6. Definição de guardrails: sem link de cadastro, preço, trial, taxa, migração ou promessa de funcionalidade não validada.
7. Definição do caminho de encerramento quando não houver fit e da regra de consentimento para retorno.

## Entregável
deliverables/AUX-03/20261119-1044-AUX-03-roteiro-conversa-diagnostica-sem-demo.md

## Canal
Contato B2B pós-evento via canal público do produtor, preferencialmente botão “Fale com o produtor” da Sympla. WhatsApp de reservas não é tratado como consentimento para prospecção B2B.

## CTA
PRÓXIMA DATA — conversa de descoberta de 10 minutos.

## Métrica principal
Primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada e aceita.

Métrica operacional: conversas qualificadas ÷ contatos autorizados efetivamente enviados. Baseline anterior: zero contatos enviados; conversões N/D.

## Evidências
- Fila e mensagem anterior: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261118-1040-AUX-03-fila-contatos-produtores-pos-evento.md
- Taberna: https://www.sympla.com.br/evento/geracao-2k/3626527
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs #724–#727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pulls

## Próxima ação
Conta principal/W00 autoriza ou nega o piloto Taberna e aprova a conversa de descoberta sem demo. Se autorizado hoje, AUX-03 envia uma única mensagem pelo canal público aprovado e registra resposta. Se não autorizado até o fim de 19/11, marcar janela expirada e revalidar timing antes de qualquer contato.

## Precisa da conta principal
SIM — autorização para contato externo e aprovação do enquadramento comercial.

## Estado final
DISCOVERY_CALL_SCRIPT_READY — TABERNA_OUTREACH_NOT_SENT — ACCOUNT_MAIN_APPROVAL_REQUIRED — WORKLOG_COMMITTED — NOT_DEPLOYED.
