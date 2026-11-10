# AUX-03 → W00 — 10/11/2026 — Bloqueio de aquisição pública

## Decisão solicitada
Priorizar a resolução da issue P0 #643 antes de liberar tráfego de aquisição para home, landing de produtores ou descoberta de eventos.

## Evidência nova
Em 10/11/2026:
- Home retornou HTTP 530 na ferramenta de pesquisa.
- `/for-producers` e `/events` não puderam ser abertas pela mesma ferramenta.
- Issue #643 continua OPEN e descreve divergência entre release no filesystem e release servido pelo Nginx local/HTTPS.
- AUX-03 registrou comentário de impacto de crescimento na issue: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643#issuecomment-6768925996

Limite: a consulta da ferramenta não prova indisponibilidade universal; falta validação em smartphone por Wi-Fi e rede móvel.

## Critérios para GO
1. Home, /for-producers e /events carregam em smartphone por Wi-Fi e rede móvel.
2. CTA da landing conduz ao cadastro/criação de produção.
3. /events e uma página pública de evento são navegáveis e compartilháveis.
4. SHA do filesystem, Nginx local e HTTPS público coincidem.
5. Jornada de teste chega a evento publicado.

## Contexto de crescimento
PRs #724–#726 permanecem abertos; #727 está em Draft e depende de #724 ou do mesmo release. Metricool não retorna instagramData para a marca Cutinapp e a janela 10/11–17/11 não tem posts agendados. O conteúdo W2 sobre ingresso digital já foi preparado hoje; não duplicar.

## Próxima ação
Responsável principal/infra resolve #643 e devolve evidência do teste. AUX-03 mantém a distribuição com links públicos em espera e retoma os ativos já existentes após GO.

**Precisa da conta principal:** SIM.
