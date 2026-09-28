# Worklog — Production metrics drill-down
agent: Hotfix Sentinel (chatgpt-vps-hotfix)
date: 2026-09-28
repositories:
- petertecnetdev/cutinapp.petertecnet.com.br
- petertecnetdev/api.petertecnet.com.br

## Implementação
A view pública de produção agora abre detalhamento também para `eventos` e `seguidores`, seguindo a interação já existente de `visualizações`.

Frontend:
- eventos clicáveis no resumo;
- seguidores clicáveis no resumo;
- modal de seguidores reutilizando a apresentação dos visualizadores, com avatar e link de perfil;
- modal de eventos com flyer quadrado maior que o avatar, nome, data/local e navegação;
- paginação lazy para seguidores e tratamento de loading/erro.

API:
- endpoint público genérico `GET /api/v1/apps/{application}/social/followers`;
- target `user|artist|production`;
- paginação limitada a 100;
- perfis com `user_social_preferences.discoverable=false` não são expostos;
- nenhuma migration criada.

## Validação
- `npm run lint:production-view`: 31/31 checks.
- build otimizado compilou com sucesso em worktree baseado na main atual; o build padrão acusou erro preexistente e fora do escopo de `react/prop-types` em `ProductionDiscoveryRail.js`, portanto a segunda compilação usou `DISABLE_ESLINT_PLUGIN=true` sem editar esse arquivo.
- Nginx local da página pública respondeu HTTP 200 após publicação atômica do build.
- assets publicados contêm `social/followers`, estados de seguidores e `cut-production-event-row`.
- `php -l` passou em controller, rota e teste.
- request pelo kernel Laravel para La Fyesta Pub (production id 10) respondeu HTTP 200 no endpoint e retornou perfil público de seguidor.
- runner PHPUnit não está instalado no ambiente de produção; o feature test foi escrito, mas não executado no VPS.

## Git
- frontend local commit: `db3c2c01e38d1302d7125b888c4892f618f39414`
- API local commit: `5d1b58004e04c3632734f158c3022a2ce2d0f461`
- push remoto pendente porque a autenticação HTTPS do Git na VPS fica bloqueada e não existe helper/token acessível ao worker. Handoff criado para sincronização sem reimplementar.

Hotfix Sentinel (chatgpt-vps-hotfix)
