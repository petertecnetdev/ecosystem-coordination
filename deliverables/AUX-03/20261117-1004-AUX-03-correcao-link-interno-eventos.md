# AUX-03 — Correção de rota interna no guia de ingresso digital

**Data:** 17/11/2026  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Objetivo:** corrigir um destino interno inválido em um ativo editorial já preparado, reduzindo o risco de perder participantes no caminho entre o guia e a descoberta de eventos.

## Confirmado

- O artigo existente `deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md` continha o link `[Explore os eventos publicados na Cutinapp](/events)`.
- A rota `/events` não está declarada no roteador React da `main`.
- `src/App.js` declara `/eventos` para `EventDiscoverySeoPage`, além de `/eventos/:citySlug` e variações por categoria/período.
- A rota singular `/event` também existe, mas abre outra experiência; para descoberta pública, o destino correto é `/eventos`.
- O PR #722, que converte links Markdown em links clicáveis no corpo do blog, continua aberto e não integrado. A correção do destino não elimina essa dependência de renderização.

## Oportunidade

O guia de ingresso digital é um ativo voltado a participantes. O CTA final deve levar a uma rota pública de descoberta de eventos, e não a uma rota inexistente que cai no fallback da aplicação.

## Trabalho realizado

1. Consultei o artigo original e conferi o destino do CTA.
2. Consultei as definições de rota em `src/App.js` na `main`.
3. Confirmei que `/eventos` é a rota de descoberta pública.
4. Corrigi o link no arquivo editorial original, sem duplicar o artigo.
5. Preservei o rótulo e a intenção do CTA.
6. Não alterei código do produto, não criei branch e não fiz deploy.

## Entregável

- Artigo corrigido: [guia de ingresso digital](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md)
- Arquivo atualizado em `main` do repositório de coordenação.
- Commit: `3b6d321eb372fce11364f79e265f0183568337b2`.

## Canal e CTA

**Canal:** Google Search → guia de ingresso digital → descoberta de eventos.

**CTA:** **Explore os eventos publicados na Cutinapp** → `/eventos`.

## Métrica

- Cliques únicos no CTA do artigo por sessão.
- Sessões que chegam a páginas individuais de evento.
- Inícios de checkout originados do guia, quando a atribuição estiver disponível.

**Baseline:** não disponível; nenhum clique ou conversão foi presumido.

## Limitações

- O PR #722 ainda precisa ser integrado para que links Markdown sejam transformados em âncoras clicáveis na experiência do blog.
- A issue P0 #643 continua sendo gate de runtime público.
- A rota foi confirmada no código, não em produção. Não declarar a jornada pública validada até o SHA servido coincidir com a release aprovada.

## Próxima ação

- W00/conta principal: coordenar #722 e resolver #643.
- Operador editorial: atualizar o rascunho/CMS com a mesma rota quando o artigo for cadastrado; confirmar o URL efetivo.
- AUX-03: após runtime GO, testar o CTA em mobile e medir artigo → evento → checkout.

## Precisa da conta principal

**SIM** — para integrar #722, liberar runtime público e validar a jornada em navegador/produção.
