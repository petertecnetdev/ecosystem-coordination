# Global Commands

Este arquivo contém ordens operacionais globais para os agentes do ecossistema Peter Tecnet.

Todos os agentes devem lê-lo no início de cada execução, antes de selecionar trabalho. Também devem consultar `REVENUE_TARGET.md` e `PROFITABILITY_PLAN.md` para entender a meta econômica e a fila estratégica.

## CMD-001 — Continuous hourly pipeline
status: ACTIVE
target: ALL_ACCOUNTS
priority: P0-OPERATIONAL

### Schedule standard
Para contas com 3 tarefas ativas:
- Task A: hourly at minute 00
- Task B: hourly at minute 20
- Task C: hourly at minute 40

Cada tarefa continua com frequência máxima de 1 execução por hora, mas a conta inicia um novo ciclo a cada 20 minutos.

Para contas com 5 tarefas, manter escalonamento equivalente de 12 minutos quando já configurado.

### Dynamic demand assignment
A responsabilidade-base de cada agente permanece, porém a prioridade concreta de cada execução é dinâmica.

No início de cada ciclo, escolher trabalho nesta ordem:
1. P0 aberto em BLOCKERS.md;
2. comando global ACTIVE aplicável;
3. handoff action-required dirigido ao agente/role;
4. regressão crítica ou falha de CI relacionada ao seu domínio;
5. claim/handoff que precise de revisão para destravar integração;
6. P1 de maior impacto;
7. oportunidade segura de maior impacto em receita, conversão, estabilidade, segurança ou arquitetura;
8. backlog P2/P3 apenas quando não houver trabalho mais importante.

Se a demanda mais importante estiver fora da especialidade principal do agente, ele pode assumir somente quando tiver capacidade clara e o trabalho não estiver claimado. Caso contrário, deve encaminhar ao agente apropriado e escolher a próxima prioridade.

### Continuity
Ao finalizar:
- registrar evidências;
- atualizar worklog;
- fechar claim;
- criar handoff para o próximo agente quando houver continuidade;
- deixar explícito o próximo ponto recomendado.

O agente seguinte deve ler esse estado e continuar, revisar ou escolher outro trabalho de maior prioridade.

### No artificial idling
Se não houver blocker, handoff ou claim pendente, o agente deve buscar trabalho seguro e útil dentro de sua função. Não criar atividade artificial nem duplicar trabalho.

## CMD-002 — Identity cleanup
status: ACTIVE
target: ALL_AGENTS
priority: P1-COORDINATION

Regularizar agent_id/display_name duplicados ou namespaces de conta conflitantes. Cada conta deve possuir namespace exclusivo e cada agente deve possuir display_name único e estável.

Quando concluído, registrar no status do agente e no worklog.


## CMD-003 — Profitability north star
status: ACTIVE
target: ALL_AGENTS
priority: P0-BUSINESS

### Goal
Colocar o ecossistema Peter Tecnet em produção estável e rentável, perseguindo a meta empresarial de R$ 100.000/mês de lucro operacional recorrente.

A meta é um norte de priorização, não uma promessa de resultado. Toda execução deve preferir trabalho com relação clara a receita, aquisição orgânica, conversão, retenção, estabilidade operacional ou redução de perdas/custos.

### Revenue decision order
1. Não perder venda existente: login, catálogo/evento, carrinho, checkout, PIX/cartão, confirmação, emissão/entrega e pós-pagamento.
2. Não perder dinheiro: idempotência, webhooks, reconciliação, ledger, fees, refunds, chargebacks, settlement e payout.
3. Captar demanda orgânica: SEO técnico, páginas públicas indexáveis, conteúdo de alta intenção, blog, dados estruturados, sitemap, canonical, performance e links internos.
4. Converter tráfego: proposta de valor, CTA, onboarding self-service, prova de produto, pricing/plans quando aplicável, recuperação de checkout e follow-up.
5. Reter/expandir: recorrência, assinatura, recompra, upsell/cross-sell legítimos, indicação e automações úteis.
6. Reduzir custo operacional e retrabalho.

### Gateway policy
- Não trocar um gateway que está processando vendas de forma estável sem evidência objetiva.
- Manter cobrança funcionando com o provedor saudável atual.
- Implementar abstração/failover apenas de forma genérica e testável.
- Se um provedor falhar, bloquear vendas ou não suportar um requisito financeiro essencial, priorizar o provedor compatível e operacional, preservando idempotência, reconciliação e contratos.
- Nunca simular suporte de gateway que a documentação/API não oferece.

### SEO/content policy
Cada produto com intenção comercial deve possuir:
- landing pública indexável;
- title/description/canonical/OG corretos;
- schema.org apropriado;
- sitemap e robots coerentes;
- páginas de intenção comercial úteis;
- blog/conteúdo editorial original e substancial;
- links internos para produto, serviço e CTA;
- métricas de impressão → clique → visita → lead/cadastro → checkout → receita.
Evitar páginas finas, duplicadas ou geradas apenas para palavras-chave.

## CMD-004 — Production + revenue war room
status: ACTIVE
target: ALL_AGENTS
priority: P0-BUSINESS

Até que o funil de monetização esteja saudável, todos os agentes devem contribuir para uma das frentes abaixo sem duplicar claims:
- PAYMENT/REVENUE: checkout, cobrança, confirmação, repasse/payout, reconciliação.
- PRODUCTION/STABILITY: P0/P1, CI, deployability, erros que bloqueiam uso/venda.
- SEO/CONTENT: indexação, conteúdo de alta intenção, blogs, páginas públicas, performance.
- CONVERSION: onboarding, CTA, pricing/plans, abandono, recuperação e funil.
- ANALYTICS: medir receita, GMV, take rate, margem, CAC orgânico proxy, conversão, retenção e falhas.

Ao final de cada ciclo, registrar impacto econômico esperado e a próxima ação de maior retorno.

## CMD-005 — Cutinapp: duas branches e encerramento de ciclo
status: ACTIVE
target: petertecnetdev/cutinapp.petertecnet.com.br; W00/W0/W1-W4 e AUX-01..AUX-11
priority: P0-OPERATIONAL
issued_at: 2026-10-12
owner: W00 Global Cutinapp Orchestrator

### Invariante obrigatória
O estado final e cada novo ciclo de desenvolvimento devem ter EXATAMENTE duas branches remotas: `main` e UMA branch de trabalho compartilhada. A branch compartilhada atualmente em execução é `Independence` (nome legado; preservar durante este ciclo). Nas próximas demandas, aplicar os nomes descritivos em português definidos no CMD-006. Não criar branches por demanda, por worker, por correção/retry nem por conta auxiliar. Todos os workers da Cutinapp implementam apenas na branch compartilhada, com claim de arquivo/escopo, rebase/refresh conservador e sem sobrescrever edições concorrentes. Uma demanda = claim/handoff; NÃO equivale a nova branch. Cada worker pode atuar em demanda diferente simultaneamente, desde que não haja conflito de arquivos/contrato.

### Operação excepcional de redução do legado
As branches históricas existentes estão CONGELADAS (somente leitura e recuperação). W00 é o único responsável por classificar, integrar, concluir e excluir refs. Não apagar branch que contenha código exclusivo útil, PR aberto relevante, claim `WORKING`, ou pendência de teste sem primeiro preservar/transferir. Comparar cada HEAD com `main` e branch compartilhada; procurar patches equivalentes, não apenas contagem de commits. Registrar SHA antes e depois, arquivo, owner, veredito, CI e destino da recuperação.

1. Classificar e transferir ownership dos claims sobre branches legadas para a branch compartilhada. AUX-01 W1 tem claim ativo de preço de ingresso: preservar até handoff explícito; não apagar só porque está `0 ahead/0 behind`.
2. Trabalhos exclusivos: completar e integrar seletivamente preços/catálogo e contratos API; carteira/404 de artwork; encontros comunitários; SEO/blog/social previews; identidade visual/guardrails; campanha em docs; monetização apenas após contrato SaaS/30 dias da API/Admin Center. Verificar dependências e conflitos; não realizar merges cegos.
3. W4 deve atestar testes reais (Jest/build/lint + browser 320/360/390/430 + API/checkout quando aplicável). Sem QA verificável, não declarar concluído; corrigir CI que não dispara em push `cycle/**` mediante PR/checks nativos autorizados.
4. Ref segura: branch idêntica, ancestral integralmente incorporada ou patch comprovadamente equivalente, SEM claim/PR/trabalho útil/ownership pendente. Excluir com API GitHub DELETE ref ou workflow de GitHub Actions já autorizado com allowlist por SHA exato, confirmar 404 após exclusão. Nunca usar `update_ref` como falso delete, force push, reset hard, clean destrutivo ou atalhos para bloqueio `OPENAI_SAFETY_CHECKS`.
5. Integrar branch compartilhada na `main` somente após CI/QA e revisão independente. Após merge validado: excluir a branch concluída e verificar remoção; SOMENTE DEPOIS criar a próxima branch única a partir da `main`. Nunca acumular branches entre ciclos.
6. Até o saneamento terminar, cada rodada W00 deve priorizar reduções reais, preservando código. Se sem mecanismo de exclusão autorizado ou bloqueado por safety, registrar blocker e solicitar ação humana específica; não inventar sucesso nem criar repos/branches de contorno.

### Responsáveis
- W00/W0: autoridade de merges, cleanup, fila, conflitos, consolidação, ciclo e medição.
- W1: cadastro/funil/pricing sob claim e escopo definido.
- W2: carteira/API/QA de regressão; nunca assumir arquivos de W1 sem handoff.
- W3: UX/CSS/brand/SEO; não sobrepor W1/W2.
- W4: reviewer independente, evidências Jest/build/mobile/checks e parecer de merge/exclusão.
- AUX-XX: ler esta regra ANTES de criar refs; entregar na branch compartilhada após claim/handoff, ou somente relatório/patch para W00 quando sem permissão de push.

### Métricas obrigatórias a cada rodada
`BRANCH_COUNT_BEFORE, BRANCH_COUNT_AFTER, UNIQUE_RECOVERED, MERGED_VERIFIED, DELETED_VERIFIED, MAIN_SHA, SHARED_SHA, CLAIM_CONFLICTS, QA_REAL_STATUS, OPEN_BLOCKERS, NEXT_ACTION`.
Não reportar contagem reduzida sem lista remota pós-operação. Produção/deploy seguem pipeline oficial; sem dirty build ou Git workaround na VPS.


## CMD-006 — Git em português e identificação do trabalho
status: ACTIVE
target: ALL_AGENTS; ALL_REPOSITORIES
priority: P0-OPERATIONAL
issued_at: 2026-10-13
origin: solicitação direta do responsável pelo ecossistema Peter Tecnet

### Regra obrigatória para trabalhos novos
- Usar português brasileiro nos nomes de novas branches, mensagens de commits, títulos e descrições de Pull Requests. Preservar nomes técnicos de bibliotecas, APIs, endpoints, arquivos e identificadores quando necessário.
- Branch: `<categoria>/<objetivo-especifico>`, em letras minúsculas, ASCII (sem acentos), palavras separadas por hífen. Não usar nomes genéricos como `nova-feature`, `fix-1`, `worker-02`, `teste-final` ou nomes de agentes/datas como identificador principal.
- Categorias recomendadas: `funcionalidade/`, `correcao/`, `melhoria/`, `seguranca/`, `refatoracao/`, `manutencao/`, `documentacao/`.
- Exemplos: `funcionalidade/curadoria-e-reivindicacoes`, `funcionalidade/tipos-de-eventos`, `melhoria/cadastro-de-produtores`, `correcao/menu-mobile`, `seguranca/permissoes-cutinapp`.
- Commits: `categoria(escopo): acao concreta em portugues`. Ex.: `funcionalidade(reivindicacoes): adicionar solicitacao de titularidade`; `correcao(eventos): ajustar validacao de campos obrigatorios`. Acentos são permitidos nas mensagens de commits. Commits de agentes na coordenação continuam incluindo `[agent:<agent-id>]`.
- O nome da branch identifica o OBJETIVO do ciclo, não o worker nem o estado (concluído/pendente). Cada claim, issue e PR deve indicar explicitamente o que foi feito, o que está em andamento, o que falta, quem é responsável, bloqueios, SHA, testes e próximo passo.
- Para trabalho compartilhado, reutilizar uma única branch ativa por repositório conforme o ciclo; subdemandas diferentes são claims/commits/PRs e não branches novas. Caso vários repositórios participem da mesma funcionalidade, usar o mesmo nome descritivo quando o ciclo seguinte for iniciado.
- Encerrar o ciclo com revisão, testes e merge na `main`; excluir a branch de trabalho somente depois de confirmar integração e preservação de commits, sem apagar trabalho exclusivo de outros workers. Deploy requer fluxo/autorização próprios.
- Não renomear, reescrever histórico, reiniciar nem excluir branches existentes apenas para traduzir seus nomes; a branch `Independence` continua válida até o fechamento seguro do ciclo atual. Não gerar novas branches para contornar a regra ou problemas de ferramentas.

### Rastreabilidade mínima da demanda
Em cada claim/handoff/PR ativo, registrar e manter atualizado:
- **Objetivo:** uma frase sobre a entrega;
- **Feito:** itens concluídos com evidência de commit/PR;
- **Em andamento:** implementação atual e responsável;
- **Falta:** testes, integração, dependências e demais critérios de aceite não cumpridos;
- **Estado:** `planejado`, `em-andamento`, `em-revisao`, `bloqueado` ou `concluido`;
- **Próxima ação:** executor, ação concreta e bloqueio, quando existir.

Regras detalhadas e exemplos estão em `PROTOCOL.md`, seção **4.1 — Identificação e rastreabilidade em português**.


## CMD-007 — Próximo ciclo Cutinapp: Administração isolada por aplicação
status: ACTIVE
target: W00/W0/W01-W06; AUX-01..AUX-11; repositórios Cutinapp/API/Admin Center quando aplicável
priority: P0-SECURITY / P1-PRODUCT
issued_at: 2026-10-14
owner: W00 Global Cutinapp Orchestrator
issue: https://github.com/petertecnetdev/ecosystem-coordination/issues/12

### Ordem explícita do proprietário
- **Atualização de prioridade por ordem direta em 14/10/2026:** executar Independence e Administrator em PARALELO: W1 + W3 na Independence; W2 + W4 no Administrator; W00 gerencia ambas de hora em hora, mede throughput por entrega testada, corrige bloqueios e revisa estimativa de conclusão. Escala W1 :06, W2 :18, W3 :30, W4 :42, W00 :54, America/Sao_Paulo.
- Durante a Independence, **não criar nova branch**; ambos os projetos usam a branch compartilhada existente `Independence` dos repositórios de código, com claims por arquivo. Trabalho Administrator deve ser modular, não exposto e seguro por padrão, evitando ativar endpoints/permissões sem gate/revisão. Na impossibilidade de isolamento confiável, entregar testes, contratos e serviços não conectados ao runtime, sem publicar funcionalidade incompleta.
- **Somente após** concluir/revisar e integrar Independence na `main` e eliminar a branch, continuar o restante Administrator na única branch compartilhada `funcionalidade/administracao-cutinapp`, obedecendo CMD-005/CMD-006. Se houver mudanças em mais de um repositório, mesmo nome por repositório, máximo uma branch de trabalho por repo.
- Plano de tarefas, handoffs, estimativas por ciclo e reporte auditável: `orchestration/PLANO_HORARIO_INDEPENDENCE_ADMINISTRATOR.md` da branch `main` de coordenação. Revisar em todos os ciclos e atualizar issues #10 e #12.
- O administrador `cutinapp@gmail.com` é administrador da **Cutinapp**, subordinado apenas à autoridade root do ecossistema (referência institucional `petertecnet@gmail.com`), sem poderes nos demais aplicativos ou sobre o root. Não usar emails hardcoded para autorização; resolver identidades, vínculos e permissões no backend.
- Reutilizar o `ApplicationAdminService` e RBAC central existentes, verificando as lacunas reais. Segurança P0: issue API #544; reconhecer melhorias prévias de API PR #543 e frontend PR #714.
- W00 precisa relatar no issue #12 o gate da Independence, owner, claims, arquivos, testes, deploy status e próxima ação. O registro do próximo ciclo não equivale a implementação, merge nem ativação em produção.
