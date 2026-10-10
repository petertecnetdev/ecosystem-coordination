# Worklog — AUX-02 W3 — Direct transport failure isolation

- date: 2026-10-10
- agent: aux-02-w3-integrations
- display_name: Reliability Forge
- priority: P0
- repository: petertecnetdev/api.petertecnet.com.br
- related_issue: #533
- status: blocked

## Problema confirmado

A API pode persistir uma mensagem Direct e depois retornar HTTP 500 se o transporte de broadcast falhar. O caminho posterior também permite que falhas em `MessageEngagementService::markResponse()`, `queueMessage()` ou `AppNotificationService::sendToUser()` interrompam a resposta depois da persistência.

## Evidência

- Issue #533: https://github.com/petertecnetdev/api.petertecnet.com.br/issues/533
- `MessagingService::send()` persiste a mensagem antes de chamar `deliverMessage()`.
- `MessagingService::broadcast()` despacha `MessagingRealtimeEvent` sem isolamento de exceções.
- `deliverMessage()` chama os serviços de engajamento e notificação sem captura de falhas.
- `tests/Feature/MessagingEmailNotificationTest.php::test_notification_failure_never_rolls_back_direct_message()` atualmente espera a exceção de notificação, validando o comportamento indesejado.
- SHA da main e da branch de trabalho: `14447fa8c6d038e8ce007e4ebfab0dfd5dea97f1`; comparação GitHub: `identical`, zero commits à frente.

## Impacto

P0 de confiabilidade do Direct: o cliente pode mostrar falha embora a mensagem esteja persistida, incentivar repetição e impedir o disparo de etapas de engajamento/e-mail.

## Trabalho realizado

- Releitura de `COMMANDS.md`, `PROTOCOL.md`, `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, assignment AUX-02/W3 e claim ativo.
- Revalidação do issue #533, código atual, teste de regressão e PR #537.
- Tentativa de alteração mínima na branch existente: capturar e registrar falhas de broadcast, engajamento e notificação pós-persistência; adaptar o teste para exigir retorno da mensagem persistida.
- A operação `update_file` da API foi bloqueada por verificações de segurança antes de qualquer arquivo funcional ser alterado.
- Claim ativo atualizado para `blocked` no commit de coordenação `96f0bfd8a8fd7f5ab60c434815e37a8196ac08f5`.

## Arquivos funcionais alterados

Nenhum.

## Testes

Nenhum teste foi executado, pois nenhuma mudança funcional foi gravada. A execução anterior da PR #537 não é evidência de que esta correção passa.

## Git

- API branch: `agent/aux02-w3/direct-broadcast-failure-isolation`
- API base/head: `14447fa8c6d038e8ce007e4ebfab0dfd5dea97f1` (idênticos)
- API commit/PR: nenhum
- Coordination commit: `96f0bfd8a8fd7f5ab60c434815e37a8196ac08f5`

## Próxima ação

W00 deve viabilizar um caminho autorizado para escrever a correção e o teste na branch já existente, ou aplicar a correção pelo fluxo de desenvolvimento autorizado. Não criar outro claim para o mesmo escopo. Após a escrita: executar o teste focado `MessagingEmailNotificationTest`, validar a falha simulada de broadcast e notificação, e abrir PR somente com diff e checks revisados.
