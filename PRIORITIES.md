# Ecosystem Priorities

## North star
Meta empresarial: construir operação capaz de sustentar R$ 100.000/mês de lucro operacional recorrente. Esta meta orienta prioridades; não é tratada como garantia.

## P0
- regressões que bloqueiem login, compra, pagamento, emissão/entrega, pedido ou acesso;
- perda de dados ou dinheiro;
- falhas de payout/settlement/reconciliação que possam duplicar, perder ou reter valores indevidamente;
- vulnerabilidades de autorização/isolamento entre aplicações;
- indisponibilidade causada por mudança recente;
- produção/CI quebrados quando impedem venda ou integração crítica.

## P1
- falhas graves de conversão, checkout, onboarding e fluxos principais;
- SEO técnico que impeça indexação de páginas comerciais importantes;
- ausência/quebra de landing pública para produtos monetizáveis;
- páginas de intenção e conteúdo editorial de alta intenção ligados a conversão;
- regressões de UX impeditivas;
- inconsistências de contrato frontend/API;
- CI/build quebrado em trabalho pronto para integração;
- telemetria insuficiente para medir funil de receita.

## P2
- performance, Core Web Vitals, acessibilidade, responsividade;
- melhorias de produto com impacto mensurável em aquisição, retenção ou ticket;
- expansão editorial/blog e long-tail após P0/P1 principais estarem cobertos.

## P3
- refinamentos cosméticos sem impacto operacional, financeiro ou de conversão imediato.

Antes de iniciar P1-P3, verificar P0 em `BLOCKERS.md`, `COMMANDS.md` e claims ativos.


## Alocação vigente — 30/10/2026
A ordem CMD-008 em COMMANDS.md substitui a distribuição histórica de W00–W4. P0 de segurança mantém precedência **dentro do escopo de cada worker**; não realocar W2/W3/W4 para Independence.

| Worker | Entrega prioritária | Gate verificável |
| --- | --- | --- |
| W1 | Concluir Independence e curadoria automatizada NP12 | API #546 e React #715: CI SHA exato, Asaas/checkout seguro, reivindicação, QA e NP12 operacional |
| W2 | Administrator / Admin Center | Admin #4: RBAC por app_id, 401/403, sessão/revogação, auditoria, CI e QA |
| W3 | Site institucional Peter Tecnet | Branding, mobile, SEO técnico, velocidade, CTAs e integração dinâmica, com commit/PR e CI quando autorizado |
| W4 | Conteúdo e SEO comercial Peter Tecnet | Artigos/serviços reais, clusters e CTAs com ID/URL de rascunho/publicação; indexação apenas medida |

W00 resolve claims, handoffs e bloqueios entre frentes. Não criar branches/automações, nem merge/deploy sem autorização; preservar OPENAI_SAFETY_CHECKS. Funil de leads (impressões, visitas, contatos, leads e vendas) somente com telemetria verificável.
