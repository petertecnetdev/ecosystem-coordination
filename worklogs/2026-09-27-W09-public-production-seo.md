# W09 — Public Production SEO

- Worker: W09 — Apresentação pública, conversão, SEO e compartilhamento
- Ponto: W09-001 (P1, IMPLEMENTING)
- Problema confirmado: `SeoManager` resolvia Produção pública apenas pelo slug e imagem genérica; Evento já buscava entidade real.
- Alteração: `src/components/SeoManager.js` agora consulta `publicProduction(slug)` e deriva title, description, canonical, OG/Twitter image e JSON-LD `ProfilePage`/`Organization` de dados reais.
- Privacidade/localização: endereço estruturado só é emitido quando `location_public` está habilitado; nenhum país, moeda, disponibilidade, avaliação ou prova social é inventado.
- Fallback: metadata baseada na rota continua ativa quando a API pública falha.
- Código: commit `fa8e9bae6b2f0e556e3425ff3092f7aa615947b1`, branch `w09/production-public-seo`, PR #672.
- Arquivos: `src/components/SeoManager.js`.
- Testes/evidência: revisão estática contra `ProductionPublicPage` e contrato existente de `SeoHead`; consulta de Actions imediatamente após abrir PR retornou zero workflow runs associados ao commit. Portanto ainda não VERIFIED.
- Push/deploy: branch enviada via GitHub; sem merge/deploy nesta execução.
- Pendências: acompanhar CI; validar preview HTTP/crawler real; W09-003 continua necessário porque metadata client-side pode não ser consumida por crawlers sem JavaScript.
- Requests: W01 preservar ownership de hero/layout; W05 considerar PR #669 histórico para coordenação e PR #672 como incremento funcional atual.
