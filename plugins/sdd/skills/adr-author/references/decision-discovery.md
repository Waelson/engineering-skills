# Decision Discovery

## Princípio

Descubra por que uma decisão é necessária antes de comparar tecnologias ou escrever o ADR. Não transforme `UNKNOWN` em fato assumido nem opção ou recomendação em decisão.

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

Faça normalmente 2 a 5 perguntas por rodada, começando pelas que eliminam alternativas ou alteram a decisão. Para síncrono versus assíncrono, investigue conforme necessário acoplamento de disponibilidade, replay, consistência, ordering, durability e infraestrutura padronizada.

## Readiness

- `DECISION_DISCOVERY_REQUIRED`: faltam contexto, driver, constraint ou resposta crítica. Não produza ADR final.
- `READY_FOR_ADR_DRAFT`: há base para documentar um ADR `Proposed`, com assumptions e questões abertas explícitas.
- `DECISION_CONFIRMED`: a escolha foi confirmada por fonte aceitável e pode ser registrada como `Accepted` quando aplicável.

Um pedido de draft permite `READY_FOR_ADR_DRAFT`, mas não autoriza preencher lacunas. Se a escolha depender de requirement ausente, registre `Decision blocked by missing requirement`, explique o impacto e recomende `$spec-author`.

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
