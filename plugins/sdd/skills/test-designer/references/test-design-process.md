# Processo de Design de Testes

## Fontes e discovery

Para change, consulte quando aplicável:

```text
docs/changes/<change-id>/SPEC.md
docs/changes/<change-id>/REVIEW.md
docs/changes/<change-id>/ARCHITECTURE.md
docs/changes/<change-id>/IMPLEMENTATION-PLAN.md
docs/architecture/adr/
```

Consulte baseline, arquitetura vigente, testes, contratos, schemas, código, fixtures, CI e ferramentas somente quando necessário. Nenhuma fonte possui autoridade absoluta: compare afirmações relevantes e sua evidência.

Antes de derivar teste de um requirement, verifique se ele é claro e testável, possui acceptance criterion quando necessário, não contradiz outro requisito e não foi reinterpretado indevidamente por arquitetura, ADR ou plano. Compare também com comportamento legado que deva ser preservado.

## Readiness

- `TEST_DISCOVERY_REQUIRED`: ambiguidade ou conflito impede saber qual resultado validar. Faça perguntas e não produza plano final.
- `READY_FOR_TEST_DRAFT`: há base para estratégia preliminar, com assumptions, gaps e blockers explícitos. Use `Draft` ou `Blocked`.
- `TEST_PLAN_READY`: comportamento esperado e evidências necessárias estão suficientemente definidos. Use `Ready` somente sem blocker material.

Classifique perguntas como `BLOCKING`, `IMPORTANT` ou `OPTIONAL`. Faça 1 a 4 por rodada e priorize partial failure, ordering, retry observável, duplicação, autorização, fail-open/closed ou outro ponto que altere o resultado esperado.

## Hard gate

Não use `Ready` quando fluxo crítico depender de assumption, acceptance criterion contraditório, requirement não testável ou conflito entre SPEC, REVIEW, ARCHITECTURE, ADR, PLAN, testes existentes e código. Um pedido de draft permite avançar sem inventar resposta.

## Conflitos

Registre:

```text
TEST_CONTEXT_CONFLICT

Sources:
- SPEC: <afirmação>
- ADR-004: <afirmação incompatível>

Impact:
Não é possível definir o resultado correto do teste de <fluxo>.

Action:
Reconciliar as fontes antes de marcar o TEST-PLAN como Ready.
```

Não confie em `REVIEW.md` que declare resolução quando a fonte revisada continuar inconsistente.

## Status e estrutura adaptativa

Use `Draft`, `Blocked` ou `Ready`. Para change, registre specification, architecture e implementation plan relacionados.

```markdown
# Test Plan: <título>

## Metadata
## Scope
## Inputs
## Test Readiness
## Confirmed Expected Behavior
## Assumptions
## Open Questions
## Context Conflicts
## Test Strategy
## Test Levels
## Functional Coverage
## Acceptance Criteria Coverage
## Compatibility Coverage
## Migration Coverage
## Reliability Coverage
## Security Coverage
## Performance Coverage
## Test Data
## Environment Requirements
## Traceability
## Risks
## Exit Criteria
```

Omita seções irrelevantes. O TEST-PLAN referencia e complementa os demais artefatos; não os substitui.
