# Brownfield e Migration

Em greenfield, priorize corretude e simplicidade sem exigir padrões ainda inexistentes ou introduzir abstrações preventivas sem impacto demonstrado.

Em brownfield, compare padrões locais, callers, callees, contratos e testes existentes. Procure regressão provável e breaking change não intencional, mas não gere finding apenas porque o código novo usa estilo diferente sem impacto. Evite recomendar rewrite amplo.

Para migrations, examine idempotência, resumability, partial failure, consistência, backward compatibility, cleanup e irreversibilidade conforme estratégia confirmada. Não invente que reexecução é possível; demonstre a condição quando alegar risco.

Generated code não é fonte primária de correção: encontre schema/template/generator e o processo de geração antes de recomendar alteração. Em scope deviation, reporte refactor ou dependency não relacionada somente quando ampliar risco, revisão ou manutenção materialmente.
