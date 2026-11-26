# AUX-03 — kit de compartilhamento de eventos para participantes

**Data:** 2026-11-26 10:14 BRT  
**Objetivo:** aumentar a distribuição orgânica de páginas públicas de eventos da Cutinapp por meio do compartilhamento feito por participantes e produtores.

## Área
Aquisição de participantes, compartilhamento de páginas públicas, distribuição social, WhatsApp, Instagram Stories e conversão de páginas de evento.

## Oportunidade
As campanhas AUX-03 anteriores priorizaram aquisição e ativação de produtores. Esta entrega abre uma frente complementar: transformar cada evento publicado em um ponto de distribuição, permitindo que produtor e participante compartilhem o mesmo endereço público com uma chamada adequada ao canal.

### Confirmado
- A issue #646 — Views distintas por entidade + alinhamento View/Create/Edit — mantém Evento como prioridade visual e exige página pública legível em mobile, com hierarquia de título, data, local, produção, ingressos/itens e ações.
- A issue #643 — Nginx serve release antigo — continua aberta. Em 26/11, a home retornou HTTP 530 nesta consulta; /for-producers e /events não foram acessíveis pela ferramenta. Isso não prova indisponibilidade universal, mas não permite declarar o caminho público validado.
- Metricool brand Cutinapp (ID 7119630) retornou apenas gbpData em networksData; Instagram não consta como rede conectada nesse retorno.
- A agenda Metricool de 26/11 a 03/12/2026 retornou vazia.
- A issue #637 — atribuição orgânica até trial/ativação — está CLAIMED por cutinapp-growth-seo. Esta entrega não cria tracking paralelo nem altera a issue.

### Hipótese
Se o compartilhamento da página do evento tiver uma mensagem clara, curta e adequada ao estado real do evento, participantes e produtores poderão distribuir o link com menos esforço e gerar visitas qualificadas. Não há baseline de cliques, compartilhamentos ou conversões para comprovar o efeito.

## Trabalho realizado
1. Consultei CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md do repositório de coordenação.
2. Consultei o último entregável, worklog, claim e handoff AUX-03 de 25/11 para evitar repetir FAQ comercial e copy da landing.
3. Revalidei issues de crescimento #636, #637, #643, #646 e #728 e PRs abertos #722, #724–#727.
4. Verifiquei a marca Cutinapp e a agenda atual no Metricool.
5. Preparei mensagens reutilizáveis com campos variáveis e regras para não anunciar ingressos/inscrições que não estejam realmente disponíveis.

## Entregável — copy pronta para compartilhamento

### 1. WhatsApp — participante convidando outra pessoa
> Encontrei este evento na Cutinapp e lembrei de você.
>
> **[NOME DO EVENTO]**  
> [DATA] · [HORÁRIO]  
> [LOCAL]
>
> Dá uma olhada nos detalhes e nas orientações de entrada:
> [LINK PÚBLICO DO EVENTO]
>
> Se animar, vamos juntos?

Uso: preencher data, horário e local somente a partir da página publicada. Se algum dado não estiver confirmado, remover a linha em vez de estimar.

### 2. Instagram Story — compartilhamento do evento
Texto na tela:
> TEM EVENTO NOVO PARA CONHECER
>
> [NOME DO EVENTO]  
> [DATA] · [CIDADE]
>
> Veja os detalhes na Cutinapp.

Sticker/link: [LINK PÚBLICO DO EVENTO]  
CTA: VER EVENTO

### 3. Instagram — legenda para o produtor
> Seu evento também merece circular.
>
> [NOME DO EVENTO] acontece em [DATA], em [LOCAL].
>
> Consulte a página pública para conferir a programação, as informações de acesso e as opções disponíveis.
>
> Compartilhe com quem não pode ficar de fora.
>
> **Veja o evento na Cutinapp:** [LINK PÚBLICO DO EVENTO]
>
> Descubra eventos. Compre ingressos. Viva experiências.

Regra: só mencionar compra de ingressos se a página confirmar que há ingressos disponíveis. Para evento gratuito com inscrição, trocar “opções disponíveis” por “orientações de inscrição”. Para evento sem venda/inscrição, manter apenas “detalhes e orientações de entrada”.

### 4. Mensagem para o produtor enviar à sua base
> A página oficial de [NOME DO EVENTO] já está disponível na Cutinapp.
>
> Envie este link para quem vai participar e consulte por lá os detalhes e as orientações atualizadas:
> [LINK PÚBLICO DO EVENTO]
>
> Compartilhe para que mais pessoas encontrem o evento.

Regra: usar “já está disponível” apenas depois de confirmar a publicação pública e abrir o link em smartphone sem autenticação.

### 5. CTA conforme o estado real
- Ingressos ativos: CONFERIR INGRESSOS.
- Inscrição gratuita ativa: FAZER INSCRIÇÃO.
- Evento publicado sem venda/inscrição: VER DETALHES DO EVENTO.
- Vendas/inscrições encerradas: VER INFORMAÇÕES DO EVENTO.
- Esgotado: não sugerir lista de espera, nova data ou disponibilidade futura sem recurso confirmado.

## Canal
WhatsApp, Instagram Stories, legenda de Instagram e compartilhamento direto da página pública do evento.

## CTA
Primário: VER EVENTO NA CUTINAPP.  
CTA transacional condicionado: CONFERIR INGRESSOS ou FAZER INSCRIÇÃO, somente quando a página confirmar disponibilidade.

## Métrica principal
Cliques únicos no link público de evento originados por compartilhamento, com conversão secundária em ingresso/inscrição concluída.

- Numerador operacional: cliques únicos atribuíveis a links compartilhados.
- Denominador operacional: compartilhamentos enviados, somente se a plataforma já disponibilizar esse dado.
- Métrica de negócio: ingressos/inscrições concluídos por visitas originadas de compartilhamento.
- Baseline: N/D.

A implementação deve reutilizar a atribuição existente ou em andamento na issue #637; não criar um segundo sistema de UTM/eventos.

## Evidências
- Issue #646 — apresentação pública do evento e mobile.
- Issue #643 — gate de release público.
- Issue #637 — atribuição orgânica.
- Issue #728 — conteúdo integral nos snapshots do blog.
- PR #722 — links editoriais clicáveis.
- Consulta Metricool brand 7119630: somente GBP no retorno de redes; agenda 26/11–03/12 vazia.
- Consulta pública de 26/11: home retornou HTTP 530; /for-producers e /events não acessíveis pela ferramenta.

## Próxima ação
1. W00/conta principal liberar e comprovar GO do runtime público.
2. Após GO, testar uma página real de evento em smartphone, sem login, conferindo conteúdo, CTA e estado de ingresso/inscrição.
3. Aplicar este kit a um evento efetivamente publicado e medir cliques/ingressos/inscrições.
4. Conectar Instagram ao Metricool ou definir publicação manual autorizada; anexar mídia oficial antes de agendar post.

## Precisa da conta principal
SIM. Precisa da liberação do runtime público e da validação de uma página real de evento. Também precisa de acesso de distribuição/mídia para agendar Instagram. Nenhum contato externo, publicação ou agendamento foi executado nesta entrega.

## Estado
SHARE_COPY_READY — EVENT_PAGE_RUNTIME_NOT_VERIFIED — INSTAGRAM_NOT_CONNECTED_IN_METRICOOL_RESPONSE — NO_POSTS_SCHEDULED — NOT_PUBLISHED — NOT_DEPLOYED.
