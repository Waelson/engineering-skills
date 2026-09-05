# Processo de Verificação

## Discovery e consistência

Para change, consulte `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `IMPLEMENTATION-PLAN.md` e `TEST-PLAN.md` sob `docs/changes/<change-id>/`, além de baseline, ADRs e `AGENTS.md` quando relevantes. Verifique código, diff, testes, build, lint, análise estática, migrations, contratos, schemas, configuração, flags, observabilidade, CI e generated code proporcionais ao escopo.

Nenhuma fonte é correta por definição. Um ADR mais recente só prevalece quando supersede ou convenção explícita comprovar a relação. Uma review marcada como resolvida não elimina inconsistência ainda presente.

## Readiness

- `VERIFICATION_CONTEXT_UNRESOLVED`: comportamento esperado, validade de decisão ou fonte está ambígua/conflitante. Pergunte e não emita verdict final.
- `READY_FOR_VERIFICATION`: há contexto suficiente para avaliar compliance.
- `VERIFICATION_COMPLETE`: análise concluída com evidência suficiente para o verdict aplicável.

Classifique perguntas como `BLOCKING`, `IMPORTANT` ou `OPTIONAL`; faça 1 a 4 por rodada somente se alterarem o verdict.

## Conflitos e questões

```text
VERIFICATION_CONTEXT_CONFLICT
Sources: <afirmações incompatíveis>
Impact: <requirements ou checks bloqueados>
Action required: <confirmação/reconciliação>
```

```text
VERIFICATION_OPEN_QUESTION
Question: <comportamento não definido>
Impact: não é possível verificar <requirement>.
```

Não preencha lacunas. Registre `SCOPE_DEVIATION` para upgrade, refactor, dependency ou contrato fora do escopo.

## Artefato

Use estrutura adaptativa:

```markdown
# Implementation Verification: <título>
## Metadata
## Verification Scope
## Inputs
## Verification Status
## Context Conflicts
## Requirement Compliance
## Acceptance Criteria Compliance
## Architecture Compliance
## ADR Compliance
## Implementation Plan Compliance
## Test Evidence
## NFR Verification
## Compatibility Verification
## Migration Verification
## Findings
## Open Questions
## Risks
## Verdict
## Recommended Next Actions
```

Para change, o path padrão é `docs/changes/<change-id>/VERIFICATION.md`. Atualize o existente e preserve `IV-*`.
