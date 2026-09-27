# Handoff
from: Cutinapp Visual Coordenação (W05)
to: W01 / W04
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: action-required

## Context
O usuário forneceu três screenshots reais de produção em 2026-09-27 mostrando problemas sistêmicos de UI/UX nas views principais da Cutinapp.

## Screenshot 1 — Evento
- hero ocupa área demais e a composição esquerda/direita fica desequilibrada;
- flyer domina a tela enquanto o conteúdo principal parece um card administrativo solto;
- excesso de ações pequenas e de mesmo peso visual;
- CTA "Ingressos e itens" quebra texto e parece apertado;
- espaço vertical desperdiçado antes do conteúdo seguinte;
- pouca integração visual entre flyer, background e bloco de informações;
- WhatsApp verde conflita com a identidade preta/grafite/vermelha.

## Screenshot 2 — Produção / modal "Quem visualizou"
- contraste crítico: linhas cinza-claro + textos claros/faint tornam nomes, datas e contagens difíceis de ler;
- metadata muito pequena;
- hierarquia ruim entre nome, última visita e quantidade de visitas;
- modal parece um bloco Bootstrap genérico dentro de uma página escura;
- precisa contraste AA, tipografia maior, superfícies sólidas e linha selecionável clara;
- ação/fechamento do modal precisa ser evidente.

## Screenshot 3 — Produção / Próximo evento
- ProductionNextEventHero está superdimensionado;
- próximo evento está funcionando como um segundo hero da página e rouba protagonismo da Produção;
- mídia horizontal/cortada perde a identidade do flyer;
- o componente ocupa largura/altura excessiva para uma informação de continuidade;
- CTA e metadata ficam pequenos em relação ao banner;
- precisa virar preview premium compacto: poster/flyer completo, data/local/preço claros, 1 CTA principal + agenda secundária, altura controlada e excelente comportamento mobile.

## Direção visual
- reduzir exageros de escala;
- aumentar legibilidade de textos pequenos;
- diminuir quantidade de cartões/caixas competindo entre si;
- usar hierarquia consistente: entidade > contexto > ações;
- preservar flyer inteiro quando ele for material editorial;
- deixar mídia colorir o ambiente sem transformar tudo em banner gigante;
- superfícies sólidas, sem opacity/transparências decorativas;
- preto/grafite/vermelho oficial Cutinapp;
- evitar Bootstrap default;
- validar desktop 1366/1440/1920 e mobile 360/390/430.

## Requested action
W01: corrigir EventView, ProductionView/Public e ProductionNextEventHero sem transformar cada seção em hero.
W04: revisar tokens/componentes compartilhados de modal, contraste, botões, tipografia e densidade para impedir recorrência.
Registrar antes/depois e não marcar VERIFIED somente por build verde.
