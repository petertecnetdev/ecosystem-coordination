# AUX-03 — Guia de descoberta: como encontrar eventos perto de você na Cutinapp

**Data:** 11/11/2026  
**Área:** aquisição orgânica de participantes, SEO editorial e descoberta pública  
**Estado:** ARTICLE_READY — SOCIAL_CAROUSEL_READY — NOT_PUBLISHED — PUBLIC_RUNTIME_NO_GO

## Objetivo

Atrair participantes que pesquisam eventos na própria cidade ou perto de sua localização, explicando como usar a busca e os filtros reais da Cutinapp. O conteúdo cobre a etapa anterior à compra; não repete o guia de segurança de compra nem o guia de QR Code já preparado.

## Oportunidade e intenção de busca

- **Intenção principal:** encontrar eventos próximos ou na própria cidade.
- **Consultas-alvo:** eventos perto de mim; eventos na minha cidade; shows perto de mim; festas neste fim de semana; eventos gratuitos.
- **Intenção secundária:** filtrar programação por data, preço, formato e gênero.
- **Público:** participantes que ainda estão decidindo o que fazer e precisam reduzir a busca a opções relevantes.
- **Etapa do funil:** descoberta → consideração → página do evento.

Não há volume de busca ou posição orgânica medidos nesta entrega. A seleção é baseada na correspondência entre intenção e funcionalidades confirmadas no código.

## Confirmado — funcionalidades existentes no código

Na versão main consultada:

1. A rota /search abre a busca global.
2. A busca reconhece resultados de eventos, produções, artistas, pessoas, publicações, itens, locais e promoters.
3. Filtros rápidos incluem **Hoje**, **Amanhã**, **Fim de semana**, **Gratuitos**, **Com ingresso** e **Perto de mim**.
4. Filtros adicionais incluem cidade, preço máximo, raio de 5/10/25/50/100 km, formato presencial/online/híbrido e gênero.
5. O filtro **Perto de mim** solicita a localização do navegador; a pessoa também pode informar uma cidade manualmente.
6. A rota /cidades lista cidades que possuem próximos eventos disponíveis e informa a quantidade de eventos retornada para cada cidade.
7. As páginas /eventos, /eventos/:cidade, /eventos/:cidade/:período e /eventos/:cidade/categoria/:categoria compõem a descoberta pública.
8. A página de descoberta mostra resultados e oferece o CTA **Ver evento e ingressos**.

**Limite:** estas são capacidades encontradas no código, não uma confirmação de que as rotas estão funcionando no ambiente público neste momento.

## Entregável 1 — artigo pronto para revisão editorial

### SEO

- **H1:** Como encontrar eventos perto de você na Cutinapp
- **SEO title:** Eventos perto de mim: como encontrar na Cutinapp
- **Slug:** como-encontrar-eventos-perto-de-voce
- **Meta description:** Descubra como encontrar eventos na sua cidade, filtrar por data, preço, formato e gênero e escolher sua próxima experiência na Cutinapp.
- **Canonical pretendida:** https://cutinapp.petertecnet.com.br/blog/como-encontrar-eventos-perto-de-voce
- **Open Graph title:** Encontre eventos que combinam com você | Cutinapp
- **Open Graph description:** Use cidade, localização e filtros para descobrir eventos na Cutinapp.
- **Intenção:** descoberta local e exploração de programação.
- **Links internos propostos:** /search, /cidades, /eventos.

---

# Como encontrar eventos perto de você na Cutinapp

Nem sempre você já sabe qual evento quer encontrar. Às vezes, a ideia é mais simples: descobrir o que acontece na sua cidade, encontrar um show para o fim de semana ou procurar uma experiência que combine com seu estilo.

A busca da Cutinapp reúne eventos e outros resultados da plataforma. Com alguns filtros, você consegue reduzir a pesquisa por localização, data, preço, formato e gênero.

## 1. Comece pela busca

Abra a busca da Cutinapp e digite o nome do evento, artista ou produção que deseja encontrar.

Se ainda não tiver algo específico em mente, explore os resultados disponíveis. Além de eventos, a busca também permite encontrar artistas, produções e locais, entre outros tipos de conteúdo.

## 2. Escolha sua cidade ou use “Perto de mim”

Se você já sabe onde quer sair, informe a cidade no filtro correspondente.

Se preferir descobrir opções próximas, use **Perto de mim**. O navegador poderá solicitar autorização para compartilhar sua localização. Essa permissão serve para calcular a proximidade; você pode optar por não concedê-la e pesquisar informando a cidade manualmente.

A busca também permite ajustar o raio de distância para 5, 10, 25, 50 ou 100 quilômetros.

## 3. Escolha o melhor dia

Use os atalhos de período para concentrar a pesquisa:

- Hoje;
- Amanhã;
- Fim de semana.

Assim, você pode começar pelo momento em que pretende sair, em vez de percorrer uma lista sem relação com sua disponibilidade.

## 4. Defina o tipo de ingresso e o orçamento

A busca oferece filtros para eventos **Gratuitos** e eventos **Com ingresso**.

Também é possível informar um preço máximo. Use esse filtro para limitar a pesquisa ao valor que pretende considerar.

Confira sempre os valores e as condições apresentados na página do evento antes de concluir qualquer compra.

## 5. Escolha o formato e o gênero

Nem toda experiência precisa acontecer no mesmo lugar. O filtro de formato contempla opções presenciais, online e híbridas.

Se estiver procurando um estilo específico, informe também o gênero desejado. Isso ajuda a refinar a descoberta sem depender apenas do nome de um evento.

## 6. Explore cidades com programação disponível

Se quiser conhecer a programação de outros lugares, abra o diretório de cidades.

A página apresenta cidades com próximos eventos disponíveis e indica quantos eventos foram encontrados em cada uma. Quando não houver programação pública para uma cidade, ela não deve ser apresentada como se tivesse eventos confirmados.

## 7. Abra a página do evento antes de decidir

Quando encontrar algo interessante, abra a página correspondente e confira as informações publicadas: data, horário, local, atrações, descrição, opções de ingresso e condições de entrada.

Se o evento fizer sentido, avance pelo botão **Ver evento e ingressos**. Se estiver combinando a saída com outras pessoas, compartilhe a página pública do evento para que todos consultem as mesmas informações.

## Perguntas frequentes

### Preciso permitir minha localização para encontrar eventos?

Não. Você pode informar uma cidade manualmente. A localização do navegador é necessária apenas se quiser usar o filtro **Perto de mim**.

### Posso encontrar eventos gratuitos?

Sim. A busca possui o filtro **Gratuitos**. Confira os detalhes da página para verificar as condições de participação.

### Consigo procurar eventos de um gênero específico?

Sim. O filtro de gênero permite refinar a busca por uma preferência informada.

### Posso procurar eventos online?

Sim. O filtro de formato inclui presencial, online e híbrido.

### Como vejo quais cidades têm eventos?

Acesse o diretório de cidades. Ele apresenta as cidades com próximos eventos disponíveis na Cutinapp.

## Encontre sua próxima experiência

Você não precisa começar sabendo o nome do evento. Escolha a cidade, o dia ou o tipo de experiência que procura e refine a busca até encontrar algo que combine com seus planos.

**CTA principal: Explorar eventos na Cutinapp.**  
**CTA secundário: Ver cidades com eventos.**

---

## Entregável 2 — carrossel Instagram (6 telas)

**Formato:** 1080 × 1350, mobile-first, identidade oficial Cutinapp, uma mensagem principal por tela.

1. **Gancho:** “Quer sair, mas ainda não sabe para onde?” Apoio: “Descubra eventos pela busca da Cutinapp.”
2. **Localização:** “Comece pela sua cidade ou use Perto de mim.” Apoio: “Você também pode escolher a distância.”
3. **Data:** “Hoje, amanhã ou fim de semana?” Apoio: “Encontre opções para o dia que combina com seus planos.”
4. **Orçamento e ingresso:** “Gratuitos ou com ingresso?” Apoio: “Use o filtro de preço máximo para refinar.”
5. **Seu estilo:** “Presencial, online, híbrido e por gênero.” Apoio: “Ajuste a busca ao tipo de experiência que procura.”
6. **Fechamento:** “Sua próxima experiência começa pela descoberta.” CTA: “Salve este guia e explore a busca da Cutinapp.”

### Legenda pronta

Seu próximo evento não precisa começar por um nome que você já conhece.

Na busca da Cutinapp, você pode explorar por cidade, usar **Perto de mim**, escolher o período e refinar por preço, formato e gênero.

Quer encontrar algo para hoje, amanhã ou para o fim de semana? Comece pelo que faz sentido para seus planos.

**CTA:** salve este guia e compartilhe com quem está procurando o próximo rolê.

#Cutinapp #Eventos #Shows #Festas #EventosPertoDeMim

## Entregável 3 — Stories (3 telas)

**Story 1 — descoberta**  
“Qual é o seu plano para os próximos dias?”  
Enquete: “Quero sair” / “Ainda estou procurando”.

**Story 2 — demonstração editorial**  
“Na busca da Cutinapp, refine por cidade, localização, data, preço, formato e gênero.”

**Story 3 — CTA**  
“Descubra sua próxima experiência.”  
Sticker de link para /search, **somente depois do GO do runtime público**.

## Direção visual

- Usar o logo e a identidade oficial vigentes da Cutinapp.
- Carrossel 4:5; Stories 9:16.
- Preferir tipografia grande, contraste alto e exemplos abstratos de filtros.
- Não simular uma tela real do aplicativo. Se houver captura de tela, usar gravação atual da interface real após validação.
- Não usar flyer, artista, cidade, evento, preço ou disponibilidade que não tenham sido confirmados.

## Canal, CTA e métrica

- **Canal:** artigo do blog + carrossel + Stories.
- **CTA do artigo:** Explorar eventos / Ver cidades com eventos.
- **CTA social:** salvar e compartilhar o guia; sticker para busca somente após GO.
- **Métrica principal:** sessões que chegam a uma página de evento a partir do artigo ÷ sessões orgânicas do artigo.
- **Métricas secundárias:** impressões, cliques, CTR, uso da busca, filtros aplicados, visualizações de eventos, início de checkout e compra atribuída.
- **Atribuição proposta:** blog_descoberta_eventos_20261111 e ig_descoberta_eventos_20261111. São códigos editoriais propostos, não eventos de analytics já instrumentados.
- **Baseline:** N/D. Não há dados de publicação, tráfego ou conversão nesta entrega.

## Hipótese

Um guia que explica filtros reais pode reduzir a fricção de descoberta para participantes que ainda não escolheram um evento. O resultado precisa ser medido por visitas às páginas de evento e início de checkout, não apenas por visualizações do artigo.

## Gate de publicação

**NO-GO para publicar links de conversão enquanto a issue P0 #643 permanecer aberta e o runtime público não tiver sido validado.**

O artigo e as peças sociais podem permanecer em revisão editorial. Antes de inserir stickers ou CTAs para /search, /cidades ou /eventos, confirmar a abertura dessas rotas em smartphone, Wi-Fi e rede móvel.

## Próxima ação

1. Conta principal/infra resolve e valida o serving público da Cutinapp.
2. Responsável editorial revisa e aprova o artigo.
3. Publicar o artigo como rascunho no CMS; não anunciar indexação até confirmar URL pública e HTML servido.
4. Após GO, publicar carrossel/Stories e inserir links rastreáveis.
5. Medir sessões do artigo que avançam para páginas de eventos e checkout.

**Precisa da conta principal:** SIM — liberação do runtime público e aprovação/publicação dos ativos.

## Estado

ARTICLE_READY — SOCIAL_CAROUSEL_READY — NOT_PUBLISHED — NOT_INDEXED — NO_EVENT_EXAMPLES_INVENTED — PUBLIC_RUNTIME_NO_GO — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY.
