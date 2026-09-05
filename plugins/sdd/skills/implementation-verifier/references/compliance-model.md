# Modelo de Compliance

## Por requirement

- `PASS`: implementação e validação possuem evidência suficiente.
- `PARTIAL`: apenas parte do requirement foi implementada ou comprovada.
- `FAIL`: implementação contradiz claramente o requirement.
- `NOT_VERIFIED`: evidência disponível é insuficiente.
- `BLOCKED`: ambiguidade ou conflito impede avaliação.

Requirements críticos sem evidência não recebem `PASS`. Uma matriz concisa pode relacionar requirement, implementação, testes e status; não crie tabela enorme sem necessidade.

## Findings

Use categorias estáveis conforme aplicáveis: `REQUIREMENT_MISMATCH`, `ACCEPTANCE_CRITERIA_GAP`, `ARCHITECTURE_MISMATCH`, `ADR_VIOLATION`, `PLAN_DEVIATION`, `TEST_COVERAGE_GAP`, `UNVERIFIED_NFR`, `COMPATIBILITY_REGRESSION`, `MIGRATION_GAP`, `SECURITY_GAP`, `RELIABILITY_GAP`, `OBSERVABILITY_GAP`, `SCOPE_DEVIATION`, `TEST_WEAKENING`, `CONTEXT_CONFLICT`, `OPEN_QUESTION`, `PREEXISTING_FAILURE` e `REGRESSION`.

Severidades: `BLOCKER`, `HIGH`, `MEDIUM`, `LOW`. Cada `IV-*` registra categoria, requirement, finding, evidência, impacto, ação recomendada e status.

## Verdicts

- `NOT_VERIFIABLE`: contexto insuficiente ou conflitante.
- `NON_COMPLIANT`: violações materiais.
- `PARTIALLY_COMPLIANT`: parte significativa atende, mas existem gaps.
- `COMPLIANT_WITH_RISKS`: requisitos principais atendidos com riscos ou verificações não conclusivas explícitas.
- `COMPLIANT`: evidência suficiente de aderência ao escopo verificado.

`COMPLIANT` exige ausência de blockers, conflitos materiais e HIGHs abertos que invalidem requirements críticos; comportamentos e acceptance criteria críticos comprovados; assumptions críticas confirmadas; NFRs relevantes verificados ou explicitamente fora do escopo.
