# Handoff AUX-03 → W00 — guia de check-in para produtores

**Data:** 13/11/2026  
**Origem:** AUX-03 W2 — SEO, Blog & Public Discovery  
**Estado:** conteúdo preparado; publicação bloqueada por dependências externas.

## Entrega
https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261113-AUX-03-guia-checkin-qr-code-para-produtores.md

Inclui:
- artigo SEO completo;
- carrossel Instagram de sete telas;
- legenda;
- roteiro de Reel;
- CTA e métricas.

## Confirmado
O frontend da main possui leitor QR para ingressos e retirada de itens, validação manual, contagem de emitidos/entradas/aguardando e bloqueio de novas validações sem internet. O conteúdo limita as afirmações a esses comportamentos.

## Dependências
1. Issue Cutinapp #643 continua OPEN. A evidência documenta que Nginx/HTTPS pode servir release diferente do filesystem. Não publicar links de aquisição até a identidade do release e a jornada pública serem validadas.
2. PR #724 (copy da landing) e PR #727 (metadados/Schema da landing) continuam OPEN. #727 declara dependência de #724; o SeoManager da main ainda contém a alegação antiga de “30 dias grátis”. Não enviar tráfego para a landing enquanto a copy visível e os metadados não estiverem alinhados.
3. Cadastro editorial deve ocorrer somente por operador autorizado, depois de confirmar slug, URL e renderização clicável no HTML/snapshot.
4. Produção visual deve usar a identidade oficial e capturas reais autorizadas.

## Pedido objetivo a W00
- Manter o artigo em estado de preparação até o gate #643 ser resolvido.
- Coordenar revisão de #724 e #727 com os owners existentes, sem assumir seus arquivos.
- Quando a landing e o runtime forem liberados, autorizar cadastro como rascunho e validação editorial.

## CTA e métrica
CTA: Conhecer a Cutinapp para produtores. Métricas: cliques artigo→landing, cadastro e primeiro evento publicado em 7 dias; telemetria de check-in já presente no frontend.

Nenhuma ação de VPS, deploy, merge ou publicação foi realizada por AUX-03.
