# AUX-03 — Instagram Stories: pesquisa rápida com produtores

**Data:** 03/11/2026  
**Área:** aquisição de produtores, Instagram Stories, pesquisa de demanda e comunicação.  
**Prioridade:** P2.  
**Estado:** ASSET_READY — NOT_SCHEDULED — NOT_PUBLISHED.

## Objetivo
Identificar produtores/organizadores entre os espectadores e captar, por resposta voluntária, qual etapa mais dificulta a produção. A ação busca gerar conversas qualificadas e informação direta para orientar futuras mensagens de aquisição da Cutinapp.

## Oportunidade
Os dois materiais W1 imediatamente anteriores foram um checklist pré-publicação (01/11) e um Reel sobre organização da lista de participantes (02/11). Esta ação muda o formato e o objetivo: sequência interativa de Stories para qualificar quem produz e descobrir desafios de atração de público e venda de ingressos, sem repetir os temas anteriores.

## Trabalho realizado
- Consultados `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/README.md`, diretórios `claims/active/` e `claims/completed/`, plano `CUTINAPP_COLD_START_GROWTH.md`, atribuição `orchestration/assignments/AUX-03/W1.md` e worklogs recentes.
- Verificado que não há claim AUX-03 ativo no diretório `claims/active/`; o checklist de 01/11 e o Reel de 02/11 estão registrados como concluídos, com publicação pendente.
- Verificadas configurações Metricool: brand `cutinapp`, ID `7119630`, timezone `America/Sao_Paulo`; `networksData` retornou somente `gbpData`, sem conexão Instagram identificada.
- Consultados analytics de feed posts e Reels de 20/10 a 03/11: ambos retornaram `rows: []`. Agendamentos de 03/11 a 10/11 também retornaram `data: []`. Esses resultados não comprovam ausência de publicações feitas diretamente no Instagram.
- A busca pública e a abertura direta de `instagram.com/cutinapp/` não forneceram conteúdo verificável. Bio, destaques, Stories e posts recentes não foram inspecionados; não são apresentados como auditados.
- Produzidos e revisados visualmente três arquivos PNG mobile-first, 1080×1920, com identidade tipográfica escura e acentos azul/roxo; as áreas de sticker ficam livres para inserir os controles nativos do Instagram.

## Entregável
Pacote anexado à execução: `20261103-AUX-03-W1-story-pesquisa-produtores-kit.zip`.

Arquivos:
- `story-01-enquete-produtora.png`
- `story-02-desafio.png`
- `story-03-caixa-perguntas.png`
- `roteiro-cta-metricas.md`

### Story 1 — qualificação
Texto: **“Você produz eventos? Queremos ouvir quem está por trás de cada produção.”**

Sticker Enquete:
- Pergunta: “Você trabalha com eventos?”
- Opções: “Sim, produzo” / “Estou começando”

### Story 2 — desafio
Texto: **“O que mais desafia sua produção hoje? Toda produção tem etapas que exigem mais atenção. Qual pesa mais na sua?”**

Sticker Enquete:
- Pergunta: “Qual é o maior desafio?”
- Opções: “Atrair público” / “Vender ingressos”

### Story 3 — resposta aberta
Texto: **“Qual etapa você gostaria de simplificar? Se pudesse resolver um único obstáculo na sua próxima produção, qual seria?”**

Sticker Caixa de Perguntas:
- Prompt: “O que mais trava sua produção hoje?”
- Complemento: “Responda com a etapa e, se puder, explique o motivo.”

## Canal e CTA
**Canal:** Instagram Stories, três frames em sequência.  
**CTA:** responder às duas enquetes e contar no último Story qual etapa mais exige tempo.

## Métrica
- **Principal:** respostas à caixa de perguntas ÷ alcance do Story 3.
- **Qualificação:** quantidade de perfis identificáveis de produtores/organizadores que responderem.
- **Secundárias:** votos nas duas enquetes, visitas ao perfil e DMs iniciadas a partir dos Stories.
- **Janela:** 24 horas após publicação.
- **Baseline:** N/D; não há analytics Instagram disponíveis nesta conexão.

## Confirmado
- A sequência de conteúdo W1 recente consultada foi: checklist pré-publicação (01/11) e Reel sobre listas de participantes (02/11).
- Metricool brand `7119630` tem timezone `America/Sao_Paulo`; configurações retornaram apenas `gbpData`, sem `instagramData`.
- Analytics de feed e Reels retornaram listas vazias e a consulta de agendamentos 03/11–10/11 retornou lista vazia.
- Abertura do perfil público Instagram não foi possível nesta execução.

## Hipótese
Enquetes simples podem reduzir a fricção para o produtor se identificar e responder. A caixa aberta pode revelar objeções reais de aquisição, divulgação ou venda. Isso ainda precisa ser validado pelas respostas e métricas após publicação.

## Recomendação / próxima ação
A conta principal deve publicar os três frames em sequência, adicionando os stickers nativos nas áreas reservadas. Responder manualmente aos produtores que se identificarem; não usar respostas como depoimento sem autorização. Registrar votos, alcance, respostas e DMs após 24 horas.

## Evidências dos arquivos
- `story-01-enquete-produtora.png` SHA-256: `c91996c89c58fee0b68536863cd61ed614d8df97716b3795a41a0f6a65ace593`
- `story-02-desafio.png` SHA-256: `89a62bfcc1deba102832e72d1ca652330719837c62d568233ba5afd2f04a743e`
- `story-03-caixa-perguntas.png` SHA-256: `32fdde5378ce1bffe50c97e814447ffdbd6598ee795287505784bab32fcb47e`
- `roteiro-cta-metricas.md` SHA-256: `94932e47194158f32811b7fa8ca5d76d6409caf8d4770e7f667ea467feb0be1f`

**Precisa da conta principal:** SIM — acesso publicador ao Instagram para inserir stickers, publicar e coletar Insights.  
**VPS/código:** nenhuma alteração.
