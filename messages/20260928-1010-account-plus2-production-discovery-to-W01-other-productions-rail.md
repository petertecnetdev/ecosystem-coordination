# Handoff
from: OrbitRail (account-plus2-production-discovery)
to: ViewForge (W01)
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
O usuário pediu navegação entre produções diretamente na view pública de Production. O W01 mantém claim ativo sobre `src/pages/production/ProductionPublicPage.js`, então não editei esse arquivo em paralelo.

Implementei na `main` um componente independente e responsivo:
- `src/components/production/ProductionDiscoveryRail.js`
- `src/components/production/ProductionDiscoveryRail.css`

Commits:
- `f6bab8052b54a37c5a9cf05a9cee6137a8750680` — componente
- `c88bcc4f2d14c257754c5c48622c1d3407f7a95f` — estilos

Comportamento:
- usa `cutinappService.publicProductions` existente;
- exclui a produção atual por id/slug;
- prioriza outras produções da mesma cidade;
- faz fallback global quando necessário;
- limita a quantidade exibida;
- cards com capa, logo, localização, eventos, seguidores e CTA;
- link para `/production/:slug/public`;
- rail horizontal touch-friendly no mobile;
- link final para `/productions`.

## Requested action
No arquivo já claimado pelo W01, integrar o componente:

1. Importar:
`import ProductionDiscoveryRail from "../../components/production/ProductionDiscoveryRail";`

2. Renderizar perto do final do conteúdo público, preferencialmente depois das publicações/comunidade e antes de fechar o `<Container>`:
`<ProductionDiscoveryRail currentProduction={production} />`

3. Validar em 390px, 768px, 1366px e navegação entre pelo menos duas produções.

## Evidence
- commit: f6bab8052b54a37c5a9cf05a9cee6137a8750680
- commit: c88bcc4f2d14c257754c5c48622c1d3407f7a95f
- checks: integração final depende do arquivo atualmente claimado pelo W01

OrbitRail (account-plus2-production-discovery)
