# Cenários de Design de Testes

Use estes cenários como testes normativos.

## 1. Change completa
SPEC, REVIEW, ARCHITECTURE e PLAN são consistentes.
- Esperado: criar `docs/changes/<change-id>/TEST-PLAN.md` com cobertura rastreável.

## 2. Requirement ambíguo
A spec exige que o sistema seja “resiliente”.
- Esperado: não inventar critério; registrar `TEST_COVERAGE_GAP` e pedir clarificação.

## 3. Conflito entre spec e ADR
- Esperado: registrar `TEST_CONTEXT_CONFLICT`, bloquear o fluxo afetado e não escolher uma fonte.

## 4. Brownfield
O código possui comportamento não documentado.
- Esperado: registrar `OBSERVED BEHAVIOR` separado de `EXPECTED BEHAVIOR`.

## 5. Characterization test
Há refactor em legado sem baseline completa.
- Esperado: sugerir characterization test; não transformar comportamento observado em requirement confirmado.

## 6. Migration
- Esperado: testar source, transition e target e incluir reconciliation/cutover somente quando aplicáveis.

## 7. Métrica ausente
NFR de performance não define valor.
- Esperado: criar `TEST-QUESTION-*`; não inventar throughput ou latência.

## 8. Draft solicitado
- Esperado: `Status: Draft`, com assumptions, gaps e blockers explícitos.

## 9. Acceptance criterion sem teste
- Esperado: registrar coverage gap e não declarar cobertura completa.

## 10. Plano existente
Já existe `TEST-PLAN.md`.
- Esperado: atualizar o mesmo arquivo e preservar IDs quando possível.

## Asserções transversais

- nenhum artefato é aceito como verdade absoluta sem validação de consistência;
- comportamento esperado, métricas, limites, timeout e guarantees não são inventados;
- observed behavior não se torna expected behavior automaticamente;
- perguntas ocorrem em rodadas de 1 a 4 e priorizam gaps que alteram resultados;
- conflitos nunca são resolvidos silenciosamente;
- blocker material impede `Status: Ready`;
- requirements e acceptance criteria permanecem rastreáveis aos testes;
- a skill não implementa código de aplicação.
