# Verificação em Brownfield

Priorize regressões, `COMPAT-*`, contratos, consumers, schemas, events e comportamento confirmado a preservar. Separe `OBSERVED IMPLEMENTATION BEHAVIOR` de `CONFIRMED EXPECTED BEHAVIOR`.

Characterization tests comprovam comportamento observado, não intenção. Se o legado contradisser SPEC ou decisão vigente, registre conflito; não o congele automaticamente.

Examine testes alterados no diff. Relaxamento de assertion, remoção de cenário ou mock ampliado pode gerar `TEST_WEAKENING`. Uma falha existente antes do patch é `PREEXISTING_FAILURE`, salvo evidência de agravamento pela mudança.
