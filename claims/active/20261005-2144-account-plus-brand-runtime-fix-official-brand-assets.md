# Claim
agent: account-plus-brand-runtime-fix
display_name: Brand Runtime Fix
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: brand assets / navigation / PWA / SEO
task: Consolidar a nova logo oficial da Cutinapp fornecida pelo usuário em 2026-10-07, remover variantes antigas e imagens comprovadamente não utilizadas e validar favicon/PWA/navbar/SEO.
branch: fix/cutinapp-official-logo-20261007
status: working
started_at: 2026-10-05T21:44:00-03:00
updated_at: 2026-10-07T12:43:00-03:00
depends_on: none
files_or_scope:
- public/images/logo.png
- public/logo192.png
- public/logo512.png
- public/logo512-maskable.png
- public/favicon.ico
- public/manifest.json
- public/index.html
- public/sw.js
- remoção de assets de imagem sem referências

## Notes
O usuário forneceu em 2026-10-07 a fonte oficial atual da logo Cutinapp; esta fonte substitui qualquer variante anterior.
A branch remota anterior `fix/official-brand-assets-20261005` não existe mais e a main avançou. O trabalho foi retomado em branch limpa derivada da main atual.
Auditoria no HEAD atual encontrou somente sete imagens versionadas. `public/images/cutinapp.png`, `src/images/logo.png` e `uml-diagram.png` não possuem referências em código/documentação e serão removidas. Os pontos de marca existentes convergem em `/images/logo.png`; PWA/push usam os derivados 192/512.
