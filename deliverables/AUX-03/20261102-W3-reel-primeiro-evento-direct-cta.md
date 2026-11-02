# AUX-03 W3 — Reel de aquisição: prepare seu primeiro evento

**Data:** 02/11/2026  
**Área:** aquisição e ativação de produtores  
**Status:** COPY_READY — NOT_SCHEDULED — NOT_PUBLISHED

## Objetivo
Gerar conversas qualificadas com produtores que já têm um próximo evento em planejamento, sem enviar tráfego para a landing pública enquanto sua oferta comercial e sua jornada mobile ainda aguardam validação.

## Oportunidade e obstáculo atacado
O maior bloqueio confirmado nesta execução está entre o interesse e o cadastro: a versão de `main` de `src/pages/ProducerLandingPage.js` ainda anuncia trial de 30 dias, assinatura obrigatória e CTAs de trial, enquanto `config/subscriptions.php` da API define Cutinapp com `subscription_enabled=false`, `monetization_model=transaction_fee` e `plans=[]`. O PR #724 contém a correção, mas continua aberto.

A rota pública `/for-producers` não pôde ser inspecionada pelo navegador de pesquisa. A home abriu somente com o shell “Ative o JavaScript”. Isso **não** prova indisponibilidade global; apenas impede validar a experiência pública por esse meio.

**Decisão de distribuição:** o Reel usa CTA por Direct e não inclui link para a landing. Assim, capta interesse sem encaminhar o produtor para a oferta contraditória.

## Confirmado
- A landing em `main` contém as mensagens de trial/assinatura e o CTA “Iniciar trial grátis”.
- A configuração da API mantém Cutinapp no modelo por taxa de transação, sem assinatura obrigatória.
- PRs #724, #725 e #726 aparecem na consulta atual como abertos; nenhum merge foi confirmado.
- Metricool reconhece a marca `cutinapp` (ID 7119630), mas `networksData` retorna somente `gbpData`; não há publicador Instagram conectado nessa marca.
- A consulta de posts agendados de 02/11 a 09/11/2026 retornou lista vazia.
- A consulta de métricas do Google Business Profile retornou valores 0 para cliques e ações no período consultado. Isso é evidência do conector, não prova de ausência total de alcance ou atividade orgânica.
- A busca pública não encontrou eventos da Cutinapp indexados com os termos consultados nesta execução. Por segurança, o roteiro não menciona evento, artista, preço, local ou data específicos.

## Hipótese
Um CTA por Direct pode reduzir o abandono causado pela landing ainda não validada e permitir qualificar produtores antes de encaminhá-los ao cadastro. Não há resposta, lead, cadastro ou ativação medidos que comprovem essa hipótese.

## Entregável — Reel de 25 segundos

### Roteiro por cena
| Tempo | Imagem / ação | Texto na tela | Locução |
|---|---|---|---|
| 0–3s | Tipografia cinética; calendário simples, sem data/evento fictício | **Seu evento já tem data. Está pronto para ser publicado?** | “Seu evento já tem data. Mas ele está pronto para ser publicado?” |
| 3–7s | Palavras entram uma a uma em tela | Nome • data • horário • local | “Comece organizando as informações que o público precisa encontrar.” |
| 7–12s | Cartões tipográficos, sem simular telas do produto | Descrição • ingressos • condições | “Se houver ingressos, revise lotes, valores e condições antes de divulgar.” |
| 12–18s | Moldura de smartphone com checklist textual; não usar interface fictícia | **Revise no celular antes de compartilhar** | “Confira como as informações aparecem no celular e corrija qualquer divergência.” |
| 18–25s | Logo oficial fornecido, sem redesenho; CTA em alto contraste | **Quer preparar seu primeiro evento?** Envie **PRIMEIRO EVENTO** no Direct. | “Quer preparar seu primeiro evento na Cutinapp? Envie PRIMEIRO EVENTO no Direct.” |

### Direção de produção
- Vertical 9:16, duração de 25 segundos, legendas embutidas e leitura confortável em tela pequena.
- Usar a paleta exata do logo oficial vigente; não introduzir roxo ou cores fora da identidade aprovada.
- Usar apenas o arquivo oficial do logo. Não redesenhar nem gerar interface falsa.
- Se forem inseridas capturas de tela, gravar a interface real em ambiente autorizado; caso contrário, manter tipografia e cartões abstratos.
- Não usar imagens de eventos, artistas, casas, ingressos ou depoimentos sem autorização.
- Não afirmar trial, assinatura, taxa zero, alcance garantido ou venda garantida.

### Legenda pronta
Seu evento não começa quando o flyer fica pronto. Antes de divulgar, deixe as informações organizadas:

• nome, data e horário;  
• cidade e local ou formato;  
• descrição objetiva;  
• ingressos e condições, quando houver;  
• página revisada no celular.

A proposta da Cutinapp para produtores é conduzir a preparação do evento até a publicação e o compartilhamento.

Quer preparar seu primeiro evento? Envie **PRIMEIRO EVENTO** no Direct.

#Cutinapp #ProdutoresDeEventos #ProduçãoDeEventos #Eventos #IngressosOnline

### Sequência complementar de Stories
1. **Story 1:** “Você já tem data para o próximo evento?” — enquete: “Sim” / “Ainda estou definindo”.
2. **Story 2:** “Antes de divulgar: nome, data, horário, local e descrição precisam estar certos. Se houver ingressos, revise também lotes e condições.”
3. **Story 3:** “Quer organizar seu primeiro evento na Cutinapp? Responda **PRIMEIRO EVENTO** no Direct.”

### Resposta inicial de Direct
“Recebi sua mensagem sobre o primeiro evento. Qual é a cidade e a data prevista? Assim consigo orientar o próximo passo de preparação.”

**Regra operacional:** não encaminhar o link `/for-producers` até a conta principal integrar/revisar o PR #724 e validar cadastro e navegação em smartphone real. Não pedir documentos nem dados pessoais por Direct.

## Canal, CTA e métrica
- **Canal:** Instagram Reels + Stories, publicação manual após aprovação; integração publicadora do Instagram não está confirmada no Metricool.
- **CTA:** enviar **PRIMEIRO EVENTO** no Direct.
- **Métrica principal:** produtores qualificados que publicam o primeiro evento em até 7 dias ÷ produtores qualificados que enviam a palavra-chave.
- **Métrica intermediária:** DMs qualificadas por 1.000 contas alcançadas.
- **Lead qualificado:** produtor ou representante autorizado + cidade + data prevista/confirmada do evento.
- **Atribuição manual sugerida:** `ig_reel_primeiro_evento_20261102`; não representa evento técnico já instrumentado.
- **Janela:** 7 dias após publicação.
- **Baseline:** N/D. O Reel e os Stories não foram publicados.

## Próxima ação
1. Conta principal aprovar o roteiro e fornecer/confirmar o acesso para publicação manual ou conectar o Instagram ao Metricool.
2. Publicar Reel e sequência de Stories sem link para a landing.
3. Registrar alcance, DMs, leads qualificados, produções criadas e primeiro evento publicado.
4. Em paralelo, revisar/integrar PR #724 e validar a landing em 320/360/390/430 px antes de ativar CTA com link.

## Dependência da conta principal
**SIM** — aprovação editorial e acesso de publicação; integração/revisão do PR #724 e validação mobile para liberar o link da landing.

## Estado final
`COPY_READY — NOT_SCHEDULED — NOT_PUBLISHED — NO_OUTREACH_SENT — NOT_DEPLOYED`.
