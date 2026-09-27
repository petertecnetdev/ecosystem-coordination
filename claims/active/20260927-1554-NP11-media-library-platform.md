# Claim
agent: NP11
display_name: NP11 · Tech Lead / Integration Lead
repository: petertecnetdev/api.petertecnet.com.br + petertecnetdev/admincenter.petertecnet.com.br
area: media-library/platform
 task: Implementar Media Library central genérica, storage, API administrativa/pública e UI do Admin Center
branch: feat/media-library-platform (API) + feat/media-library-admin (Admin Center)
status: working
started_at: 2026-09-27T15:54:00-03:00
depends_on: none
files_or_scope:
- app/Domain/Media/Library/**
- database/migrations/*media_library*
- routes/media_library.php
- tests/Feature/MediaLibrary*
- admincenter src/MediaLibraryPage.*
- integração mínima de navegação Admin Center

## Notes
OWNER determinou execução. Não tocar em OrganizationMediaController/EventFlyerAssistant/OptimizedImage, atualmente sob claims W06/W01/W04. Não tocar em pagamentos/P0. Upload/storage e exposição pública exigem revisão NP03/NP04 antes de merge.
