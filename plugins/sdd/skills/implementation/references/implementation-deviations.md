# Desvios de Implementação

- `LOCAL_IMPLEMENTATION_DETAIL`: decisão reversível e de baixo nível, alinhada às convenções, sem alterar requirement, arquitetura, contrato ou dependency material. Pode avançar.
- `PLAN_DEVIATION`: diferença que pode alterar sequência, risco, escopo ou validação. Avalie impacto e confirme quando material.
- `ARCHITECTURAL_DEVIATION`: altera boundary, storage, protocolo, consistency, topology ou decisão. Bloqueie e retorne a `$architecture-designer` ou `$adr-author`.
- `REQUIREMENT_DEVIATION`: altera comportamento esperado ou acceptance criterion. Bloqueie e retorne a `$spec-author` ou `$spec-reviewer`.

Não use “detalhe local” para justificar tecnologia, dependency, feature flag, retry policy ou contrato novo. Registre desvios relevantes e `Affected Tasks`.

Oportunidades não necessárias ao escopo devem ser deixadas intactas e, se úteis, registradas como `OUT_OF_SCOPE_OBSERVATION`.
