# Cenários de Revisão SDD

Use estes cenários como testes normativos de decisão.

## 1. Greenfield válido

Alvo: `docs/spec/SPEC.md` de uma aplicação nova com requisitos completos.

- Tipo: `BASELINE`
- Contexto: `GREENFIELD`
- Esperado: revisar requisitos e readiness sem exigir estado atual, compatibilidade, migração ou riscos de regressão artificiais.

## 2. Evolution com baseline

Existem `docs/spec/SPEC.md` e `docs/changes/batch-authorization/SPEC.md`.

- Tipo: `CHANGE`
- Contexto: `EVOLUTION`
- Baseline: `ESTABLISHED` ou `PARTIAL`, conforme cobertura
- Esperado: comparar fontes, validar estado atual, delta, comportamento a preservar, compatibilidade, regressões e contradições.

## 3. Evolution sem baseline

Existe `docs/changes/batch-authorization/SPEC.md`, mas não `docs/spec/SPEC.md`.

- Baseline: `ABSENT`
- Esperado: não reprovar somente pela ausência da baseline; revisar reconstrução do estado atual, evidências, premissas e questões abertas.

## 4. Baseline parcial

A baseline não cobre completamente o domínio alterado.

- Baseline: `PARTIAL`
- Esperado: usar evidências complementares, tornar inferências visíveis e não exigir reconstrução global.

## 5. Migration incompleta

`docs/changes/migrate-policy-storage/SPEC.md` define estados atual e alvo, mas omite rollback apesar de risco real de cutover.

- Contexto: `MIGRATION`
- Esperado: finding `MISSING_MIGRATION_REQUIREMENT` ou `MISSING_FAILURE_MODE`, com severidade proporcional ao risco.

## 6. Baseline atualizada prematuramente

A baseline descreve uma feature como vigente enquanto a change spec permanece `Draft`.

- Esperado: `PREMATURE_BASELINE_UPDATE`.

## 7. Contradição entre evidências

A spec declara fail-closed, mas testes relevantes demonstram fail-open.

- Esperado: `EVIDENCE_CONFLICT`; não escolher silenciosamente qual fonte está correta.

## 8. Placement incorreto

Uma change spec substituiu a baseline em `docs/spec/SPEC.md`.

- Esperado: `INCORRECT_ARTIFACT_PLACEMENT`; não mover o arquivo sem solicitação.

## Asserções transversais

- `docs/spec/SPEC.md` representa a baseline vigente.
- `docs/changes/<change-id>/SPEC.md` representa uma mudança proposta ou em andamento.
- Uma review persistida de change spec fica em `docs/changes/<change-id>/REVIEW.md`.
- Ausência ou parcialidade da baseline exige avaliação das evidências, não reprovação automática.
- Change specs não atualizam silenciosamente a baseline.
- A skill não implementa código nem corrige specifications sem solicitação explícita.
- O veredito depende do contexto `GREENFIELD`, `EVOLUTION` ou `MIGRATION`.
