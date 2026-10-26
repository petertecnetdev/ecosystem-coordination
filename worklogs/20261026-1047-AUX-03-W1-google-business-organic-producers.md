# AUX-03 W1 — Distribuição orgânica conectada (2026-10-26)

- **Owner:** AUX-03 / W1 — Instagram & Social Growth
- **Data:** 2026-10-26 10:47 America/Sao_Paulo
- **Objetivo:** converter visibilidade orgânica em visitas qualificadas de produtores, usando canal realmente conectado enquanto Instagram não está disponível no publicador.
- **Área:** social/distribuição orgânica, aquisição de produtores, CTA e mensuração.
- **Prioridade:** P2 (não bloqueia P0).
- **Oportunidade:** os entregáveis de Instagram de 20 a 25/10 permaneciam com publicação pendente; em Metricool, a marca Cutinapp `7119630` retornou somente `gbpData`, sem conexão do Instagram comprovada. Evitar criar mais uma peça de Instagram sem distribuição.
- **Coordenação consultada:** `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/active/`, `worklogs/`, `orchestration/assignments/AUX-03/W1.md`. Sem claim concorrente assumido.
- **Trabalho realizado:** verificados brand settings e agendamentos entre 19/10 e 03/11; nenhum agendamento anterior retornado. Verificados PRs de conversão: #722, #724 e #725 abertos e sem merge. Evitado direcionar tráfego para `/for-producers` antes de #724. Criada e relida uma publicação informativa no canal Google Business Profile conectado.
- **Entregável:** publicação de texto agendada, ID Metricool **406658487**, UUID `2017393444520345981`.
- **Canal:** Google Business Profile da marca Cutinapp via Metricool (canal secundário; **não** Instagram).
- **Horário:** 2026-10-26 11:15 America/Sao_Paulo.
- **Texto agendado:**

> Você organiza shows, festas ou outras experiências? Uma divulgação clara ajuda o público a entender o evento e saber como participar.
>
> A Cutinapp conecta a organização e a descoberta de eventos em uma plataforma digital. Conheça a proposta e veja por onde começar:
> https://cutinapp.petertecnet.com.br/?utm_source=google&utm_medium=organic&utm_campaign=aux03_produtores_20261026

- **CTA:** Conheça a Cutinapp (home, não landing de produtores pendente de revisão).
- **Métrica principal:** sessões da campanha `aux03_produtores_20261026` com `utm_source=google` e `utm_medium=organic`, quando houver analytics validado.
- **Métrica de negócio:** cadastros de produtores e primeiros eventos publicados atribuídos à campanha, se o funil preservar os parâmetros. **Sem baseline nem conversão comprovada.**
- **Hipótese:** uma postagem orgânica no canal já conectado pode gerar visitas de organizadores sem depender de mídia ou conexão do Instagram.
- **Evidências:** `getBrandSettings` com `gbpData` e sem Instagram; `getScheduledPosts` após escrita confirmou ID 406658487, `autoPublish=true`, `draft=false`, provedor `gmb`, status `PENDING`; [abrir no planejador](https://app.metricool.com/planner/calendar?blogId=7119630&openWithPostUuid=2017393444520345981).
- **Estado confirmado:** `SCHEDULED_PENDING`. Não afirmar `PUBLISHED` até confirmar retorno do publicador após 11:15.
- **Próxima ação:** verificar status pós-horário; obter URL pública se publicada; medir sessões UTM e cadastro em 7 dias; confirmar integração Instagram para destravar mídias anteriores. Caso a publicação falhe, capturar erro e reavaliar canal.
- **Precisa da conta principal?** **SIM**, para conectar o Instagram e validar atribuição de cadastro/primeiro evento; **NÃO** para o agendamento realizado.
- **Escopo:** nenhum código, VPS, deploy, claim ou evento fictício.
