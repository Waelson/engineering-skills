# Testes em Brownfield

## Observed versus expected

Mantenha a separação explícita:

```text
OBSERVED BEHAVIOR:
O código retorna 200 com resultado parcial.

EXPECTED BEHAVIOR:
Não confirmado; a specification não define partial failure.
```

Código e testes existentes evidenciam comportamento atual. Eles não comprovam intenção de negócio nem obrigação de preservação. Se contradisserem SPEC ou ADR, registre `TEST_CONTEXT_CONFLICT`.

## Regression e characterization

Priorize integrações impactadas, contratos, compatibilidade e riscos de regressão. Use characterization test antes de refactor quando for útil compreender ou preservar comportamento legado, mas rotule-o como comportamento observado.

Não congele silenciosamente comportamento incorreto ou indefinido. Quando não houver baseline confiável, caracterização cria evidência para decisão posterior; não cria requirement.

## Test-first

Quando reduzir risco, indique regression characterization, contract ou outro teste que deve existir antes da mudança. Não implemente o teste nesta skill e não presuma que todo trabalho exige abordagem test-first.
