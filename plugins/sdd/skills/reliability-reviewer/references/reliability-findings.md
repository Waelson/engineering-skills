# Findings de Reliability

Use `REL-FINDING-001`, preservando IDs ao atualizar. Cada finding inclui severidade, categoria, localização, finding, evidência, risco/impacto, status e validação ou ação necessária.

Categorias preferenciais: `TIMEOUT_GAP`, `RETRY_RISK`, `RETRY_AMPLIFICATION`, `IDEMPOTENCY_GAP`, `BACKPRESSURE_GAP`, `LOAD_SHEDDING_GAP`, `UNBOUNDED_QUEUE`, `SATURATION_RISK`, `AUTOSCALING_GAP`, `CAPACITY_GAP`, `FAILURE_MODE_GAP`, `RECOVERY_GAP`, `CONSISTENCY_RISK`, `CASCADING_FAILURE_RISK`, `GRACEFUL_DEGRADATION_GAP`, `DEPENDENCY_ISOLATION_GAP`, `RELIABILITY_REQUIREMENT_GAP`, `RELIABILITY_CONTEXT_CONFLICT` e `OPEN_RELIABILITY_QUESTION`.

Severidades:

- `BLOCKER`: failure behavior crítico indefinido ou risco que impede rollout seguro.
- `HIGH`: risco relevante de cascading failure, overload collapse, data loss ou indisponibilidade significativa.
- `MEDIUM`: gap importante de proteção, observability, recovery ou capacity.
- `LOW`: melhoria defensiva ou de precisão.

Não infle severidade. Finding conclusivo exige requirement, arquivo, configuração, métrica, teste, arquitetura, ADR ou evidência operacional. Quando existe apenas hipótese plausível, registre assumption ou open question.

Validações podem incluir dependency timeout/unavailable, queue saturation, consumer lag, partial failure, retry storm e restart recovery sem exigir chaos engineering formal por padrão.
