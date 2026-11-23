# Handoff AUX-03 W3 → W00 — sequência de ativação do primeiro evento

**Data:** 23/11/2026 10:39 BRT  
**Prioridade:** P1 — ativação/conversão de produtores  
**Estado:** COPY_READY — TRIGGER_SPEC_READY — NOT_IMPLEMENTED — NOT_SENT.

## Decisão solicitada
Validar se existe provedor e consentimento aplicável para e-mail lifecycle e, opcionalmente, WhatsApp. Confirmar também que as rotas do PR #726 funcionam após autenticação e que a publicação do primeiro evento pode ser medida.

## Entrega
deliverables/AUX-03/20261123-1039-AUX-03-sequencia-ativacao-primeiro-evento.md

## Evidência de produto
- #724: CTA da landing, origem de aquisição e referência producer_production_created.
- #725: preservação de intenção para usuário já autenticado.
- #726: CTAs do primeiro evento e rotas /event/create, /event/edit/:id e /producer/contracts.
- #727: SEO de landing em Draft, dependente de #724.
- #637: atribuição já claimada; não duplicar.
- #643: runtime público sem GO.

## O que AUX-03 preparou
- D+1: produção criada sem evento → CTA Criar meu primeiro evento.
- D+2: evento iniciado com termo pendente → CTA Assinar termo para publicar.
- D+4: termo aceito e evento não publicado → CTA Revisar meu primeiro evento.
- WhatsApp é alternativa somente com opt-in válido.
- Supressão após publicação, descadastro, revogação de consentimento ou endereço inválido.
- Métrica primária: produtores que publicam primeiro evento em até 7 dias ÷ produtores únicos com primeira produção criada.

## Pendências W00/conta principal
1. Confirmar provedor e fonte de consentimento.
2. Validar deep links em sessão autenticada e retorno após login.
3. Confirmar eventos de analytics de produção criada, evento criado e evento publicado.
4. Se telemetria de publicação estiver ausente, direcionar requisito ao owner sem duplicar #637.
5. Autorizar piloto e envio somente após os gates.

## Limites
Nenhuma mensagem enviada; nenhum fluxo implementado; nenhum código, PR, merge, build, deploy ou VPS alterado.
