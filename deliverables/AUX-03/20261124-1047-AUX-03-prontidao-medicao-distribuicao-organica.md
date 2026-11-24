# AUX-03 — Prontidão de medição e distribuição orgânica

**Data:** 24/11/2026 10:47 BRT  
**Objetivo:** tornar mensurável a aquisição orgânica da Cutinapp antes de ampliar o volume de conteúdo e campanhas.  
**Área:** distribuição orgânica, SEO, blog, Instagram, aquisição de produtores e conversão.  
**Estado:** DIAGNOSTIC_CONFIRMED — UTM_STANDARD_READY — CONNECTIONS_PENDING — NO_PUBLICATION.

## 1. Confirmado

### Coordenação e ownership
- Foram consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, os worklogs recentes e os claims AUX-03 ativos/concluídos.
- `CURRENT_STATE.md` ainda contém consolidação antiga; `PRIORITIES.md` registra alocação de 30/10. `BLOCKERS.md` não espelha a issue #643.
- A issue #643 permanece OPEN: o Nginx público serve um SHA antigo, diferente do release validado no filesystem. Não há GO de runtime.
- PR #722 (links editoriais), #724 (oferta da landing), #726 (CTA de primeiro evento) e #727 (SEO da landing) continuam abertos; #727 está em Draft e depende de #724 ou do mesmo release.
- Issue #637 permanece aberta para persistência da atribuição orgânica. Esta entrega não cria implementação paralela nem altera seu ownership.
- O worklog de 23/11 sobre sequência de ativação do primeiro evento já definiu mensagens D+1/D+2/D+4; não foi repetido.

### Metricool — marca Cutinapp (brand 7119630)
- Configuração da marca informa `networksData` apenas com `gbpData`; Instagram não aparece conectado ao Metricool.
- Agenda consultada para 24–30/11/2026: nenhum post agendado.
- Relatório Website de 01–24/11 retornou pageViews 0.0, visits 0.0, visitors 0.0 e posts 0.0. As tabelas de posts, páginas e fontes retornaram vazias.
- Relatório GBP no mesmo período retornou valores 0.0 para avaliações, visualizações de posts, alcance e cliques.
- Esses resultados demonstram ausência de dados úteis nessa integração/período; não provam que o site não recebeu visitas nem substituem GA4 ou Search Console.

### Descoberta pública
- A rota `/for-producers` não pôde ser aberta pela ferramenta web.
- As buscas realizadas não retornaram páginas indexadas do domínio Cutinapp.
- Não foi possível verificar uma página de evento publicada da Cutinapp nesta rodada. Nenhum evento externo foi apresentado como se fosse da plataforma.

## 2. Hipótese

O gargalo imediato de crescimento não é falta de novas pautas. É a combinação de runtime público sem GO, landing/links editoriais ainda não integrados e ausência de dados de distribuição/website utilizáveis no Metricool. Continuar aumentando o estoque de artigos antes de resolver esses gates tende a ampliar conteúdo não distribuído e sem mensuração.

Esta é uma hipótese operacional; não há dados de tráfego ou conversão suficientes para quantificar o impacto.

## 3. Entregável concreto — padrão de UTMs para distribuição

Usar UTMs somente em links externos de campanhas e distribuição. Não adicionar UTMs a links internos do site e não etiquetar visitas do Google orgânico manualmente.

### Instagram — link da bio
```
?utm_source=instagram&utm_medium=social&utm_campaign=aux03_organic_202611&utm_content=bio
```

### Instagram — conteúdo específico
```
?utm_source=instagram&utm_medium=social&utm_campaign=aux03_organic_202611&utm_content=carousel_[slug]
?utm_source=instagram&utm_medium=social&utm_campaign=aux03_organic_202611&utm_content=reel_[slug]
?utm_source=instagram&utm_medium=social&utm_campaign=aux03_organic_202611&utm_content=story_[slug]
```

### Compartilhamento por produtor/parceiro
```
?utm_source=producer_partner&utm_medium=referral&utm_campaign=aux03_organic_202611&utm_content=[partner_slug]
```

### Regras
- Valores em minúsculas, sem espaços, com `snake_case`.
- Não incluir nome, e-mail, telefone ou outro dado pessoal em UTMs.
- Não usar `utm_term` em campanhas orgânicas.
- Google orgânico deve ser medido por Search Console + GA4 (source/medium e landing page), sem UTM artificial.
- A persistência first-touch deve continuar no escopo da issue #637; este padrão apenas identifica links distribuídos.

## 4. Métricas e definição operacional

| Etapa | Fonte | Métrica |
|---|---|---|
| Descoberta Google | Search Console | impressões, cliques, CTR e consulta por URL |
| Visita | GA4 | sessões orgânicas, landing page e sessões engajadas |
| Interesse | GA4/eventos do produto | clique no CTA da landing/artigo |
| Cadastro | produto | cadastro de produtor concluído |
| Ativação | produto | produção criada e primeiro evento criado |
| Resultado | produto | primeiro evento publicado em até 7 dias, por origem |

`producer_production_created` é citado no PR #724, mas sua emissão em runtime não foi verificada nesta execução. Os demais eventos específicos devem ser tratados como métricas propostas até confirmação no produto. Não criar um segundo sistema de atribuição: coordenar com a issue #637.

**Métrica principal:** produtores atribuídos à origem orgânica que publicam o primeiro evento em até 7 dias.  
**Baseline:** N/D — sem acesso a Search Console/GA4 e sem telemetria de conversão verificada.

## 5. Canal e CTA

- **Canais:** Google orgânico, Instagram, compartilhamentos de produtores/parceiros.
- **CTA:** “Cadastrar minha produção” em `/for-producers`, somente após integração de #724/#727 e runtime GO.
- **CTA editorial:** “Conheça a Cutinapp para produtores”, somente quando os links internos de #722 estiverem integrados e testados.
- Não agendar ou publicar conteúdo sem conta social conectada, mídia aprovada e URL pública validada.

## 6. Próxima ação priorizada

1. **Conta principal/W00:** resolver a issue #643 e confirmar o SHA servido por HTTP/HTTPS.
2. **Conta principal/W00:** coordenar #724 + #727 no mesmo release; revisar #722 e #726 sem sobrescrever ownership.
3. **Conta principal:** conectar a conta profissional do Instagram ao Metricool e confirmar permissões.
4. **Conta principal:** conectar GA4/website ao Metricool e disponibilizar Search Console para leitura.
5. **AUX-03:** após GO, distribuir primeiro o conteúdo já produzido, usando o padrão UTM acima; medir cliques e primeiro evento publicado antes de abrir novo cluster editorial.

## 7. Evidências

- Issue #643 — runtime/Nginx: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Issue #637 — atribuição first-touch: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/637
- PR #722 — links editoriais: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #724 — oferta da landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #726 — primeiro evento: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727 — SEO da landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Metricool brand: Cutinapp, ID 7119630; fuso America/Sao_Paulo.
- Consulta de agenda Metricool: 24–30/11/2026, vazia.
- Relatório Metricool Website e GBP: 01–24/11/2026, valores zero/sem linhas de detalhamento.

## 8. Precisa da conta principal?

**SIM.** Conexão de Instagram, GA4 e Search Console, liberação de runtime e coordenação dos PRs dependem da conta principal/W00.

## Estado final

`DIAGNOSTIC_CONFIRMED — UTM_STANDARD_READY — INSTAGRAM_NOT_CONNECTED — WEBSITE_ANALYTICS_ZERO_OR_UNAVAILABLE — SCHEDULE_EMPTY — RUNTIME_NOT_GO — NOT_PUBLISHED — NO_PRODUCT_CODE_CHANGED — NO_VPS`.
