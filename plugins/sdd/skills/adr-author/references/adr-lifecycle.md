# Lifecycle do ADR

## Fluxo normal

```text
Discovery
   ↓
Decision Framing
   ↓
Evaluation
   ↓
Recommendation
   ↓
Explicit Confirmation
   ↓
Accepted
```

`Proposed` é um estado documental opcional, criado somente quando o usuário pede explicitamente um draft antes da confirmação:

```text
Evaluation → Proposed → Explicit Confirmation → Accepted
```

Não é obrigatório criar `Proposed` antes de `Accepted`. É obrigatório obter confirmação antes de `Accepted`.

## Política de criação

- `DECISION_DISCOVERY_REQUIRED`: não criar arquivo, mesmo que uma tecnologia tenha sido sugerida. Exceção: pedido explícito de draft permite somente `Proposed`, desde que haja contexto mínimo coerente.
- `DECISION_READY_FOR_EVALUATION`: comparar e recomendar na conversa; pedir confirmação. Não criar arquivo por padrão.
- `DECISION_CONFIRMED`: criar ou atualizar o ADR e usar `Accepted` quando apropriado, registrando `Decision Source`.

Um ADR `Proposed` deve registrar que a decisão não está confirmada, opções, recomendação atual, open questions e condições necessárias para aceitação.

## Evolução histórica

```text
Accepted
   ↓
Superseded
```

Não reescreva substancialmente um ADR aceito para representar decisão posterior. Crie novo ADR, use `Supersedes` e preserve a fonte e o racional históricos.
