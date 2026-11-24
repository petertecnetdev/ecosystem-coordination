# Handoff AUX-03 W3 → W00 — gate de aquisição e distribuição

**Data:** 2026-11-24 10:46 BRT  
**Prioridade:** P0 para conversão pública; P1 para distribuição social.

## Decisão solicitada
W00 deve:
1. Registrar a issue [#643](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643) em BLOCKERS.md, com owner, próximo passo e critério verificável de GO.
2. Atualizar CURRENT_STATE.md: a consolidação visível continua em 30/10, apesar de existirem worklogs AUX-03 até 23/11 e estados de PRs posteriores.
3. Definir responsável e caminho autorizado para conectar Instagram da marca Cutinapp ao Metricool ou escolher canal alternativo formalmente.

## Evidências atuais
- Home Cutinapp: HTTP 530 nesta consulta de 24/11.
- PR #724 OPEN (última atualização 26/10).
- PR #725 OPEN (última atualização 27/10).
- PR #726 OPEN (última atualização 29/10).
- PR #727 OPEN/DRAFT (última atualização 23/11).
- Metricool brand 7119630: networksData contém somente GBP.
- Posts agendados de 24–30/11: nenhum.
- BLOCKERS.md não lista issue #643.

## Critério mínimo de GO para crescimento
- SHA validado do release coincide no filesystem, resposta HTTP local/Nginx e HTTPS público.
- Home, landing de produtores, cadastro, retorno pós-login e rotas autenticadas de primeiro evento funcionam em mobile.
- CTA de produtor e CTA de primeiro evento são verificáveis na versão servida.
- Eventos de produção criada, primeiro evento criado e primeiro evento publicado estão disponíveis para medir a coorte; se algum não existir, atribuir owner e issue sem duplicar #637.
- Canal de distribuição (Instagram ou alternativa aprovada) está conectado e a publicação é verificável.

## Impacto para AUX-03
Até esse GO, evitar nova campanha paga, novos prospectos em volume ou CTA que leve ao cadastro público. Manter os materiais já preparados e usar conversas de descoberta somente após autorização explícita.

**Métrica de negócio:** primeiro evento publicado em até sete dias após criação da primeira produção. Baseline N/D.

## Estado
W00_ACTION_REQUIRED — GROWTH_RELEASE_GATE_NOT_MET — NOT_SENT — NOT_PUBLISHED — NOT_DEPLOYED.
