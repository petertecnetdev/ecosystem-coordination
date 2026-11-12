# AUX-03 → W00 / W3 / conta principal — 12/11/2026 10:09 BRT

## Entrega
Pacote de copy para tornar explícitos os quatro públicos da Cutinapp na página `https://petertecnet.com.br/plataformas/cutinapp`:
- participantes;
- produtores;
- artistas;
- organizadores.

Arquivo:
`deliverables/AUX-03/20261112-AUX-03-posicionamento-por-publico-cutinapp.md`

A página já possui title, description, canonical, OG/Twitter, Schema.org SoftwareApplication/WebApplication e sitemap no gerador W3. Não duplicar essa infraestrutura. A oportunidade é trocar o H1 genérico “Cutinapp” por “Descubra eventos. Compre ingressos. Viva experiências.” e inserir uma seção que explique a proposta para cada público.

## Confirmado
- Cutinapp domain returned HTTP 530 on 12/11.
- Issue P0 #643 remains open.
- PRs #724–#727 remain open/unmerged; #727 Draft.
- Metricool Cutinapp brand exposes GBP only, no Instagram data; 30-day GBP metrics returned zeros/empty posts and keyword rows.
- GBP eligibility has not been confirmed. Google requires in-person customer contact and lists online-only brands as ineligible.
- Search Console not accessed; no claim of deindexation.

## Ações solicitadas

### W00
1. Reconciliar issue P0 #643 em `BLOCKERS.md`; o arquivo atual consultado lista FIN-P0-001, mas não espelha o gate público #643.
2. Coordenar a resolução do serving e não declarar GO sem SHA igual no filesystem, HTTP local e HTTPS público.

### W3
1. Revisar o bloco editorial no entregável.
2. Se aprovado pelo owner, inserir a seção por público em `src/seoEntities.js`/gerador dentro do fluxo Git autorizado.
3. Preservar title/description/schema/sitemap já existentes; não criar nova página nem duplicar FAQ.
4. Não ativar CTAs para Cutinapp até o gate público estar verde.

### Conta principal
1. Confirmar se a empresa possui local real que recebe clientes durante horários declarados ou presta atendimento presencial elegível.
2. Se a operação for somente online, não usar GBP como canal de aquisição nem tentar contornar as regras.
3. Autorizar revisão/integração W3 e validar os destinos mobile após a resolução do #643.

## CTA e métricas
- Participantes: Explorar eventos.
- Produtores: Cadastrar minha produção.
- Métrica: cliques por CTA, cliques da página Peter Tecnet para Cutinapp, produtores cadastrados e primeiro evento publicado em 7 dias, sessões de participantes que avançam a evento/checkout.
- Baseline: N/D.

Nenhuma alteração de produto, publicação social/GBP, merge ou deploy foi realizada.
