# Decision Discovery

## Princípio

Descubra por que uma decisão é necessária antes de comparar tecnologias ou escrever o ADR. Não transforme `UNKNOWN` em fato assumido nem opção ou recomendação em decisão. A interação acontece primeiro na conversa; não gere arquivo a cada rodada.

## Problem framing

Formule a decisão como necessidade ou capacidade a definir, não como duelo entre soluções sugeridas. Separe:

```text
Necessidade: definir como propagar atualizações entre A e B.
Solução candidata: Kafka.
```

Antes de enquadrar como “Kafka vs RabbitMQ”, confirme que mensageria é realmente uma classe de solução aplicável. Investigue requisitos que podem mudar o espaço de alternativas, como sincronismo, bloqueio do produtor, replay, ordering e delivery guarantee.

## Classificação obrigatória

- `CONFIRMED FACT`: informação confirmada pelo usuário ou fonte confiável.
- `EXISTING CONSTRAINT`: restrição técnica, organizacional, legal ou operacional estabelecida.
- `EXISTING DECISION`: decisão vigente registrada por fonte confiável.
- `DECISION ASSUMPTION`: hipótese ainda não confirmada, usada apenas em draft.
- `OPEN DECISION QUESTION`: informação ausente capaz de alterar a decisão.
- `PROPOSED OPTION`: alternativa em análise.
- `RECOMMENDED OPTION`: alternativa favorecida pela análise, ainda não aceita.
- `CONFIRMED DECISION`: escolha efetivamente confirmada, com fonte.

Registre a proveniência material, como `NFR-004`, `ADR-002`, Platform Constraint ou User Confirmation.

## O que descobrir

- **Decision Context:** problema ou pressão arquitetural que exige a decisão.
- **Decision Drivers:** requisitos aplicáveis, como consistência, disponibilidade, segurança, compatibilidade, custo e operabilidade.
- **Constraints:** limites já estabelecidos.
- **Alternatives:** opções plausíveis no contexto.
- **Trade-offs:** benefícios, custos e riscos de cada opção.
- **Consequences:** efeitos esperados da escolha.
- **Decision Status:** escolha confirmada ou ainda em análise.

## Prioridade das perguntas

- `BLOCKING`: sem resposta, não há base responsável para registrar nem um draft coerente.
- `IMPORTANT`: melhora a análise, mas pode permanecer aberta em ADR `Proposed`.
- `OPTIONAL`: pode ser resolvida depois e não deve atrasar o draft.

Faça 1 a 4 perguntas por rodada, começando pelas `BLOCKING` que eliminam alternativas ou alteram a decisão. Use as respostas para determinar a rodada seguinte; não apresente questionário extenso. Para síncrono versus assíncrono, investigue conforme necessário acoplamento de disponibilidade, replay, consistência, ordering, durability e infraestrutura padronizada.

## Readiness

- `DECISION_DISCOVERY_REQUIRED`: faltam informações que podem alterar a escolha. Pergunte; não produza ADR nem recomende se faltarem drivers essenciais.
- `DECISION_READY_FOR_EVALUATION`: há base para comparar alternativas, recomendar quando possível e pedir uma decisão explícita ao usuário.
- `DECISION_CONFIRMED`: a alternativa foi explicitamente escolhida ou está formalmente confirmada por fonte confiável. Pode ser registrada como `Accepted` quando aplicável.

Um pedido explícito de draft permite criar `Proposed`, mas não muda a readiness nem autoriza preencher lacunas. Se a escolha depender de requirement ausente, registre `Decision blocked by missing requirement`, explique o impacto e recomende `$spec-author`.

## Evidências e conflitos

Uma constraint exige fonte. Não presuma Kubernetes, Kafka corporativo ou qualquer arquitetura atual. Se specification, arquitetura, ADR, código e configuração divergirem, registre o conflito e pergunte quando ele afetar a decisão; não escolha silenciosamente uma fonte.

Registre números desconhecidos como `OPEN-DECISION-QUESTION-*`. Nunca invente RPS, latência, throughput, partições, réplicas, timeout, retries, TTL, retention, custo ou volume.

## Checkpoint

Use quando reduzir risco antes de um ADR `Accepted`:

```text
Entendimento atual da decisão

Problema: ...
Drivers:
- ...
Constraints:
- ...
Alternativas consideradas:
- ...
Recomendação: ...
Trade-offs:
- ...
Decisão confirmada: ...
Fonte da confirmação: ...
```
