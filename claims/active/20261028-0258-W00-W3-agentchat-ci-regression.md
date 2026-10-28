# Reserva condicional W00 → W3 — regressão AgentChatGithub no API CI

agent: W3
display_name: W3 — Independence API e CI
repository: petertecnetdev/api.petertecnet.com.br
branch: Independence
status: reservado-condicional-aguardando-aceite-e-runner
started_at: 2026-10-28T02:58:00-03:00
depends_on: ecosystem-coordination#10; ecosystem-coordination#12; API CI #40636582397
files_or_scope:
- tests/Unit/AgentChatGithubServiceTest.php

## Evidência e limite de ownership
- Solicitação do executor W3 na issue #10 comentário 6461456559, com diagnóstico específico da falha `test_it_reads_and_parses_the_shared_chat`.
- No HEAD remoto da API Independence `4fb29b5edc8ce4a27fc815496dab3c6277b5afe4`, blob do teste `336d2e2ea5cfffe5a13aa641629134e16ae34b80`.
- A listagem de 172 claims ativos e a busca nominal não apontaram claim específico para esse teste. Isso NÃO prova ausência de claim genérico ou edição concorrente.
- Esta reserva NÃO transfere automaticamente arquivo que esteja sob ownership de terceiro. Antes de editar, W3 deve confirmar exclusividade por conteúdo de claims relevantes, obter cessão explícita se necessária, conferir HEAD/blob atuais e registrar ACEITE na issue #10. Se houver conflito, não editar e devolver ao W00.
- Serviço `app/Services/AgentChatGithubService.php` explicitamente FORA do escopo, sem autorização para alteração.

## Entrega esperada após desbloqueio
- Corrigir apenas regressão de contrato no teste: diferenciar `write_enabled` (fila `github_actions_sync` autorizada) de `direct_write_enabled` (token direto); confirmar `delivery_mode`, ausência de PUT sem token e fluxo direto com token. Não enfraquecer regras de autorização nem transformar ausência de token em permissão de escrita direta.
- Reproduzir falha antes, executar PHPUnit oficial focal com exit 0 depois, PHP lint e diff check, publicar commit REAL [agent:W3] em português na branch Independence e conferir CI oficial no SHA exato.
- A conexão Remote Desktop Commander atingiu limite mensal de uso nesta rodada (28/10/2026). Não repetir chamadas nem contornar cota ou `OPENAI_SAFETY_CHECKS`. Sem runner de testes isolado e autorizado, registrar bloqueio nominal, não inventar exit 0 nem publicar patch não testado.
- Não tocar W1 financeiro, W2 React, W4 Admin, NP12, /var/www, MySQL/gateways reais, main, merges ou deploys.

## Critério de encerramento
Aceite explícito e ownership confirmado; SHA do commit; arquivos; PHPUnit exit 0; CI no SHA exato; QA/revisão W00. Reserva não equivale a liberação de merge.
