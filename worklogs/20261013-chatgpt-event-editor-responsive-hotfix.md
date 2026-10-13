# Cutinapp — event-create responsive hotfix
operator: Event Editor Hotfix (chatgpt-event-editor-hotfix-20261013)
status: RUNTIME SHA VERIFIED; browser-auth visual QA pending
priority: P1 conversion/onboarding
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Diagnóstico
A criação do evento reutilizava grid da página pública com `display: contents`. A ajuda de upload era um item sem área de grid explícita e aparecia cortada na margem esquerda. O fluxo de publicação tinha botões repetidos e o cadastro rápido da produção carecia de hierarquia.

## Implementação
- Remoção de `imageHelp` e de sua renderização órfã (validação e conversão do flyer 1024 × 1536 permanecem).
- CTA duplicado removido da faixa de resumo (outras ações de salvar preservadas).
- Cadastro rápido de produção reorganizado em passos Produção/Evento/Ingressos, com campo acessível.
- CSS responsivo limitado ao editor de evento, datas, seleção da produção e correção de grid desktop.

## Evidência
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/712
- merge main: d691af9c729bb7fb7a07eb6b07e67de063e24230
- CI PR/main: 38407282426 / 38407649528 — passed
- GitHub Actions outbound artifact: 38407718008 — passed
- Deploy manual VPS a partir do artefato GH, sem compilar localmente.
- Nginx localhost HTTP e HTTPS público `/release-sha.txt`: d691af9c729bb7fb7a07eb6b07e67de063e24230.
- Branch temporária excluída e 404 confirmado.

## Follow-up
- W4 QA mobile/tablet/desktop (320/360/390/430+): viewport scroll/horizontal overflow, campos date/production, upload, publish, autopublish, first ticket.
- Investigar reachability SSH GitHub-hosted runner -> VPS; deploy padrão falhou no run 38402578896 por timeout, fallback artifact/Remote Desktop foi necessário.
- W00 deve classificar Independence e AUX branch antes de exclusões.
