# W09 Worklog — Production SEO snapshots

worker: W09
repository: petertecnetdev/cutinapp.petertecnet.com.br
point: W09-003
status: implementing

## Problemas encontrados
- `/production/:slug/public` ainda não possui HTML específico para crawlers no gerador da main.
- O gerador mantinha `America/Sao_Paulo` e fallback `BR` estruturais.
- O checkout local do servidor está compartilhado e muito sujo por outros workers; implementação foi isolada em worktree limpo.
- `git push` HTTPS no host bloqueou aguardando autenticação; foi interrompido sem alterar a árvore compartilhada.

## Implementação
- `scripts/generate-seo-snapshots.mjs`
- paginação de `/organizations/public`;
- snapshots de `/production/:slug/public`;
- title/description/canonical/OG/image;
- JSON-LD ProfilePage + Organization;
- corpo crawler-visible com nome/localização/descrição/link;
- remoção dos defaults estruturais `BR`;
- timezone default UTC configurável por `CUTINAPP_SEO_TIME_ZONE`;
- cleanup/marker passam a incluir Produções.

## Testes e evidências
- `node --check scripts/generate-seo-snapshots.mjs`: PASS.
- `git diff --check`: PASS.
- gerador executado em build fixture isolada contra API pública: PASS, 21 páginas a partir de 6 eventos e 3 produções.
- HTML de `Luxury Club`: title específico, canonical `/production/luxury-club/public`, `ProfilePage`, `Organization` e `data-cutinapp-seo-snapshot` confirmados.
- commit local: `6de4d201` (`77 insertions, 4 deletions`) sobre main `32786cc1`.
- push/PR: pendente; HTTPS do host aguardou autenticação e foi interrompido.
- deploy: não aplicável neste ciclo.

## Impacto econômico esperado
Produções passam a poder ser compreendidas e compartilhadas por crawlers sem depender de JavaScript, fortalecendo descoberta orgânica, confiança e aquisição de produtores a partir de links públicos.

## Pendências / requests
- W05: preservar ownership W09 e evitar duplicação; transportar/aprovar o commit por canal GitHub autenticado.
- Após PR: observar CI e, após deploy, testar crawler/preview real antes de `VERIFIED`.
