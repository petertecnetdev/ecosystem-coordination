# Coordination Protocol

## 0. Identidade obrigatória
Na primeira execução de cada agente:
1. defina um `agent_id` técnico, único e estável;
2. escolha um `display_name` humano, curto e único;
3. registre `agent_id`, `display_name` e `role` em `agents/<agent-id>/status.md`;
4. verifique se o nome já não pertence a outro agente;
5. depois de escolhido, não altere o nome sem necessidade real.

Toda comunicação deve ser assinada com:
`<display_name> (<agent_id>)`.

## 1. Leitura obrigatória
Todo ciclo começa lendo, nesta ordem:
- `COMMANDS.md`
- `CURRENT_STATE.md`
- `PRIORITIES.md`
- `BLOCKERS.md`
- `claims/active/`
- mensagens recentes relacionadas ao projeto/frente
- discussões abertas relacionadas à área de trabalho

## 1.1 Prioridade dinâmica
A função-base do agente permanece estável, mas a demanda concreta deve ser escolhida dinamicamente conforme `COMMANDS.md`, P0/P1, blockers, handoffs, claims, regressões, CI e impacto. Não insistir em backlog menos importante quando existir demanda superior segura e acionável.

## 2. Claim
Crie:
`claims/active/YYYYMMDD-HHMM-<agent-id>-<slug>.md`

Formato:

```md
# Claim
agent: <agent-id>
display_name: <nome>
repository: <owner/repo>
area: <área funcional>
task: <objetivo>
branch: <branch ou TBD>
status: working
started_at: <ISO-8601>
depends_on: <PR/claim/none>
files_or_scope:
- <caminho/área>

## Notes
<contexto curto>
```

Não iniciar o mesmo escopo de outro claim ativo sem handoff explícito.

## 3. Discussões públicas
Use `discussions/open/<thread-id>/`.

O primeiro agente cria:
`discussions/open/<thread-id>/README.md`

As contribuições seguintes são arquivos independentes:
`YYYYMMDD-HHMM-<agent-id>-<slug>.md`

Cada contribuição deve conter:

```md
# Contribution
from: <display_name> (<agent-id>)
topic: <assunto>
position: proposal|question|review|agreement|disagreement|decision-candidate
related_repository: <owner/repo ou none>
related_pr: <# ou none>

## Analysis
...

## Proposal / Response
...

## Evidence
- commit:
- PR:
- checks:
- issue:
```

Discuta de forma técnica e objetiva:
- melhorias;
- avanços;
- bugs e correções;
- arquitetura;
- UX/UI;
- segurança;
- performance;
- receita/conversão;
- integrações;
- riscos;
- dependências;
- implementação proposta ou realizada.

Não crie conversa artificial apenas para gerar atividade. Responda quando houver algo relevante a acrescentar. Discordâncias devem registrar evidências e alternativas.

Quando houver consenso e ação segura, abra claim e execute. Quando o tópico estiver resolvido, registre uma conclusão e mova o thread para `discussions/closed/` quando possível.

## 4. Implementação
- preservar trabalho recente;
- branch/PR quando apropriado;
- nunca force-push;
- respeitar branch protection;
- evitar mudanças destrutivas;
- preservar arquitetura central genérica e reutilizável;
- verificar dependências frontend/backend.

## 4.1 — Identificação e rastreabilidade em português
Padrão vigente para todas as novas demandas e repositórios do ecossistema, conforme `COMMANDS.md` (CMD-006).

### Branches: descrever a entrega
- Formato obrigatório para novas branches: `categoria/objetivo-especifico`.
- Prefixos em português: `funcionalidade`, `correcao`, `melhoria`, `seguranca`, `refatoracao`, `manutencao`, `documentacao`.
- Usar ASCII minúsculo, palavras com hífen, sem acentos, espaços, datas ou números de worker como identidade principal.
- Exemplos: `funcionalidade/curadoria-e-reivindicacoes`, `funcionalidade/tipos-de-eventos`, `melhoria/cadastro-de-produtores`, `correcao/menu-mobile`, `seguranca/permissoes-cutinapp`.
- É o nome da **entrega do ciclo**, não o nome de cada alteração individual: vários workers podem trabalhar nessa mesma branch, em arquivos diferentes sob claims exclusivos.
- Para a Cutinapp, respeitar o limite de `main` e uma branch compartilhada ativa por repositório após o saneamento de legado. Não abrir branches por worker, por demanda paralela ou por retry. W00 coordena exceções necessárias e preservação do trabalho.
- `Independence` é um nome legado válido enquanto esse ciclo estiver aberto. Não renomear retroativamente nem reescrever histórico apenas para aplicar o padrão.

### Commits e Pull Requests
- Commit: `categoria(escopo): verbo + resultado específico` em português brasileiro, com acentos permitidos. Exemplos:
  - `funcionalidade(reivindicacoes): permitir solicitacao de acesso de artistas`
  - `correcao(eventos): exibir erros obrigatorios no SweetAlert`
  - `melhoria(cadastro): organizar formulario no celular`
  - `teste(permissoes): cobrir isolamento entre aplicativos`
  - `documentacao(coordenacao): registrar pendencias da curadoria [agent:<agent-id>]`
- Para commits de agentes neste repositório, manter a assinatura `[agent:<agent-id>]` definida no README.
- Títulos e descrições dos PRs em português. Referências técnicas imutáveis (endpoints, classes, nomes de bibliotecas) permanecem literais quando fizer sentido.
- Evitar `ajustes`, `update`, `final`, `mais correcoes` ou mensagens vagas sem objeto verificável.

### Evidência de feito, em andamento e pendente
Todo trabalho ativo deve ter um issue, PR, claim ou worklog rastreável, com a seguinte seção atualizada a cada ciclo:

```md
## Andamento
Objetivo: [entrega exata]
Estado: planejado | em-andamento | em-revisao | bloqueado | concluido
Responsável: [agent-id]

### Feito
- [x] [etapa com SHA/PR e evidência]

### Em andamento
- [ ] [etapa atual e responsável]

### Falta
- [ ] [etapa restante, dependência ou critério de aceite]

### Validação e publicação
Testes/CI: [resultado observado ou não verificado]
Merge na main: [SHA/PR ou não realizado]
Deploy: [ambiente/SHA verificado ou não realizado]
Próxima ação: [quem fará o quê]
```

- `concluido` exige critérios de aceite, testes e evidências compatíveis com a entrega. Não confundir `commit enviado` com `em produção`.
- Atualizar status em claims, handoffs e PRs em vez de criar outra branch para sinalizar progresso.
- Encerrar branch após merge e preservação confirmada; nunca deletar trabalho exclusivo, claims ativos ou PRs relevantes sem handoff.
- Se a ferramenta bloquear publicação/exclusão, registrar `bloqueado` com a causa e a próxima ação; não declarar sucesso.

## 5. Handoff
Crie:
`messages/YYYYMMDD-HHMM-<from>-to-<to>-<slug>.md`

Formato:

```md
# Handoff
from: <display_name> (<agent-id>)
to: <display_name/agent-id ou role>
repository: <owner/repo>
related_pr: <# ou none>
priority: P0|P1|P2|P3
status: action-required|informational

## Context
...

## Requested action
...

## Evidence
- commit:
- PR:
- checks:
```

## 6. Encerramento
- registrar commit/PR/checks;
- marcar `completed`, `blocked` ou `handoff`;
- criar registro em `claims/completed/`;
- remover o ativo somente após existir o registro concluído;
- atualizar o worklog com resumo e evidências.

## 7. Blockers
Blockers globais de alto impacto entram em `BLOCKERS.md`.

## 8. Prioridades
`PRIORITIES.md` é consolidado pela frente Tech Lead/Coordination. Outros agentes propõem mudanças por discussão ou mensagem.

## 9. Segurança e transparência
O repositório é público. Nunca registrar:
- tokens;
- senhas;
- chaves;
- credenciais;
- segredos de produção;
- dados pessoais desnecessários;
- dumps de banco;
- conteúdo confidencial de usuários.

Pode registrar decisões técnicas, análises, commits, PRs, testes, riscos e discussões de produto que não exponham segredos.


## 1.2 Orquestração global W00 / contas AUX
Workers identificados como `AUX-01` até `AUX-11` fazem parte do pool auxiliar da Cutinapp.

Após a leitura de prioridades e antes de escolher trabalho por conta própria, todo worker AUX deve ler sua inbox em:
`orchestration/assignments/AUX-XX/WN.md`

Mapeamento do slot:
- a conta vem do identificador `AUX-XX` definido no prompt-base;
- o worker usa seu slot W1/W2/W3 registrado em `orchestration/WORKER_REGISTRY.md`.

Precedência operacional:
1. P0 explícito emitido por W00;
2. assignment `READY` na inbox individual;
3. handoff `action-required`;
4. função-base permanente do worker.

Se a inbox estiver `AVAILABLE`, o worker executa normalmente sua missão-base e não fica ocioso.

Ao consumir uma assignment, o worker deve manter o estado: `READY -> CLAIMED -> IN_PROGRESS -> DONE|BLOCKED`, com evidências em claims/worklogs/handoffs. W00 pode substituir assignments `READY`; não deve sobrescrever `CLAIMED` ou `IN_PROGRESS`, exceto por P0 documentado.

O prompt-base permanente do worker não precisa ser reescrito para cada demanda. A inbox define a demanda concreta do ciclo. Isso preserva especialização e permite realocação dinâmica.

W00 é responsável por ler os resultados AUX, evitar duplicação, respeitar claims ativos e manter `orchestration/WORKER_REGISTRY.md` e `orchestration/STATE.md` coerentes com as contas configuradas.
