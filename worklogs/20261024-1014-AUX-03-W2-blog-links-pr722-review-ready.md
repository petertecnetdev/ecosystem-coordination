# AUX-03 W2 — SEO editorial / links de aquisição — 2026-10-24

owner: AUX-03-W2
priority: P1
status: REVIEW_READY — CI_SUCCESS — NOT_MERGED — NOT_DEPLOYED
repository: petertecnetdev/cutinapp.petertecnet.com.br
scope: blog público / links editoriais / aquisição de produtores

## Objetivo
Transformar artigos do blog em caminhos navegáveis até o cadastro de produtores, com links internos seguros e mensuráveis, sem duplicar trabalho de SEO global ou da landing comercial.

## Área e oportunidade
SEO editorial, blog público e conversão. O PR #722 havia ficado em draft enquanto correções de CI eram realizadas. Com os dois workflows verdes, o próximo gargalo era liberar a revisão humana e documentar as dependências de lançamento.

## Coordenação e prevenção de duplicação
Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/assignments/AUX-03/W2.md, orchestration/STATE.md, claim ativo 20261008-1600-AUX-03-W2-seo-public-discovery.md e worklog AUX-03-W2 de 23/10.
Mantido o escopo do PR #722; oferta comercial /for-producers pertence ao PR #724 (AUX-03-W3). Sem criar branch ou artigo redundante.

## Trabalho realizado / entregável
- Verificados PR #722 e HEAD d717ef3321d362328b908091b6984723fde55351.
- Confirmados workflows Validate Cutinapp e Lighthouse CI concluídos com SUCCESS para o HEAD.
- Atualizada descrição do PR #722 com evidências de CI, escopo de links Markdown, CTA/métricas, QA mobile e dependência do PR #724.
- PR #722 promovido de draft para **ready for review**, permanecendo OPEN, mergeable=true na resposta do GitHub, sem merge.
- Nenhum deploy, build na VPS, mudança de domínio público ou alegação de conversão.

## Evidências
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- Validate Cutinapp: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39959804379 — SUCCESS
- Lighthouse CI: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39959804361 — SUCCESS
- Landing comercial (outro owner): https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Fonte de coordenação: CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md.

## Canal, CTA e métrica
Canal: blog público / busca orgânica / links internos.
CTA de referência: **Conheça a Cutinapp para produtores** → `/for-producers` (após validar a oferta comercial).
Métrica intermediária: CTR editorial = cliques únicos em links internos de aquisição / sessões dos artigos.
Métrica de negócio: primeiros eventos publicados atribuídos ao blog (janela de atribuição a definir com telemetria).
Baseline: não medido; não há prova de crescimento ou conversão.

## Confirmado, hipótese, recomendação
**Confirmado:** dois workflows verdes, PR pronto para revisão, aberto e não integrado; GitHub indicou mergeable=true após atualização de metadados.
**Hipótese:** navegação contextual pode aumentar avanço de leitores para cadastro de produtores.
**Recomendação:** revisar em 320/360/390/430px, revalidar destino dos CTAs, integrar PR #722 após revisão; sincronizar com owner do PR #724 antes de ativar distribuição.

## Próxima ação / conta principal
Conta principal necessária: **SIM** — revisão final, QA mobile, merge do PR #722 e posterior validação pública; coordenar landing PR #724.
Estado final: REVIEW_READY — 2 CI SUCCESS — OPEN — NOT_MERGED — NOT_DEPLOYED.
