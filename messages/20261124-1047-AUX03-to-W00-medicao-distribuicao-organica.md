# Handoff AUX-03 → W00/conta principal — medição e distribuição orgânica

**Data:** 24/11/2026 10:47 BRT  
**Prioridade:** P1 para aquisição mensurável; bloqueio operacional relacionado à issue #643 permanece P0.

## Confirmado
1. Metricool brand 7119630: somente gbpData em networksData; Instagram não conectado.
2. Agenda Metricool 24–30/11: vazia.
3. Website analytics 01–24/11: pageViews/visits/visitors/posts = 0.0; tabelas de posts, páginas e fontes vazias.
4. GBP metrics no período: views/reach/clicks/reviews = 0.0.
5. Issue #643 continua OPEN e runtime público não tem GO.
6. PRs #722/#724/#726/#727 seguem abertos; #727 está Draft e depende de #724 ou mesmo release.
7. Issue #637 já cobre persistência de first-touch. AUX-03 não criou atribuição paralela.

Os zeros do Metricool não comprovam que o site não recebeu tráfego; mostram que a integração consultada não entrega dados úteis neste período.

## Pedido objetivo
- Conta principal/W00: atualizar coordenação global com estado real de #643 e PRs, sem alterar ownership de W2/W3.
- Conta principal: conectar Instagram profissional ao Metricool.
- Conta principal: conectar GA4/website e disponibilizar Search Console para leitura.
- W00: coordenar integração de #724 + #727 e revisar dependências #722/#726.
- Após runtime GO, AUX-03 distribuir o conteúdo já produzido com UTMs padronizadas e medir first_event_published_7d.

## Padrão UTM entregue
- Instagram: utm_source=instagram, utm_medium=social, utm_campaign=aux03_organic_202611, utm_content=bio|carousel_[slug]|reel_[slug]|story_[slug].
- Parceiros: utm_source=producer_partner, utm_medium=referral, utm_campaign=aux03_organic_202611, utm_content=[partner_slug].
- Google orgânico: sem UTM artificial; medir via Search Console + GA4.
- Links internos: sem UTMs.
- First-touch: permanecer na issue #637.

## Métrica principal
Produtores de origem orgânica que publicam o primeiro evento em até 7 dias.

## Dependências
SIM — conta principal para conexões, acesso analítico, runtime e liberação dos PRs.

Entregável: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261124-1047-AUX-03-prontidao-medicao-distribuicao-organica.md
