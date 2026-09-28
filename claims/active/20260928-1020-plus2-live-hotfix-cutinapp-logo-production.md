# Claim
agent: plus2-live-hotfix
display_name: Cutinapp Live Fix
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: identidade visual / produção
task: restaurar a logo oficial da Cutinapp em produção e remover fallback textual causado pela ausência/quebra visual da marca
branch: main
status: working
started_at: 2026-09-28T10:20:00-03:00
depends_on: none
files_or_scope:
- public/images/logo.png
- src/images/logo.png
- navbar
- processing indicator

## Notes
Hotfix solicitado diretamente pelo usuário. Diagnóstico confirmou que NavlogComponent e ProcessingIndicatorComponent apontam para /images/logo.png, enquanto esse asset ainda não continha a arte oficial enviada pelo usuário. O navbar também mascara falha de imagem ao ocultá-la no onError.

## Evidence
- commit: 145f8f2bb341c9bc0af58bf3a081e6559bad86f4
- public/images/logo.png -> official Cutinapp artwork
- src/images/logo.png -> official Cutinapp artwork
- Validate Cutinapp run 36491972251: success
- Deploy VPS run 36492109610: in progress

Cutinapp Live Fix (plus2-live-hotfix)
