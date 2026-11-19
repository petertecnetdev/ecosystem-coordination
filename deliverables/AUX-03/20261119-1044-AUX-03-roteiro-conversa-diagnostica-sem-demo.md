# AUX-03 W3 — Roteiro de conversa comercial sem demonstração ao vivo

**Data:** 19/11/2026 10:44 BRT  
**Objetivo:** permitir qualificação comercial honesta de um produtor enquanto a experiência pública da Cutinapp ainda não recebeu GO, sem prometer uma demonstração funcional nem enviar o prospecto a um cadastro não validado.

## Área
Aquisição de produtores, qualificação comercial, ativação e conversão.

## Oportunidade
A fila de 18/11 consolidou sete prospectos ativos e um piloto prioritário (Taberna Music Pub). O worklog e o claim anteriores registram zero contatos enviados e exigem autorização da conta principal. A janela sugerida para o piloto Taberna era 18–19/11; hoje, 19/11, é o último dia dessa janela original. O bloqueio não deve ser contornado por contato não autorizado.

A oportunidade desta execução é preparar um formato de primeira conversa que não dependa de login, landing, cadastro ou demo ao vivo: uma conversa de descoberta de 10 minutos para entender a próxima produção e verificar se existe aderência comercial.

## Confirmado
- A fila comercial e a mensagem de Taberna foram registradas em 18/11; nenhum contato foi enviado.
- Issue P0 #643 permanece aberta e descreve divergência entre release no filesystem e release servido pelo Nginx/HTTPS.
- PRs #724, #725, #726 e #727 continuam abertos na consulta desta execução; #727 está em Draft e depende de #724 ou do mesmo release.
- A coordenação mantém W3 como papel de aquisição/conversão após conclusão da atribuição específica de landing. W1 está bloqueado por mídia pública para distribuição social; W2 permanece no papel de SEO/blog/public discovery. Esta entrega não assume esses escopos.

## Hipótese
Uma conversa consultiva de descoberta pode avançar o relacionamento comercial sem apresentar uma demo, desde que a limitação seja explicitada e não haja promessas de disponibilidade, preço, trial, taxas ou migração.

## Recomendação
Usar o piloto Taberna apenas após autorização explícita da conta principal. O CTA deve convidar para entender a próxima edição, não para cadastrar ou migrar o evento atual.

## Mensagem revisada — Taberna Music Pub
**Canal prioritário:** botão público “Fale com o produtor” da página Sympla. Não usar WhatsApp de reservas como canal B2B sem autorização específica.

Olá, equipe Taberna! Vi que a GERAÇÃO 2K aconteceu nos dias 14 e 15 de novembro. Espero que a edição tenha corrido bem.

Falo pela Cutinapp, plataforma de eventos da Peter Tecnet. Gostaria de entender se vocês já têm uma próxima edição em planejamento e como organizam hoje a divulgação, os ingressos e a entrada do público.

Neste primeiro contato, minha proposta é uma conversa breve de 10 minutos para conhecer a operação e avaliar se existe aderência. Não quero interferir na edição que acabou de acontecer nem prometer uma demonstração ao vivo antes da validação do ambiente público.

Se fizer sentido, respondam **PRÓXIMA DATA** e combinamos um horário.

## Roteiro da conversa — 10 minutos
### 0–2 min | Contexto
- Agradecer o tempo e confirmar se a conversa é sobre uma próxima edição.
- Perguntar qual é o formato de evento que a equipe pretende realizar em seguida.

### 2–6 min | Diagnóstico
1. Já existe uma próxima data ou produção em planejamento?
2. Como os ingressos são divulgados e vendidos atualmente?
3. Qual parte costuma gerar mais trabalho: página e informações, lotes/ingressos, atendimento ao público, check-in ou acompanhamento das vendas?
4. Quem decide a plataforma e o processo de venda?
5. O que precisaria ser demonstrado para a equipe considerar uma alternativa?

### 6–8 min | Síntese
- Repetir o problema principal com as palavras do produtor.
- Confirmar se é uma prioridade real para a próxima edição.
- Não comparar taxas, preço ou desempenho de plataformas sem dados aprovados.

### 8–10 min | Próximo passo honesto
Se houver aderência:
- Registrar formato, janela da próxima produção e principal necessidade.
- Informar que a conta responsável confirmará a disponibilidade de uma apresentação do produto quando o ambiente público estiver validado.
- Combinar autorização para novo contato e prazo de retorno.

Se não houver aderência:
- Agradecer e encerrar sem insistência.
- Registrar “sem timing” ou “sem fit”, sem adicionar o contato a campanhas recorrentes sem consentimento.

## Guardrails comerciais
- Não enviar link de cadastro enquanto o runtime público não receber GO.
- Não afirmar que uma demonstração ao vivo está disponível.
- Não prometer trial, 30 dias grátis, assinatura, preço, percentual ou condição comercial não confirmada.
- Não prometer migração, integração ou suporte específico sem validação.
- Não solicitar dados pessoais de participantes, listas de compradores ou credenciais.
- Não tratar canal de reserva/venda de ingressos como consentimento para prospecção B2B.
- Não enviar mensagem externa sem autorização da conta principal.

## Qualificação e handoff
Marcar como **lead qualificado** somente quando houver:
- responsável ou decisor identificado;
- próxima produção concreta ou planejamento reconhecido;
- necessidade operacional/comercial explícita;
- concordância com próximo contato.

Registrar: produtor, evento/produção (se público), data aproximada, canal autorizado, dor principal, decisor, resposta, consentimento para retorno e próxima ação. Não registrar dados sensíveis.

## Canal e CTA
- **Canal:** contato B2B pós-evento, preferencialmente botão “Fale com o produtor” da Sympla.
- **CTA:** PRÓXIMA DATA — conversa de descoberta de 10 minutos.
- **Métrica principal de negócio:** primeiro evento publicado na Cutinapp em até 30 dias após conversa comercial qualificada e aceita.
- **Métrica operacional:** conversas qualificadas ÷ contatos autorizados efetivamente enviados.
- **Baseline:** zero contatos enviados na fila anterior; conversões N/D.

## Evidências
- Fila anterior: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261118-1040-AUX-03-fila-contatos-produtores-pos-evento.md
- Taberna GERAÇÃO 2K: https://www.sympla.com.br/evento/geracao-2k/3626527
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #725: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/725
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727

## Próxima ação
Conta principal/W00: autorizar ou negar o piloto Taberna e aprovar o formato de conversa sem demo. Se autorizado, AUX-03 envia uma única mensagem pelo canal público aprovado e registra a resposta. Se a janela de 19/11 passar sem autorização, mover o piloto para “janela expirada — revalidar timing” e não disparar automaticamente.

## Precisa da conta principal
**SIM** — autorização de contato externo e aprovação do enquadramento comercial sem demonstração.

## Estado final
DISCOVERY_CALL_SCRIPT_READY — TABERNA_OUTREACH_NOT_SENT — PUBLIC_RUNTIME_NO_GO — ACCOUNT_MAIN_APPROVAL_REQUIRED — NOT_DEPLOYED.
