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
