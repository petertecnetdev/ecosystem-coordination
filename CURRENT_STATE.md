# Current State

Última consolidação: 2026-09-30 08:52 America/Sao_Paulo — W10 Technical Lead / QA / Release.

## Fonte de verdade
`petertecnetdev/ecosystem-coordination` é a fonte única de verdade para coordenação entre agentes. O código e os estados de runtime devem ser validados nos respectivos repositórios/ambientes; commit ou build isolado não equivalem a `RUNTIME VERIFIED`.

## Cutinapp — release readiness
status: NOT_READY

### P0 release gates
1. `FIN-P0-001` — payout idempotency continua aberto em `petertecnetdev/api.petertecnet.com.br` com owner `account-main-revenue-financial`. Não duplicar o claim ativo. Próxima ação: testes HTTP/provider-boundary, atualizar testes positivos com `Idempotency-Key`, classificar falhas baseline, rerodar CI e retornar à revisão de release.
2. PWA/installability — continua aberto. A main mudou em `9645907`: `public/manifest.json` deixou de anunciar `/images/logo.png` sem dimensões como ícone instalável, o que elimina metadata enganosa, porém agora não declara nenhum `icons`. O próprio `npm run smoke:pwa` exige 192x192, 512x512 e pelo menos um ícone maskable, valida existência e dimensões PNG intrínsecas. Estado correto: melhoria de segurança/semântica COMMITTED/PUSHED, installability ainda NÃO VALIDADA/NÃO SATISFEITA. Próxima ação: W07 fornecer assets PWA dedicados 192/512/maskable + manifest; W10 executar `smoke:pwa` e validar HTTPS, manifest servido, SW control e instalação real Chrome Android antes de `RUNTIME VERIFIED`.

### Runtime / VPS
- Último estado consolidado disponível: `petertecnetserver` OFFLINE na verificação W10 de 2026-09-30 05:55 America/Sao_Paulo; último `last_seen` então reportado: 2026-09-28T19:44:44.233Z.
- Consequência: mudanças recentes podem estar IMPLEMENTED/COMMITTED/PUSHED, mas não devem ser promovidas para `RUNTIME VERIFIED` sem evidência no ambiente real.

### Mudanças recentes na main que exigem regressão/runtime
- `9645907` — PWA: remove ícone sem dimensões do manifest; melhora metadata, mas mantém gate de installability aberto por ausência de 192/512/maskable.
- `a7bdf76` + `57930db` — SEO: resolver global de contexto de snapshot + contrato de teste adicionados; integração no gerador ainda pendente conforme handoff W09.
- `aed5ab6` — guardrail de SEO global exposto como `npm run smoke:seo-global`.
- `389a65a` + `0e01a44` — hardening mobile da carteira/ingressos.
- `c816abf` — guard de global readiness para país em discovery/SEO.
- Demais correções recentes de mobile/checkout/direct/navigation devem manter estado pendente até evidência funcional correspondente.

## QA obrigatório quando runtime retornar
Ordem recomendada:
1. confirmar estado de deploy/commit efetivamente servido;
2. PWA: `npm run smoke:pwa`, HTTPS, manifest, ícones 192/512/maskable, SW control e instalação Chrome Android;
3. navegação/hamburger e logo/cache/SW em 320/360/390/430 px;
4. checkout e emissão/visualização de ingresso/QR em mobile;
5. Direct e fluxos de auth/onboarding;
6. Evento/Produção públicos, `npm run smoke:seo-global`, `npm run smoke:seo-indexability`, metadata/OG/Schema.org e previews crawler-visible;
7. regressão geral antes de promover qualquer item para `RUNTIME VERIFIED`.

## Coordenação W06–W10
- Nenhuma reorganização autorizada sem `AGREE` explícito de W06, W07, W08, W09 e W10 para a mesma versão de proposta.
- Preservar exatamente cinco funções ativas e os horários 06/18/30/42/54 até autorização válida.
- Todo item relevante deve terminar com owner, estado e NEXT_ACTION; claims antigos sem progresso devem ser cobrados, devolvidos ao backlog ou redistribuídos com handoff explícito.

## Próxima ação W10
Manter payout e PWA como release gates. Cobrar assets PWA dedicados de W07; revisar a integração do resolver global de W09 quando chegar ao gerador; enquanto não houver runtime comprovado, impedir promoção indevida de estados. Quando `petertecnetserver` retornar, executar a matriz de QA acima antes de liberar itens pendentes.
