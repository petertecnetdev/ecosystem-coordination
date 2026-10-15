# Plano horário — Independence + Administrator (Cutinapp)
Data da decisão: 2026-10-14 | Coordenador: W00 | Estado: ATIVO
Origem: solicitação direta do proprietário para **2 executores por projeto e W00 gerente de ambos**.
Issues: [Independence #10](https://github.com/petertecnetdev/ecosystem-coordination/issues/10) · [Administrator #12](https://github.com/petertecnetdev/ecosystem-coordination/issues/12)

## Escala exata — America/Sao_Paulo
| Horário por hora | Worker | Projeto | Responsabilidade e área exclusiva |
| --- | --- | --- | --- |
| :06 | W1 | Independence | API Laravel: modelagem/migrations, endpoints de reivindicação, gates de comércio autoritativos e testes correspondentes. Não editar arquivos com claim W2 antes do handoff. |
| :18 | W2 | Administrator | API central: auditoria/implementação isolada de RBAC, papéis, colaboradores, delegação, revogação e testes tenant. Primeiro transferir claim anterior da Independence via handoff a W00/W1. |
| :30 | W3 | Independence | React: ficha pública, formulário/reivindicação, mensagens, SEO, acessibilidade e integrações frontend da Independence, limitado ao seu claim/handoff. |
| :42 | W4 | Administrator | Frontend administração de colaboradores, papéis e matriz de permissões da Cutinapp; contratos e testes de UI; migrar sua função anterior de QA independente para revisão gerida pelo W00. |
| :54 | W00 | Gestão de ambos | Verificar commits/tests/claims/bloqueios de :06/:18/:30/:42, planejar próximo lote de tarefas **antes da próxima rodada**, recalcular trabalho restante e horizonte, aceitar/reabrir entregas e atualizar issues/assignments; manter review independente. |

## Regras de branches e releases
- Nenhuma branch nova durante Independence. Ambos os projetos podem desenvolver **somente** na branch compartilhada **existente** `Independence`, nos repositórios Cutinapp/API que já a possuem. Não editar `main` dos repositórios de código, nem branches auxiliares, nem criar `administrator` em paralelo.
- Administrator no ciclo atual: **código incremental não ativado em produção**, priorizar serviço/testes e UI isolada sem alterar permissões efetivas nem registrar rotas expostas até validação. Qualquer alteração que possa conceder poder novo, mudar comportamento de rotas ou alterar banco deve possuir feature flag segura/desligada por padrão, teste de isolamento, revisão do W00 e decisão de gate. Sem flag confiável, entregar auditoria/testes/serviço sem conexão a runtime.
- Ao fechar Independence, W00 identifica commits Administrator no HEAD compartilhado. **Não declarar Independence concluída** com código Administrator inseguro ou rotas parcialmente conectadas. Garantir que merge/CI/deploy não ativem nada do Administrator. Após fechamento e exclusão da Independence, continuar Administrator em `funcionalidade/administracao-cutinapp` criada da `main`; não duplicar commits já integrados.
- Respeitar claims por caminhos e contratos; W1 não sobrescrever arquivos de W2 sem handoff explícito. W3 e W4 não editar simultaneamente navbar/auth/context/admin root sem autorização.
- P0 de segurança da API #544: antes de autorizar poderes de colaborador, verificar escopo, não elevar ao root, negar cross-app, invalidar cache em revogação.
- Sem deploy/merge sem autorização, CI e revisão; sem force-push/reset-hard/clean/contornos de safety.

## Primeiro ciclo executável, não só diagnóstico
- **W1 :06 (Independence)**: verificar branch/main, claims, contratos da API e CI; implementar 1 fatia verificável de schema/migration ou endpoint de reivindicação com teste, sem checkout liberado para fichas não verificadas; commit em português na `Independence` se seguro.
- **W2 :18 (Administrator)**: registrar handoff do antigo claim de Request/ReviewPolicy da Independence para W00/W1. Mapear `ApplicationAdminService`, roles, grants, endpoints e issue API #544; escolher um teste de isolamento ou 1 serviço RBAC **não exposto**, executar teste e fazer commit seguro na `Independence` da API quando houver patch verificado.
- **W3 :30 (Independence)**: verificar estado da UI dos eventos/produções e claim existente; entregar e testar uma fatia de painel de ficha não verificada / contrato de reivindicação ou hardening do CTA sem confiar no frontend; commit seguro e handoff contrato com W1.
- **W4 :42 (Administrator)**: transferir para W00 a revisão independente da Independence. Auditar UI admin atual + autoridade via API (PR frontend #714), criar testes/regra de menu de equipe e/ou componente isolado de `Equipe e permissões` em arquivos novos, sem ativar acessos inexistentes; validar Jest/build e commit seguro na `Independence` do frontend.

## Ciclo de gestão :54 — obrigatório
1. Conferir HEAD e commits desde o ciclo anterior **por worker** (SHA e arquivos), testes executados e exit codes, notas e blockers. Commit sem testes não é tarefa concluída; ausência de commit exige motivo e próximo patch.
2. Conferir claim por arquivo e risco de conflito; fechar/transferir claims antigos W2/W4; atualizar 4 *tarefas da próxima hora* com ação pequena, testável, critérios de aceite e dependências. Preferir 1 fatia por worker, não 5 metas vagas.
3. Atribuir estimativa de esforço por fatia em **ciclos efetivos de worker**, não por tamanho em linhas; confrontar estimado x realizado depois de cada execução. Medir throughput real de itens aceitos (não simplesmente commits).
4. Estimar por projeto `T_min = max(caminho_critico, unidades_restantes/capacidade_efetiva)`, com capacidade e disponibilidade observadas, bloqueios, integração, revisão e CI. Manter intervalo de conclusão `ETA_min–ETA_max`, confiança e hipóteses; se não houver medição suficiente, `SEM PREVISÃO CONFIÁVEL (baseline coletando)`, nunca inventar data.
5. Publicar a cada hora nos issues #10/#12 e/ou no arquivo de status: plano vs realizado, commits, falhas/tests, tarefas aceitas e restantes, throughput por worker, ETA revisada, impedimentos e próximos 4 objetivos. Se zero execução, registrar zero e corrigir a causa; não alegar progresso por texto.
6. Atualizar prompts/assignments dos workers **somente** se autorizado/disponível; na indisponibilidade do acesso às automações, publicar atribuições neste repositório que todos leem a cada chamada.
7. W00 não faz trabalho de implementação nas áreas dos quatro workers; sua responsabilidade é gestão, revisão independente, integração segura, branches e desbloqueio técnico/operacional.

## Estado inicial medido (não estimativa de entrega)
- 2026-10-14: backend Independence possui bases parciais e ainda faltam migrations, rotas/controllers, aprovação humana e gates financeiros. API/produção não verificada; frente de segurança P0.
- API #544 aberta para rotas legadas que não respeitam administração por app; API PR #543 e frontend PR #714 registram testes/ajustes que devem ser reaproveitados.
- **ETA inicial:** não mensurável antes de registrar pelo menos duas rodadas de execução com testes/revisão dos itens, e decompor dependências.
- **Estado das automações:** verificação de habilitação e prompts pelo W00 a cada ciclo. Não presumir que compromisso escrito seja execução automática se uma tarefa estiver desabilitada ou sem permissão.

## Modelo de reporte horário
```text
CICLO (America/Sao_Paulo): YYYY-MM-DD HH:54
PROJETO INDEPENDENCE: feitos X/Y | testados X/Y | pendentes P0 N | ETA intervalo ou SEM PREVISÃO CONFIÁVEL
PROJETO ADMINISTRATOR: feitos X/Y | testados X/Y | pendentes P0 N | ETA intervalo ou SEM PREVISÃO CONFIÁVEL
W1: objetivo -> SHA/testes -> status -> próximo passo -> tempo estimado vs observado
W2: objetivo -> SHA/testes -> status -> próximo passo -> tempo estimado vs observado
W3: objetivo -> SHA/testes -> status -> próximo passo -> tempo estimado vs observado
W4: objetivo -> SHA/testes -> status -> próximo passo -> tempo estimado vs observado
CONFLITOS/CLAIMS: ...
GATES: CI, auth/tenant, checkout, deploy, merge
PLANO PRÓXIMA HORA: 4 entregas únicas com critérios de aceite
```

## Demanda incorporada — catálogo independente (issue #13)
- O pedido de pesquisar e cadastrar continuamente produtoras e eventos foi **incluído na Independence #10**; o primeiro lote e fontes estão em [#13](https://github.com/petertecnetdev/ecosystem-coordination/issues/13): 28 produtoras e 4 eventos candidatos. **Zero cadastros confirmados desse lote.**
- **W00 (:54):** acompanhar #13 junto a #10, conferir as condições de curadoria/ownership, atribuir descoberta e validação de novas fontes à capacidade disponível que não conflite com W1/W3, registrar números por rodada e só liberar ingestão real após testes dos gates. Não criar nova branch nem automação adicional; acompanhar no ciclo já existente.
- **W1 (:06):** incluir no contrato da Independence o registro de fontes, propriedade não reivindicada, criador editorial por app, idempotência e bloqueio comercial em fichas não verificadas; preservar migrações e testes existentes.
- **W3 (:30):** assegurar no frontend ficha informativa de curadoria (não implica endosso) e CTA de reivindicação com estado verificável; manter responsividade e testes.
- **Limite de escopo:** catálogo em lote é expansão P1 condicionada ao P0 de segurança/claim; não importar via endpoint padrão que marca o usuário como dono/produtor e publica automaticamente; não publicar ingressos, checkout nem repasses antes da aprovação. Sem deploy implícito.
- **Critério de aceite:** 2–3 registros piloto sem duplicidade nem privilégios indevidos; auditoria, revisão humana, correção/remoção; depois expansão gradual com contadores de pesquisados, verificados, duplicados, cadastrados, reivindicados e aprovados.


## Regra de commits e prestação de contas em português — ordem do proprietário (14/10/2026)
Aplicação obrigatória a **W1, W2, W3, W4 e W00**, em todas as rodadas horárias. Esta seção complementa CMD-005/006/007.

1. **Execução e commit**: W1–W4 devem usar a rodada para desenvolver uma melhoria real de código ou teste automatizado útil e tentar realizar pelo menos **um commit testado por rodada**, na única branch de trabalho autorizada. W00 deve revisar e integrar à `main`, por PR, os commits que estejam prontos e seguros; quando não houver merge seguro, executar a menor correção técnica ou teste de integração que destrave o próximo merge e registrar o resultado. Evitar rodadas limitadas a leitura, relatório ou planejamento.
2. **Idioma obrigatório**: assunto e corpo de **todos os novos commits, PRs, comentários técnicos e relatos** em **português brasileiro**, preservando nomes técnicos necessários. Padrão do assunto: `categoria(escopo): descrever melhoria concreta [agent:W1]` (ajustar identificador para W2, W3, W4 ou W00). Não usar título genérico como “ajustes”, “update” ou “trabalhos”.
3. **Corpo explicativo do commit**: registrar **o que foi feito, por que foi feito, componentes/arquivos alterados, comportamento anterior e novo, testes executados e resultado, limitações/riscos**. A mensagem do commit é parte da entrega, não apenas o SHA.
4. **Comentário no GitHub**: após cada commit, comentar no PR correspondente ou issue do projeto (**Independence #10 / Administrator #12**) em português, com **worker, rodada, link e SHA do commit, resumo do código implementado, testes e resultado, pendências e próxima ação**. Se a integração disponibilizar comentário específico no commit, comentar lá também; caso contrário, corpo do commit + comentário vinculado a PR/issue cumprem a rastreabilidade, sem alegar capacidade não disponível.
5. **Relato no chat**: encerrar cada execução com mensagem objetiva em português, no próprio chat/resultado da rodada: `Worker | data/hora | implementado | commit SHA e link | testes/resultado | bloqueios | próxima rodada | merge (W00)`. Não limitar a informação ao GitHub.
6. **Medição real**: W00 deve verificar e divulgar a cada hora quais dos quatro executores realizaram commits de **código ou testes** nesta rodada, quais passaram em testes/CI e quais entraram na `main`. Um commit de documentação, vazio, cosmético ou sem alteração útil **não** conta para meta de engenharia. Não atribuir commits sem evidência ao worker.
7. **Sem entrega**: se permissão, segurança, CI, conflito de claim ou outra falha impedir o commit/merge, classificar `BLOQUEADA / SEM COMMIT`, relatar no chat e PR/issue o erro exato e a solução planejada. **Não fabricar commits nem forçar merge**; preservar checkout, permissões e dados da VPS.
8. **Fechamento**: PRs de código só são integrados após critérios verificáveis de testes, revisão e compatibilidade frontend/API; W00 nunca realiza merge de PR draft incompleto ou código que conceda indevidamente privilégios. Deploy somente com liberação, pipeline e VPS íntegra.

**Modelo do corpo do commit**:
```text
correcao(independence): proteger edição de item comercial [agent:W1]

O que foi feito: adicionada validação no fluxo de alteração de itens.
Motivo: impedir mudanças em eventos explicitamente não verificados.
Arquivos/fluxos: controlador de eventos e testes de regressão.
Testes: PHPUnit direcionado (aprovado).
Riscos/limites: sem alteração nas regras de registros legados.
```

