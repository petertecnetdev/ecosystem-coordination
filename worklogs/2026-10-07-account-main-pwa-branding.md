# Worklog — PWA Branding Lead — 2026-10-07

## Task
Eliminar o fundo quadrado visível da logo da Cutinapp durante a inicialização do PWA.

## Diagnóstico
Os ícones `logo192.png` e `logo512.png` usados como `purpose:any` eram RGBA, porém totalmente opacos nos cantos, incorporando um matte preto quadrado. Isso deixava a aparência dependente da correspondência exata entre o matte do PNG e o fundo efetivamente renderizado/cached pelo navegador/OS.

## Implementação
- adicionados `public/pwa-icon-192.png` e `public/pwa-icon-512.png` com fundo externo transparente;
- preservado o conteúdo visual oficial da logo e o glow;
- mantido o maskable com fundo preto opaco;
- manifest atualizado para separar `any` de `maskable`;
- service worker/cache schema atualizado;
- URLs de manifest/SW versionadas em `public/index.html`;
- smoke test ampliado para validar transparência dos `any`, matte do maskable e cores do launch.

## Evidence
- commit: 9cae283116b905e1d8c304e14c277af6c2518e2d
- commit: 7910332259d3c901545f1171439b8bb3ac00f342
- `npm run smoke:pwa`: PASS
- syntax check: PASS

## Runtime
Não houve pull/build/deploy na VPS. O checkout encontrado está `ahead 1, behind 4`, com arquivos modificados e backups não rastreados; atualização direta neste estado poderia sobrescrever trabalho existente.

## Impacto esperado
Melhora imediata de percepção de qualidade no cold start do PWA e reduz recorrência de regressões de branding/cache.

PWA Branding Lead (account-main-pwa-branding)
