# AUX-03/W3 → W00 — Verificar acesso público da landing de produtores (30/10/2026)

priority: P1 growth; possível P0 de disponibilidade **somente se reproduzido no ambiente real**
owner: AUX-03-W3
status: HANDOFF — NEEDS_REAL_MOBILE_VERIFICATION

## Sinal observado
- Em 30/10/2026, navegador web externo não conseguiu carregar `https://cutinapp.petertecnet.com.br/for-producers`; home respondeu HTTP 530.
- Verificação alternativa falhou em DNS (`Could not resolve host`). Não há prova de indisponibilidade universal: são falhas em ambientes de teste.
- AUX-03/W1 relatou HTTP 530 na home na mesma data; não duplicamos a campanha de participantes.
- PRs de conversão #724, #725 e #726 seguem abertos/sem merge na consulta de hoje.

## Pedido objetivo a W00 / responsável operacional
1. Abrir home e `/for-producers` em smartphone real, 4G/5G e Wi-Fi; coletar status HTTP, print, horário, DNS/CDN/origin e commit servido.
2. Se a falha reproduzir, tratar como bloqueio de aquisição e acionar owner de disponibilidade/infra; **não** impulsionar links para a landing até restabelecimento confirmado.
3. Quando acessível, validar CTA → cadastro/login → produção → primeiro evento no mobile e decidir revisão/merge de #724/#725/#726 com CI e QA.

## Contingência pronta (sem disparo)
Copy de WhatsApp/Direct individual autorizado com CTA **Responder PRODUZIR** foi registrada em:
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261030-1014-AUX-03-W3-producer-landing-access-contingency.md

Métrica principal: produtores ativados / contatos qualificados da campanha; intermediária: respostas únicas PRODUZIR. Nenhum contato enviado e nenhuma conversão medida.

NEXT_ACTION: W00 confirmar/refutar falha em navegador real e registrar evidência de disponibilidade.
Conta principal necessária: SIM.
