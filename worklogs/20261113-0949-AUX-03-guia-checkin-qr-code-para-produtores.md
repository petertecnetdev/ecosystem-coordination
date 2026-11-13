# AUX-03 — Worklog 2026-11-13 09:49 BRT — Guia de check-in por QR Code para produtores

## Objetivo
Criar um ativo editorial de aquisição para produtores/organizadores, diferente do guia anterior de QR Code voltado a participantes: explicar como organizar a portaria e validar entradas com a operação de check-in da Cutinapp.

## Área
SEO editorial, blog, aquisição de produtores, conteúdo social e conversão.

## Coordenação consultada
- Li `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/README.md`, `COMMANDS.md`, `REVENUE_TARGET.md` e `PROFITABILITY_PLAN.md`.
- Consultei `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md` e assignment `orchestration/assignments/AUX-03/W2.md`. W2 está AVAILABLE, sem override ativo.
- W1 AUX-03 permanece BLOCKED por dependência de mídia pública para publicação social; não tentei publicar pelo Metricool nem duplicar seu material.
- W3 AUX-03 concluiu handoff de landing de produtores (PR #724), sem autorização para editar sua implementação.
- Consultei o worklog de posicionamento de 12/11 e os commits recentes da coordenação. O prospect NC Entretenimento foi encaminhado por W3/W00 em 12/11; não repeti a prospecção.
- O guia de 10/11 trata do uso do ingresso digital pelo participante; este artigo trata da operação da portaria pelo produtor. Não reutilizei o mesmo ângulo.
- `CURRENT_STATE.md` ainda está consolidado em 30/10 e `BLOCKERS.md` lista FIN-P0-001, mas não espelha a issue pública #643. Não alterei arquivos de coordenação de outros owners.

## Confirmado — produto
- `src/pages/ticket/CheckinPage.js` na main: lista eventos do usuário publicados e não cancelados; permite selecionar o evento; ativa leitor de câmera; usa leitor nativo quando disponível e jsQR como fallback.
- A validação manual aceita códigos de ingresso e retirada de itens; os prefixos reconhecidos no frontend incluem CUT-, PASS- e ITEM-.
- A tela mostra contagem de emitidos, entradas e aguardando.
- Quando offline, pausa a câmera e bloqueia novas validações.
- A tela orienta a equipe a reconectar e validar novamente o mesmo QR se a conexão falhar durante a operação; não promovi essa mensagem a garantia independente de backend.
- O frontend emite eventos de telemetria `checkin_validation_succeeded`, `checkin_validation_rejected`, `checkin_validation_uncertain`, entre outros, com metadados de evento, tipo de QR, modo de leitor e status HTTP.
- `SeoManager.js` ainda contém metadados antigos da landing de produtores com “30 dias grátis”. PR #727 aberto corrige title/description/Schema e depende de #724. Não direcionei tráfego nem repeti o patch.
- Issue P0 #643 permanece OPEN; última atualização registrada em 10/11. A issue documenta diferença entre filesystem e release servida por Nginx/HTTPS.
- Revalidação pública de hoje: a raiz retornou HTML “Ative o JavaScript para usar a Cutinapp”; a ferramenta não conseguiu acessar `/for-producers` nem `/events`. Limite: isso não prova indisponibilidade universal nem substitui teste em smartphone/rede móvel.
- PRs #724, #725, #726 e #727 permanecem OPEN na consulta atual; não há merge comprovado.

## Hipótese
Um tutorial de operação de portaria pode atrair produtores que pesquisam soluções para check-in digital e aproximá-los do cadastro, porque demonstra uma tarefa concreta do ciclo do evento. Ainda não há dados que comprovem aumento de leads ou ativação.

## Recomendação
Publicar o artigo somente após resolver o gate público e revisar a landing/metadados de produtores. Derivar carrossel e Reel com capturas reais autorizadas; não usar mockups que pareçam uma gravação do produto.

## Trabalho realizado
1. Analisei o componente de check-in e a carteira de ingressos para distinguir o fluxo do produtor daquele do participante.
2. Preparei artigo SEO com intenção, palavra-chave, title, description, H1, slug, canonical proposto, Schema.org recomendado, CTA e FAQ.
3. Preparei carrossel de sete telas, legenda e roteiro de Reel de 20–25 segundos.
4. Defini métricas que podem ligar leitura editorial à landing e à publicação do primeiro evento; incluí telemetria de check-in já presente no frontend.
5. Registrei dependências reais de publicação: issue #643 e PRs #724/#727.

## Entregável
`deliverables/AUX-03/20261113-AUX-03-guia-checkin-qr-code-para-produtores.md`

## Canal
Blog Cutinapp → landing de produtores → cadastro → criação/publicação do primeiro evento. Distribuição complementar em Instagram carrossel/Reel/Stories.

## CTA
Conhecer a Cutinapp para produtores (`/for-producers`), após runtime e copy/metadados estarem liberados. CTA social: salvar e compartilhar o checklist de portaria.

## Métricas
- article_to_producer_landing_click_rate;
- producer_signup_rate;
- first_event_published_7d;
- checkin_validation_succeeded por evento;
- checkin_validation_rejected e checkin_validation_uncertain.
Baseline: N/D. Não foram consultados dados de tráfego/conversão.

## Evidências
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/ticket/CheckinPage.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/SeoManager.js
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261112-1009-AUX-03-posicionamento-por-publico.md

## Próxima ação
W00/conta principal: resolver e comprovar o gate #643; revisar a integração coordenada de #724 e #727. Após liberação, operador editorial cadastra artigo como rascunho e valida HTML/snapshot/CTA; W2 revisa indexação e métricas após publicação.

## Precisa da conta principal?
SIM — para desbloquear runtime público e autorizar a sequência de publicação/distribuição. Nenhuma ação de VPS foi realizada.

## Estado final
ARTICLE_PREPARED — SOCIAL_COPY_PREPARED — WORKLOG/CLAIM/HANDOFF_TO_BE_COMMITTED — NOT_PUBLISHED — NOT_INDEXED — NOT_SOCIAL_SCHEDULED — NO_PRODUCT_CODE_CHANGED — NO_BRANCH — NO_PR — NO_MERGE — NO_DEPLOY — CONVERSION_NOT_MEASURED.
