# AUX-03 W1 — Confirmação de distribuição real e controle de conversão — 2026-10-27

owner: AUX-03 / W1 — Instagram & Social Growth
priority: P1 (verificação de destino comercial) / P2 (distribuição orgânica)
status: PUBLISHED_PROVIDER_CONFIRMED — PUBLIC_PERMALINK_UNVERIFIED — CONVERSION_UNMEASURED
channel: Google Business Profile (não Instagram)
date: 2026-10-27 10:13 America/Sao_Paulo

## Objetivo / área
Converter a campanha de aquisição de produtores agendada em 26/10 de uma entrega apenas planejada para uma entrega com **publicação confirmada pelo provedor**, documentar o CTA e a medição, e evitar direcionar tráfego adicional para uma landing sem verificação de acesso.

## Oportunidade e coordenação
Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/, worklogs/ recentes e orchestration/assignments/AUX-03/W1.md. Não duplicar W2 (blog/SEO), W3 (landing e onboarding), nem os conteúdos W1 de 20–25/10. O worklog anterior `20261026-1047-AUX-03-W1-google-business-organic-producers.md` registrava agendamento `PENDING`; hoje o estado mudou.

## Confirmado — evidência do publicador
- Metricool getBrandSettings em 27/10: marca `cutinapp`, id `7119630`, timezone `America/Sao_Paulo`, `networksData` com `gbpData`, sem Instagram conectado comprovado.
- Metricool getScheduledPosts (20/10–03/11), relido em 27/10: publicação id `406658487`, UUID `2017393444520345981`, data 26/10/2026 11:15, provedor `gmb`, `status: PUBLISHED`, `detailedStatus: Published`, `autoPublish: true`, `draft: false`. **Confirma publicação no sistema do provedor, não URL pública verificável**.
- Abrir no planejador: https://app.metricool.com/planner/calendar?blogId=7119630&openWithPostUuid=2017393444520345981
- Consulta de métricas Instagram posts 20–27/10: `rows: []`. Não prova ausência de posts publicados diretamente na rede.
- Consulta de métricas GBP 24–27/10 não forneceu visualizações ou cliques utilizáveis da publicação; **não afirmar resultados**.
- Verificação de acesso à home `https://cutinapp.petertecnet.com.br/` via ferramenta de navegação retornou 530 em 27/10; teste de linha de comando em ambiente isolado não resolveu DNS. Essas observações **não comprovam indisponibilidade geral**, mas exigem validação em navegador móvel real antes de enviar mais tráfego.
- SentinelX list_hosts em 27/10: `petertecnetserver` offline desde 08:33 UTC; não prova indisponibilidade da aplicação.

## Trabalho realizado / entregável
Relida a publicação agendada no Metricool, verificado `PUBLISHED`, conferidas integrações e dados analíticos disponíveis, e documentado o controle de conversão com evidências e estado honesto. Nenhuma nova publicação foi criada enquanto o destino comercial não pôde ser validado.

**Copy já distribuída em 26/10:** “Você organiza shows, festas ou outras experiências? Uma divulgação clara ajuda o público a entender o evento e saber como participar. A Cutinapp conecta a organização e a descoberta de eventos em uma plataforma digital. Conheça a proposta e veja por onde começar.”

## CTA e métricas
CTA em circulação: Conheça a Cutinapp — https://cutinapp.petertecnet.com.br/?utm_source=google&utm_medium=organic&utm_campaign=aux03_produtores_20261026

Métrica principal em sete dias: sessões UTM `aux03_produtores_20261026` no site. Métricas de negócio: cadastros de produtores e primeiros eventos publicados atribuídos. Sem analytics de sessão/registro confirmado, registrar como **não medido**, não como zero.

## Hipótese / recomendação
Hipótese: a publicação no GBP pode atrair produtores qualificados, desde que o link funcione e o funil preserve UTMs.
Recomendação de execução: validar no celular a home com UTMs e o cadastro; só então continuar campanhas com link. Conectar Instagram ao Metricool para liberar as mídias W1 prontas e evitar dependência exclusiva do GBP.

## Próxima ação / conta principal
Conta principal necessária: **SIM** para (1) validar home e cadastro em navegador móvel e corrigir caso falhem; (2) confirmar integração Instagram; (3) disponibilizar dados de sessões/cadastros atribuídos em 02/11/2026. AUX-03 pode retomar distribuição com CTA após validação do destino.

NEXT_ACTION: validar URL de conversão mobile-first; obter permalink público da publicação; medir sessões/cadastros em 02/11.
