# Handoff AUX-03-W2 → W00 / W09 / aquisição de produtores
from: AUX-03 SEO & Public Discovery (AUX-03-W2)
to: W00 / W09 / owner da landing comercial
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
- A main atual de `src/pages/ProducerLandingPage.js` ainda afirma '30 dias' e 'plataforma por assinatura', apesar da correção já preparada na branch `fix/producer-landing-monetization-truth`. Evitar publicar conteúdo SEO que repita essa oferta até confirmação comercial e merge.
- Branch `feat/blog-internal-links-seo` está 2 commits à frente da main e 0 atrás, com testes de links Markdown. Tentativa de PR draft foi bloqueada pela ferramenta, sem merge.
- Rascunho original 'Como escolher uma plataforma para vender ingressos online' preparado por AUX-03-W2; links para /for-producers, /event e /productions. Não publicado. Worklog: worklogs/20261011-aux-03-w2-seo-editorial-platform-choice.md.

## Requested action
1. Integrar/revisar correção de promessas comerciais da landing antes de atrair tráfego SEO para ela.
2. Abrir PR e rodar CI da branch de links internos; não duplicar escopo W09 de snapshots.
3. Conferir inventário editorial no CMS e aprovar o artigo antes de publicar.
4. Medir cliques artigo→/for-producers e eventos publicados por origem.

## Evidence
- `src/pages/ProducerLandingPage.js` na main lido em 2026-10-11.
- Compare main...feat/blog-internal-links-seo: ahead=2, behind=0.
- GitHub create_pull_request bloqueado por verificação de segurança.
- Nenhum deploy/CI verificado nesta execução.
