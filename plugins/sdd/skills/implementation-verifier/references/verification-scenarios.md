# Cenários de Verificação

Use estes cenários como testes normativos.

## 1. Implementação correta
Artefatos, testes e código consistentes. Esperado: `COMPLIANT` com evidências explícitas.

## 2. Requirement parcial
Esperado: `PARTIAL` e finding rastreável.

## 3. Teste superficial
Teste passa com assertion insuficiente. Esperado: não declarar `PASS` automaticamente.

## 4. SPEC e ADR conflitam
Esperado: `VERIFICATION_CONTEXT_UNRESOLVED`, pergunta e nenhum `COMPLIANT`.

## 5. ADR Proposed usado
Esperado: indicar decisão não confirmada; não tratá-la como obrigatória.

## 6. Brownfield regression
Comportamento confirmado foi quebrado. Esperado: `COMPATIBILITY_REGRESSION`.

## 7. NFR sem benchmark
Há P95 definido sem medição. Esperado: `UNVERIFIED_NFR`, nunca `PASS`.

## 8. Teste enfraquecido
Esperado: `TEST_WEAKENING` com evidência do diff.

## 9. Scope creep
Dependency não relacionada foi alterada. Esperado: `SCOPE_DEVIATION`.

## 10. Migration incompleta
Estado final existe, mas rollback/cutover previsto não foi validado. Esperado: `MIGRATION_GAP`.

## 11. Confirmação necessária
Comportamento crítico está aberto. Esperado: perguntar; não assumir nem finalizar verdict.

## 12. Falha preexistente
Esperado: distinguir `PREEXISTING_FAILURE` de `REGRESSION`.

## Asserções transversais

- verification é independente da implementação;
- artefatos e testes não são verdades absolutas;
- comportamento, requirements, métricas e constraints não são inventados;
- conflitos e questões blocking impedem `COMPLIANT`;
- requirements críticos sem evidência não recebem `PASS`;
- findings citam evidência;
- verification não corrige silenciosamente.
