# Architecture Discovery

## Princípio

Não transforme unknown em fato assumido nem opção proposta em decisão. Antes de documentar, compreenda requisitos arquiteturalmente relevantes, constraints, arquitetura atual, dependências, decisões existentes, unknowns e trade-offs.

## Classificação das informações

- `CONFIRMED REQUIREMENT`: requirement confirmado na specification.
- `EXISTING CONSTRAINT`: restrição confirmada pelo sistema, plataforma, ADR, `AGENTS.md` ou usuário.
- `EXISTING DECISION`: decisão arquitetural vigente estabelecida por fonte confiável.
- `ARCHITECTURE ASSUMPTION`: hipótese necessária para um draft, ainda não confirmada.
- `OPEN ARCHITECTURAL QUESTION`: informação ausente capaz de alterar materialmente o design.
- `PROPOSED OPTION`: alternativa em análise, ainda não aprovada.
- `CONFIRMED ARCHITECTURAL DECISION`: decisão confirmada pelo usuário ou estabelecida por evidência confiável.

Registre a fonte das decisões importantes, por exemplo `NFR-004`, `ADR-002`, Platform Constraint ou User Confirmation.

## Perguntas e prioridade

- `BLOCKING`: sem resposta, alternativas válidas produzem designs materialmente diferentes, como consistência, fail-open/closed, multi-region, ordering, durability, source of truth ou perda de dados permitida.
- `IMPORTANT`: melhora o design, mas permite draft com assumption explícita, como crescimento, ownership operacional ou pico ainda desconhecido.
- `OPTIONAL`: pode ser decidido em ADR ou planejamento posterior e não bloqueia arquitetura responsável.

Faça normalmente 2 a 5 perguntas por interação. Não pergunte o que a spec, `REVIEW.md`, ADRs, código ou documentação já respondem. Não pergunte nomes de classes, packages, métodos, variáveis ou tasks.

## Readiness

- `ARCHITECTURE_DISCOVERY_REQUIRED`: faltam decisões ou informações críticas. Pergunte e consolide; não gere arquitetura definitiva.
- `READY_FOR_ARCHITECTURE_DRAFT`: permite proposta preliminar com assumptions e decisões pendentes claramente abertas.
- `ARCHITECTURE_READY`: decisões principais estão suficientemente compreendidas e confirmadas para uma arquitetura madura.

O pedido “faça uma proposta inicial com o que temos” permite avançar para draft quando houver base responsável. Não invente dados para completar o documento.

## Quando perguntar

Pergunte quando existirem múltiplas alternativas plausíveis e a escolha depender de prioridade de negócio ou constraint desconhecida. Para propagação de atualizações, investigue conforme necessário imediatismo, tolerância à consistência eventual, acoplamento de disponibilidade, replay, ordering, durability, infraestrutura existente e volume.

## Quando avançar sem perguntar

Avance quando houver requirement explícito, ADR válido, platform constraint, convenção obrigatória em `AGENTS.md`, apenas uma opção razoável dadas as constraints ou decisão reversível e de baixo impacto. Ainda assim, documente a origem.

## Contexto e evidências

Em brownfield, consulte contexto relevante antes de perguntar. Se spec, ADR e código divergirem, registre `ARCHITECTURE_CONTEXT_CONFLICT`; não escolha silenciosamente.

### Greenfield

Priorize boundaries, consumidores, escala, consistência, segurança, disponibilidade, falhas, deployment e operação. Greenfield não autoriza inventar uma baseline completa.

### Evolution

Preserve invariantes, compreenda o delta e pergunte somente sobre decisões novas. Não redesenhe componentes não relacionados.

### Migration

Esclareça motivação, source/target state, coexistência, consistência, cutover, rollback, tolerância a perda e compatibilidade quando relevantes. Não invente estratégia.

## Checkpoint de entendimento

Use quando reduzir risco antes da documentação:

```text
Entendimento arquitetural atual

Requisitos relevantes:
- ...
Constraints confirmadas:
- ...
Arquitetura atual:
- ...
Decisões estabelecidas:
- ...
Decisões em aberto:
- ...
Assumptions:
- ...
Alternativas relevantes:
- ...
```
