# AUX-03 W2 — Worklog 2026-11-10 10:16 BRT — Guia do participante: ingresso digital e QR Code

## Objetivo
Preparar um ativo evergreen de aquisição orgânica para participantes que pesquisam como localizar e apresentar um ingresso digital com QR Code, direcionando-os à descoberta de eventos publicados na Cutinapp.

## Área
SEO editorial, blog, aquisição de participantes, educação do usuário, compartilhamento e conversão para páginas de eventos.

## Oportunidade
O inventário editorial AUX-03 já contém um guia sobre compra de ingresso online com segurança, mas a pesquisa de arquivos não encontrou um artigo específico sobre abrir o ingresso na carteira, apresentar o QR Code, proteger o código e transferir a titularidade. A intenção de busca é prática e próxima do uso do produto. Os resultados atuais para consultas equivalentes favorecem guias passo a passo sobre abrir o ingresso e mostrar o QR Code na entrada.

## Confirmado
- A assignment AUX-03/W2 estava AVAILABLE; W1 está BLOCKED e W3 já concluiu o gate de aquisição de produtores. O escopo escolhido é conteúdo para participantes, sem duplicar a sequência de ativação de produtores.
- src/pages/ticket/MyPassesPage.js apresenta a carteira de ingressos e encaminha o participante aos detalhes do ingresso.
- src/pages/ticket/PassDetailPage.js apresenta o QR Code individual, oferece ampliação/tela cheia, alerta para não compartilhar prints e oferece a ação de compartilhar a página do evento sem compartilhar o QR.
- O mesmo componente implementa transferência oficial por e-mail de uma conta Cutinapp; após a transferência, o QR anterior é invalidado e o destinatário recebe um novo código.
- src/pages/ticket/CheckinPage.js contém leitor por câmera e alternativa de validação manual; o servidor confirma a validade antes de registrar a entrada.
- A main do frontend permanece em 9b5502cdf2dca098bc73a465d58d7274b596d0a4 na consulta de 10/11.
- PR #722 está OPEN, NOT_MERGED, base main, head feat/aux03-blog-editorial-links-20261013; o InlineText atual do BlogArticlePage.js reconhece negrito, mas não converte links Markdown em âncoras.
- PRs #724, #725 e #726 continuam OPEN/NOT_MERGED; #727 continua OPEN/DRAFT/NOT_MERGED.
- A consulta Metricool da marca cutinapp (ID 7119630) retornou somente gbpData em networksData, sem instagramData. Isso não prova ausência de publicações feitas diretamente no Instagram; apenas significa que a conexão consultada não fornece Instagram para publicação/analytics.
- A home pública observada pela pesquisa web retorna somente “Ative o JavaScript para usar a Cutinapp”; /events e /for-producers não puderam ser abertas pela mesma ferramenta. Isso não prova indisponibilidade universal, mas mantém o gate de campanha pendente de validação em dispositivo real.
- A busca desta execução não forneceu uma página de evento publicada da Cutinapp que pudesse ser confirmada. O guia foi escrito como evergreen e não inventa evento, artista, data, preço, local ou disponibilidade.

## Hipótese
Um guia específico de uso do QR Code pode captar buscas de participantes e reduzir dúvidas pré-evento. O CTA para a área de eventos pode converter parte dessas visitas em descoberta de eventos. Não há baseline nem uplift comprovado.

## Trabalho realizado
1. Revisei COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims ativos/completados, assignments AUX-03, worklogs e entregas editoriais recentes.
2. Verifiquei a implementação real da carteira, do detalhe do ingresso e do check-in para não prometer recursos inexistentes.
3. Pesquisei a intenção atual de busca e confirmei que o formato passo a passo é adequado.
4. Preparei um artigo original com metadados SEO, canonical proposto, CTA para /events, checklist do participante e conteúdo limitado às funcionalidades confirmadas.
5. Preparei payload JSON para CMS com status draft.
6. Derivei um roteiro de carrossel Instagram com sete telas e legenda, sem agendar ou publicar.

## Entregáveis
- deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md
- deliverables/AUX-03/20261110-W2-ingresso-digital-qr-code-cms-draft.json

Commits de coordenação:
- Artigo e pacote de distribuição: 36be8dda65f5231f303cd744ee08229b5f9bd72a
- Payload CMS: a97ed54b4e24c0cf2e31463aa63e9998debd2c0f

## Canal e CTA
- Canal principal: blog / busca orgânica.
- Canal secundário: Instagram carrossel, após arte original e validação do canal.
- CTA do artigo: explorar eventos publicados em /events.
- CTA social: salvar o guia e compartilhar a página pública do evento, nunca o QR individual.

## Métricas
- Impressões, cliques e CTR orgânico do artigo (Search Console).
- Sessões orgânicas do artigo que abrem páginas de eventos.
- Cliques no CTA /events por sessão do artigo, quando instrumentados.
- Seleção de ingresso e início de checkout atribuídos à origem do artigo, quando disponíveis.
- Salvamentos e compartilhamentos por alcance do carrossel.
- Baseline: N/D. Nenhuma métrica de Search Console, Analytics ou Instagram foi consultada nesta execução.

## Dependências / bloqueios de publicação
- PR #722 precisa ser revisado/integrado ou o CTA deve usar um campo de link comprovadamente suportado pelo CMS; o renderizador atual não transforma Markdown link em âncora.
- W09 mantém ownership do gerador SEO global; o corpo integral do artigo deve estar no HTML inicial/snapshot ou ter rastreabilidade validada antes de declarar SEO concluído.
- Gate público AUX-03 de 09/11 continua NO-GO para campanhas até a conta principal validar /events e a jornada em smartphone, Wi-Fi e rede móvel.
- O Instagram não aparece conectado na configuração Metricool consultada; não foi possível preparar agendamento/publicação social com evidência.
- A imagem de capa do artigo e as sete telas do carrossel ainda precisam ser produzidas com a identidade oficial.

## Próxima ação
1. Conta principal/W00 valida o gate público em dispositivo real.
2. Owner do PR #722 integra e valida os links editoriais em mobile.
3. W09 confirma o conteúdo integral do artigo no snapshot/HTML inicial.
4. Operador editorial autorizado verifica duplicidade no CMS e submete o JSON como rascunho, retornando ID/URL.
5. Após GO, produzir a arte original e distribuir o carrossel; medir saves, shares, visitas e cliques para eventos.

## Precisa da conta principal?
SIM — liberação do gate público, autorização de publicação e distribuição.

## Estado final
EDITORIAL_ASSET_READY — CMS_PAYLOAD_PREPARED — NOT_SUBMITTED_TO_CMS — NOT_PUBLISHED — NOT_INDEXED — SOCIAL_NOT_SCHEDULED — NO_PRODUCT_CODE — NO_BRANCH — NO_PRODUCT_PR — NO_MERGE — NO_DEPLOY — NO_VPS — CONVERSION_NOT_MEASURED.
