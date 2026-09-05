# Rastreabilidade de Testes

## Cadeia

Preserve:

```text
Requirement → Acceptance Criterion → Test Case → Evidence
Architecture / ADR / Risk → Test Case
TASK → Required Validation
```

Use IDs simples e estáveis, como `TC-001`, ou prefixos quando agregarem clareza: `FUNC-*`, `COMPAT-TC-*`, `MIG-TC-*`, `PERF-*`, `SEC-*` e `REL-*`. Não crie taxonomia complexa para planos pequenos.

## Mapeamento

```text
FR-004 → TC-004-01, TC-004-02
AC-003-01 → TC-003-01
NFR-003 → PERF-003-01
COMPAT-002 → COMPAT-TC-002-01
MIG-004 → MIG-TC-004-01

TASK-004
Required Validation:
- TC-004-01
- TC-004-02
```

Não invente IDs. Cite path e seção quando a fonte não tiver identificador. Preserve IDs ao atualizar um plano.

## Coverage validation

Ao final, identifique requirements e acceptance criteria sem teste, testes sem origem e tarefas sem validation. Quando não houver forma objetiva de testar um requirement, registre:

```text
TEST_COVERAGE_GAP

Source: NFR-007
Problem: “O sistema deve ser resiliente” não define resultado verificável.
Status: bloqueado até refinamento do requirement.
```

Cada acceptance criterion relevante deve possuir pelo menos uma estratégia de verificação. Evite duplicar o implementation plan; relacione apenas tasks e validações.
