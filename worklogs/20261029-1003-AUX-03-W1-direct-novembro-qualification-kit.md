# AUX-03 / W1 — 29/10/2026 — Kit de conversão de leads NOVEMBRO

owner: AUX-03 / W1 — Instagram & Social Growth
priority: P2
status: COPY_READY — DISTRIBUTION_DEPENDS_ON_INSTAGRAM_DIRECT — NOT_SENT
date: 2026-10-29 10:03 America/Sao_Paulo

## Objetivo e área
Converter contatos de produtores que responderem à campanha de 28/10 em conversas qualificadas, sem inventar resultados ou enviar links não validados. Área: Instagram Direct, aquisição e ativação de produtores.

## Coordenação e prevenção de duplicidade
Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/assignments/AUX-03/W1.md`, `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md`, worklog W1 de 28/10 e buscas de claims. Leitura/listagem do diretório `claims/active/` não foi suportada pela ação fetch_file; buscas GitHub não retornaram resultados. Não foi criado claim de código, landing, SEO ou mídia. Esta entrega complementa a publicação de 28/10 sem duplicar os conteúdos de feed dos dias 19–25.

## Confirmado / evidências
- Metricool brandId 7119630, fuso America/Sao_Paulo, integração retornada: `gbpData` (sem Instagram conectado confirmado).
- Releitura do planejador em 29/10 retornou publicação de 28/10 ID `408949842`, UUID `-3400814918281901423`, `providers[0].network=gmb`, `status=PUBLISHED`. Isso confirma o status no planejador, não URL pública nem alcance.
- Publicação de 26/10 ID `406658487` também consta como `PUBLISHED`.
- Consulta Instagram Feed 15–29/10: `rows: []`; não comprova ausência de posts diretos.
- Consulta de posts GBP 25–29/10: `rows: []`; não permite medir impressões, visualizações ou contatos.
- Home Cutinapp foi recuperada via navegação web em 29/10 com título `Cutinapp | Rede social e plataforma global de eventos` e shell `Ative o JavaScript para usar a Cutinapp`; isso não valida onboarding mobile ou páginas de conversão.
- Perfil Instagram direto indisponível ao navegador; bio, destaques e posts recentes não auditados diretamente.

## Oportunidade e hipótese
O post de 28/10 convidou produtores com eventos de novembro a enviar `NOVEMBRO` por Direct. Sem um roteiro de atendimento, uma eventual resposta pode ficar sem qualificação e não chegar à criação de produção. Hipótese: uma resposta curta e padronizada aumenta a proporção de contatos que fornecem cidade, categoria e data.

## Trabalho realizado / entregável
Kit operacional de resposta manual a Directs, com três mensagens e critério de qualificação. Não há evidência de mensagens recebidas nem de disparos realizados.

### Mensagem 1 — resposta a contato real
Olá! Obrigado por chamar a Cutinapp. Para entender sua próxima produção, me conta três coisas?
1) Em qual cidade será o evento?
2) Que tipo de evento você organiza?
3) Qual é a data prevista?
Com isso, consigo te orientar sobre o próximo passo na plataforma.

### Mensagem 2 — após receber cidade, tipo e data
Perfeito, obrigado pelas informações! A Cutinapp reúne divulgação e descoberta de eventos, com recursos para quem organiza experiências. Você já tem uma produção cadastrada na plataforma ou seria a primeira?
Se for a primeira: Posso te passar o caminho de cadastro assim que confirmarmos o acesso pelo celular. Não precisa enviar dados pessoais ou documentos por aqui.
Se já tem produção: Qual é a principal dificuldade agora: divulgar, organizar as informações do evento ou vender ingressos?

### Mensagem 3 — follow-up único após 48h sem resposta
Oi! Passando uma vez para retomar sua mensagem sobre o evento de novembro. Se ainda quiser conversar, me envie cidade, tipo de evento e data. Se não for o momento, tudo bem — não vou insistir.

## Canal / CTA / métrica
- Canal: Instagram Direct de @cutinapp; envio manual e somente a produtores que iniciarem contato.
- CTA: **Seu evento já está cadastrado na Cutinapp ou será o primeiro?**
- Métrica principal: **contatos qualificados que avançam para orientação de cadastro / contatos qualificados** em sete dias.
- Qualificado = produtor identificável + cidade + categoria + data de evento futura.
- Métrica de negócio: **primeiras produções publicadas atribuídas à campanha**, quando verificáveis.
- Janela de avaliação: até 04/11/2026.
- Registro mínimo: data, @perfil, cidade, categoria, data do evento, estágio (novo / qualificado / orientado / produção criada), próxima ação. Não solicitar documentos, CPF ou pagamentos por DM. Sem disparos em massa.

## Próxima ação / conta principal
**Conta principal necessária: SIM**. Abrir Direct, responder somente a contatos reais, registrar leads, validar cadastro mobile antes de enviar links e confirmar primeiras produções quando existirem. Se não houver mensagens, registrar zero apenas após verificar a caixa, não por ausência de analytics no Metricool.

NEXT_ACTION: executar o roteiro nos Directs recebidos e reportar a taxa de qualificação e a criação de produções.

Estado final: `CAMPAIGN_28OCT_PUBLISHED_IN_PLANNER — DIRECT_KIT_READY — NOT_SENT — NO_CONVERSIONS_VERIFIED`.
