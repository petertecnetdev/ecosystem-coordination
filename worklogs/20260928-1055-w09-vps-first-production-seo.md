# W09 Worklog — VPS-first Production SEO

worker: W09 Public UX SEO Sharing
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: partial / push-blocked

## Problemas encontrados
- VPS principal estava em `w09/production-seo-prerender` com alterações não commitadas de outro escopo; foram preservadas.
- A branch `main` estava em worktree separado do W10, limpa, 1 commit à frente e 7 atrás de `origin/main`.
- `scripts/generate-seo-snapshots.mjs` da main remota ainda não tinha snapshot público de Produção, timezone configurável e mantinha fallback estrutural de país.
- Após aplicar o lote W09, auditoria detectou `addressCountry: production.country || "BR"` ainda presente no schema de Produção; corrigido para não inventar país.
- Build do worktree falhou por ausência de `react-scripts`; tentativa de `npm ci` falhou com EACCES em `node_modules/react/LICENSE` pré-existente.
- `git push origin main` ficou aguardando autenticação HTTPS e foi interrompido; nenhuma publicação remota foi declarada.

## Implementação VPS
- Merge não destrutivo de `origin/main` na main VPS preservando commit W10.
- `2726eac6` — feat(seo): prerender public production pages.
- `31272547` — fix(seo): harden production social previews.
- `234bc7a7` — fix(seo): remove Brazil fallback from production schema.

## Arquivos
- `scripts/generate-seo-snapshots.mjs`

## Testes / evidências
- `node --check scripts/generate-seo-snapshots.mjs`: PASS.
- `git diff --check`: PASS.
- build: BLOCKED (`react-scripts` ausente no worktree).
- `npm ci`: BLOCKED por EACCES no node_modules do worktree.
- snapshot runtime: pendente porque o build base não pôde ser produzido.
- push: BLOCKED por autenticação Git HTTPS do host.
- deploy/restart/cache clear: não executados; não havia artefato validado/publicado.

## Pendências / requests
- Restaurar/publicar a main VPS pelo canal Git autenticado sem perder os commits existentes de W10/W09.
- Corrigir ownership/isolamento de dependências no worktree de main e repetir build + snapshot runtime.
- Depois do push/deploy, validar crawler real de Evento e Produção: title, description, canonical, OG/Twitter, imagem, JSON-LD e conteúdo indexável.
- W05: não duplicar W09-003 enquanto este lote estiver ativo.
- W10: considerar o EACCES do node_modules como dívida da infraestrutura de teste/worktree.
