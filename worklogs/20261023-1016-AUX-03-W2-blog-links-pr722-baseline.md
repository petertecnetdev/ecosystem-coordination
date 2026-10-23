# AUX-03 W2 — SEO editorial / links de aquisição — 2026-10-23

Owner: AUX-03-W2
Priority: P1
Status: COMMITTED_PUSHED — CI_SUCCESS — PR_DRAFT — NOT_MERGED — NOT_DEPLOYED

## Objetivo
Liberar links internos clicáveis em artigos do blog da Cutinapp para conectar tráfego orgânico a páginas de aquisição de produtores, sem duplicar conteúdo editorial pendente.

## Área / oportunidade
Blog público → links contextuais → landing de produtores → cadastro → produção → primeiro evento publicado. O PR #722 estava bloqueado desde 20/10 por baseline obsoleto de estabilidade React após a remoção de duas chaves instáveis da página de artigo.

## Coordenação e trabalho realizado
- Consultados CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, claims/active/, worklogs/ e orchestration/assignments/AUX-03/W2.md.
- Reutilizado claim existente claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md e branch existente feat/aux03-blog-editorial-links-20261013.
- Lido scripts/check-react-stability.js na branch e confirmada exatamente uma entrada obsoleta de baseline para src/pages/blog/BlogArticlePage.js:array index (2).
- Inspecionado BlogArticlePage.js na mesma branch: zero ocorrências de key={index|idx|i}.
- Removida exclusivamente a entrada obsoleta; nenhuma outra regra alterada.
- Commit remoto d717ef3321d362328b908091b6984723fde55351, validado por nova leitura do arquivo.
- PR #722 permanece draft e mergeable=true; GitHub Actions run 39959804379 concluiu SUCCESS: lint:react-stability, testes Jest, build e perf:budget aprovados. Sem testes locais, merge ou deploy.

## Entregável / canal
Commit: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/d717ef3321d362328b908091b6984723fde55351
PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
CI: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/39959804379
Canal: blog público / SEO editorial / aquisição orgânica.

## CTA e métricas
CTA contextual de referência: "Conheça a Cutinapp para produtores" → /for-producers (somente após validação da oferta comercial no PR #724).
Métrica principal: cliques únicos nos CTAs editoriais / sessões dos artigos.
Métrica de negócio: primeiros eventos publicados atribuídos ao blog.
Baseline e conversões: não medidos; não afirmar melhoria de tráfego ou receita.

## Confirmado, hipótese e recomendação
Confirmado: commit enviado, arquivo remoto atualizado, PR mergeable e CI concluído com sucesso (job frontend).
Hipótese: links contextuais podem elevar avanço dos leitores para o cadastro.
Recomendação: aguardar CI, corrigir eventuais falhas, validar links e mobile (320/360/390/430), revisar/mesclar PR #722; coordenar a revisão da oferta comercial do PR #724 antes de encaminhar tráfego para a landing.

## Próxima ação / conta principal
W2: entregar CI verde e evidências à conta principal; acompanhar integração e validar os CTAs no ambiente público após merge/deploy.
Conta principal necessária: SIM — aprovação de PR, QA mobile e integração. Nenhuma alteração em VPS.
