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
