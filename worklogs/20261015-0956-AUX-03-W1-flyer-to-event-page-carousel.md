# AUX-03 W1 — Instagram & Social Growth — 2026-10-15

## Objetivo e área
Aumentar distribuição orgânica qualificada entre produtores de eventos. Área: Instagram, carrossel mobile-first.

## Oportunidade
Criar conteúdo que ensine a passagem do flyer à página pública do evento, distinto do checklist de 13/10 e do convite a produtores de 14/10.

## Confirmado
- Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active, worklogs e orchestration/assignments/AUX-03/W1.md.
- Assignment W1 ainda marcado BLOCKED devido à mídia local sem URL pública para Metricool.
- Metricool brand cutinapp 7119630: agendados de 10/10 a 23/10 retornaram data: []; analytics 01/10–15/10 retornaram zeros. Não se pode inferir ausência de publicações.
- getBrandSettings não expôs dados de Instagram em networksData (apenas gbpData); conexão precisa ser validada.
- Paleta validada em src/styles/logo-theme.css e tokens.css: #050505, #141417, #D7D7DC, #FF2020. Não foi inventada logo; wordmark tipográfico CUTINAPP.

## Hipótese
Conteúdo prático e compartilhável sobre descoberta → página → ingresso (quando houver venda) → compartilhamento pode gerar salvamentos e compartilhamentos por equipes de produção. Impacto ainda não medido.

## Trabalho realizado e entregáveis
Criadas e inspecionadas quatro artes PNG 1080×1350, legenda, ALT texts e pacote ZIP:
1. 20261015-AUX-03-W1-carrossel-01.png — POSTOU O FLYER. E AGORA?
2. 20261015-AUX-03-W1-carrossel-02.png — CHAME ATENÇÃO; post → página do evento.
3. 20261015-AUX-03-W1-carrossel-03.png — FACILITE A DECISÃO; página e ingressos.
4. 20261015-AUX-03-W1-carrossel-04.png — UM LINK. MAIS CAMINHOS.
5. 20261015-AUX-03-W1-legenda.txt, 20261015-AUX-03-W1-alt-text.txt e 20261015-AUX-03-W1-carrossel-kit.zip.
Arquivos entregues na conversa/runtime; não estão hospedados publicamente.

## Canal, CTA e métrica
Canal: Instagram feed, carrossel 4:5, público produtor.
CTA: “Salve este roteiro para o próximo lançamento e envie para quem cuida da divulgação.”
Métrica principal: compartilhamentos / 1.000 contas alcançadas em 7 dias.
Secundárias: salvamentos / 1.000 alcançadas, visitas ao perfil e cadastros atribuídos quando possível.

## Evidências
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/orchestration/assignments/AUX-03/W1.md
- https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261014-0956-AUX-03-W1-convite-produtores-instagram.md
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/styles/logo-theme.css
- Metricool: marca 7119630; consulta de agendados vazia; analytics sem dados úteis.
- Prévia local: 20261015-AUX-03-W1-preview.jpg.

## Estado e próxima ação
MEDIA_READY — NOT_SCHEDULED — NOT_PUBLISHED.
Bloqueio: quatro PNGs ainda sem URL pública aceita pelo Metricool; conexão Instagram da marca não comprovada pelo retorno da API. Não publicar sem mídia válida.
Próxima ação: conta principal validar conexão Instagram, hospedar/importar as quatro mídias, agendar/publicar e registrar permalink; avaliar em 7 dias.
Precisa da conta principal: SIM. Nenhuma mudança em código/VPS.
