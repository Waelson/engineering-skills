# Qualidade de Findings

Um finding deve explicar problema, localização, cenário ativador, impacto e relevância. Use `CR-FINDING-001` com severidade, categoria, localização, evidência, cenário, impacto e status. Evidência deve permitir que o autor reproduza ou raciocine sobre o problema.

Categorias preferenciais: `CORRECTNESS`, `ERROR_HANDLING`, `RESOURCE_LEAK`, `CONCURRENCY`, `DATA_INTEGRITY`, `CONTRACT_MISMATCH`, `COMPATIBILITY`, `SECURITY_RISK`, `RELIABILITY_RISK`, `PERFORMANCE_RISK`, `MAINTAINABILITY`, `TEST_GAP`, `TEST_WEAKENING`, `SCOPE_DEVIATION`, `DEAD_CODE` e `CONTEXT_CONFLICT`.

Severidades:

- `BLOCKER`: bug ou risco que impede merge/rollout seguro.
- `HIGH`: defeito provável com impacto funcional, de dados, segurança ou disponibilidade.
- `MEDIUM`: problema relevante, não necessariamente bloqueante.
- `LOW`: melhoria pequena com impacto real; nunca use para nitpick.

Diferencie bug demonstrável, risco plausível sustentado, maintainability issue com custo concreto, nitpick sem impacto e context conflict. Não diga “pode quebrar em edge case” sem mostrar qual entrada, estado ou sequência ativa o problema. Ordene findings por severidade; se não houver findings, informe limitações e confiança sem alegar correção absoluta.
