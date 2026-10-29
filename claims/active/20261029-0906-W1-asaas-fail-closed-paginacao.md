# Claim W1 — Asaas GET conclusivo e paginação segura (P0)

agent: W1
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: working
started_at: 2026-10-29T09:06:00-03:00
issue: petertecnetdev/ecosystem-coordination#10
related_pr: petertecnetdev/api.petertecnet.com.br#546
handoff_offer: messages/20261029-0858-W00-to-W1-W2-atribuicao-condicional-p0.md
scope: Falhar fechado quando GET Asaas não comprova inexistência/unicidade; paginação conclusiva, sem POST após falha.
files_or_scope:
- app/Services/AsaasPaymentService.php
- tests/Unit/AsaasPaymentServiceTest.php

## Pré-condições verificadas
- W00 ofereceu atribuição condicional, não cessão de terceiro, no commit f6f15a439ba8c192c779b4904cf8424cd7277204.
- HEAD API Independence: aed56b3c05252e6403ab67ca70dac3ee8a21b0d7.
- Blob do serviço: e28c38f406d72399b73dd970a57c27b849bdf01a.
- Blob do teste: 3d547973e43de2f00a14d8200724b9be4515b6da.
- Revisados diretório de claims ativos (177 entradas), claims financeiros Ledger/Pulse/Validator, claim W1 anterior e handoffs W00; não foi identificado claim ativo específico para esses dois arquivos. Histórico Git não equivale a reserva. Sem edição concorrente conhecida na verificação.
- ACEITE expresso W1 será registrado na issue #10 antes de alterar arquivos.

## Critérios
- GET /customers ou /payments com falha, timeout, JSON inválido, metadados ausentes/ambíguos: zero POST subsequente.
- Paginação hasMore percorrida até conclusão, com limite máximo e rejeição de duplicidade/resultado malformado.
- Consulta comprovadamente vazia ainda permite criação legítima; cobrança já existente é reutilizada de forma idempotente.
- Testes HTTP::fake e CI no HEAD final; sem tocar retry W1, EventPass, ledger, settlement, webhook, fixtures W01 ou produção.
- Não ampliar escopo sem novo aceite; não realizar merge/deploy.

Próxima ação: W1 registrar aceite na issue #10, implementar exclusivamente os dois arquivos e verificar CI no SHA final.
