# Facilitação de Decisões Arquiteturais

## Separação obrigatória

Uma recomendação não é decisão. Uma opção não é constraint. Uma assumption não é fato. Preserve status e confirmação explicitamente.

## Formato de facilitação

```markdown
### Decisão necessária: <tema>

Requisitos e fontes:
- NFR-003
- ADR-002

#### Opção A — <nome>

Vantagens:
- ...

Desvantagens e riscos:
- ...

#### Opção B — <nome>

Vantagens:
- ...

Desvantagens e riscos:
- ...

Recomendação: <opção e justificativa>
Status: Proposed
Confirmação necessária: Sim
ADR candidato: Sim | Não
```

Quando a escolha depender do usuário, mantenha `Status: Proposed` até confirmação. Use `Status: Accepted` somente para `CONFIRMED ARCHITECTURAL DECISION` com fonte registrada.

## Assumptions como dívida de decisão

```text
ARCH-ASSUMPTION-001

Assumption: ordering é necessário apenas por tenant.
Motivo: o requisito não define o escopo de ordering e o draft precisa avaliar particionamento.
Impacto: se ordering global for necessário, a estratégia proposta deve ser reconsiderada.
```

Cada assumption deve informar hipótese, motivo e decisão afetada.

## Questões orientadas à decisão

Use `ARCH-QUESTION-*` para perguntas específicas, como “a indisponibilidade da auditoria pode bloquear o fluxo principal?”. Evite “qual arquitetura você quer?”.

## Conflitos

Quando fontes divergirem, registre:

```text
ARCHITECTURE_CONTEXT_CONFLICT

Fontes: SPEC, ADR-004, teste relevante
Conflito: <comportamentos incompatíveis>
Decisão afetada: <tema>
Confirmação necessária: <pergunta específica>
```

## ADRs

Marque decisões significativas como **Architecture Decision Required** e explique opções, trade-offs e recomendação. Não crie ADR automaticamente sem pedido explícito.
