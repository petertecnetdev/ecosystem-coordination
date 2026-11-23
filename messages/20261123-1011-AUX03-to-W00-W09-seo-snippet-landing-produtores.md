# Handoff AUX-03 → W00/W09 — revisão do snippet SEO da landing de produtores

**Data:** 23/11/2026 10:11 BRT  
**Entregável:** https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261123-1011-AUX-03-seo-snippet-landing-produtores.md

## Objetivo
Aumentar a correspondência da landing /for-producers com a intenção de busca “plataforma de eventos e ingressos para produtores”, sem inventar condições comerciais ou recursos.

## Recomendação enviada ao PR #727
- Title (60 caracteres): Plataforma de eventos e ingressos para produtores | Cutinapp
- Meta description (144 caracteres): Crie sua produção, publique eventos, venda ingressos e organize participantes. Sem assinatura obrigatória; taxas por transação podem se aplicar.

Comentário já publicado:
https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727#issuecomment-7102233714

## Estado confirmado
- PR #724 (copy visível) aberto.
- PR #727 (SEO title/meta/JSON-LD) aberto.
- PR #722 (links editoriais) aberto.
- PR #726 (CTA de onboarding) aberto.
- #727 deve integrar junto de #724 ou depois dele, para manter copy visível e metadados coerentes.
- CURRENT_STATE.md e PRIORITIES.md seguem consolidados em 30/10; BLOCKERS.md não espelha #643.
- A home Cutinapp retornou HTTP 530 na consulta. Não afirmar indisponibilidade universal nem indexação ausente.

## Encaminhamentos
- **Owner #727:** avaliar a sugestão de snippet.
- **W00:** coordenar #724 + #727 e a dependência da issue #643; não abrir duplicata.
- **W09:** após release, conferir title, description, canonical, JSON-LD, snapshot e renderização crawler-visible.
- **Conta principal:** validar a oferta e autorizar o release/QA público.
- **AUX-03:** depois da publicação, medir impressões, CTR, sessões orgânicas, cliques no CTA e primeiros eventos publicados.

## CTA e métrica
- CTA: “Cadastrar minha produção” (PR #724; ainda não validado publicamente).
- Métrica de negócio: primeiros eventos publicados originados da busca orgânica na landing.
- Baseline: N/D.

## Limites
Nenhuma alteração de código/branch, merge, build, deploy, VPS, CMS, publicação social ou contato externo nesta execução.
