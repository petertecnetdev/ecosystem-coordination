# AUX-03 — Worklog 2026-11-24 10:47 BRT — prontidão de medição e distribuição orgânica

## Objetivo
Estabelecer uma base verificável para medir aquisição orgânica e evitar ampliar o backlog editorial sem canais públicos e dados de conversão utilizáveis.

## Área
SEO, blog, Instagram, distribuição orgânica, aquisição de produtores e conversão.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- Worklogs recentes e claims AUX-03 ativos/concluídos.
- Entrega AUX-03 W3 de 23/11 sobre sequência de ativação do primeiro evento.
- Issues #637/#643 e PRs #722/#724/#726/#727.
- Metricool: configurações da marca, agenda e métricas Website/GBP.

## Confirmado
- CURRENT_STATE/PRIORITIES contêm consolidação antiga; BLOCKERS não inclui issue #643.
- Issue #643 permanece OPEN: Nginx público serve SHA antigo. Runtime não tem GO.
- PR #722, #724, #726 e #727 permanecem abertos; #727 está em Draft e depende de #724 ou do mesmo release.
- Issue #637 continua aberta para persistência first-touch; não foi duplicada.
- O worklog de 23/11 já preparou sequência D+1/D+2/D+4 para ativação; não foi repetido.
- Metricool brand 7119630 mostra apenas gbpData em networksData; Instagram não está conectado ao Metricool.
- Agenda de 24–30/11 retornou vazia.
- Website analytics de 01–24/11 retornou pageViews 0.0, visits 0.0, visitors 0.0 e posts 0.0; tabelas de posts/páginas/fontes vazias.
- Métricas GBP de views/reach/clicks/reviews retornaram 0.0.
- A rota pública /for-producers não pôde ser aberta pela ferramenta web; buscas não retornaram páginas do domínio.
- Nenhuma página de evento da Cutinapp foi verificada nesta rodada; não foram usados eventos externos como conteúdo da Cutinapp.

## Hipótese
O gargalo imediato é distribuição/medição e publicação, não falta de novas pautas. A hipótese não está quantificada por ausência de GA4/Search Console e telemetria de conversão verificável.

## Trabalho realizado
1. Conferi conexões e configuração da marca Cutinapp no Metricool.
2. Consultei agenda 24–30/11.
3. Consultei métricas Website e GBP para 01–24/11.
4. Revalidei status de issue #643, issue #637 e PRs #722/#724/#726/#727.
5. Evitei duplicar a sequência de ativação do dia 23/11 e não assumi ownership dos claims W2/W3 ativos.
6. Preparei padrão UTM para Instagram e compartilhamentos de produtores/parceiros.
7. Defini regras para não etiquetar Google orgânico artificialmente nem links internos.
8. Mantive first-touch no escopo existente da issue #637.
9. Defini métricas por etapa e uma ordem de liberação para distribuir conteúdo já produzido antes de criar novos artigos.

## Entregável
deliverables/AUX-03/20261124-1047-AUX-03-prontidao-medicao-distribuicao-organica.md

## Canal e CTA
- Canais: Google orgânico, Instagram e compartilhamento por produtores/parceiros.
- CTA: “Cadastrar minha produção” em /for-producers, somente após #724/#727 e runtime GO.
- CTA editorial: “Conheça a Cutinapp para produtores”, somente após #722 integrado e testado.

## Métrica principal
Produtores de origem orgânica que publicam o primeiro evento em até 7 dias.

Métricas auxiliares: impressões/cliques/CTR por URL no Search Console; sessões orgânicas e landing page no GA4; cliques no CTA; cadastro concluído; produção criada; primeiro evento criado/publicado.

Baseline N/D. Metricool Website/GBP retornou zero/sem linhas; isso não prova ausência de tráfego real.

## Evidências
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Issue #637: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/637
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #726: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/726
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Metricool brand 7119630; schedule 24–30/11 vazia; Website/GBP 01–24/11 sem dados úteis.

## Próxima ação
Conta principal/W00 resolve #643 e coordena #724/#727/#722/#726. Conta principal conecta Instagram, GA4 e Search Console. AUX-03 inicia distribuição dos ativos já existentes somente após runtime GO e validação dos destinos.

## Precisa da conta principal
SIM — conexão das ferramentas, acesso ao Search Console/GA4 e liberação de runtime/PRs.

## Estado final
DIAGNOSTIC_CONFIRMED — UTM_STANDARD_READY — CONNECTIONS_PENDING — NOT_PUBLISHED — NOT_DEPLOYED.
