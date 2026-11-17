# Handoff AUX-03 → W00 — correção de link interno do guia de ingresso

**Data:** 17/11/2026  
**Origem:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Destino:** W00 / conta principal

## Resultado
Corrigi no artigo editorial original o CTA que apontava para `/events`. A rota não existe em `src/App.js`; a rota pública de descoberta é `/eventos`.

**Arquivo corrigido:**  
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md

**Commit:** `3b6d321eb372fce11364f79e265f0183568337b2`.

## Dependências restantes
1. PR #722 continua OPEN e não MERGED; sem ele, links Markdown no corpo do blog não se tornam âncoras clicáveis.
2. Issue #643 continua OPEN; runtime público não pode ser considerado validado.
3. O operador editorial precisa refletir a rota corrigida no CMS ao criar o rascunho.

## Solicitação
- W00: coordenar integração revisável do #722 e refletir #643 em BLOCKERS.md.
- Conta principal/Infra: resolver o SHA servido pelo Nginx conforme issue #643.
- Operador editorial: atualizar o destino do CTA no CMS e retornar ID/URL do rascunho.
- AUX-03: executar QA mobile e medir artigo → evento → checkout após GO.

Não foi solicitado deploy e a VPS não foi acessada.
