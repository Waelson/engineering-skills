# Findings de Segurança

Use `SEC-FINDING-001`, preservando IDs ao atualizar. Cada finding inclui severidade, categoria, localização, finding, evidência, risco, status e validação ou ação necessária. Relacione requisito existente quando possível; se ele não existir, use `SECURITY_REQUIREMENT_GAP` sem inventá-lo.

Categorias preferenciais: `AUTHENTICATION_GAP`, `AUTHORIZATION_GAP`, `PRIVILEGE_ESCALATION`, `TENANT_ISOLATION_GAP`, `DATA_EXPOSURE`, `SECRET_EXPOSURE`, `INPUT_VALIDATION_GAP`, `AUDITABILITY_GAP`, `TRUST_BOUNDARY_GAP`, `REPLAY_RISK`, `ABUSE_RISK`, `INSECURE_DEFAULT`, `DEPENDENCY_RISK`, `SECURITY_REQUIREMENT_GAP`, `SECURITY_CONTEXT_CONFLICT` e `OPEN_SECURITY_QUESTION`.

Severidades:

- `BLOCKER`: risco crítico ou impossibilidade de avaliar comportamento essencial.
- `HIGH`: possibilidade relevante de acesso indevido, privilege escalation, exposição sensível ou bypass.
- `MEDIUM`: gap importante de defesa, logging, validation ou hardening.
- `LOW`: melhoria defensiva ou impacto limitado.

Não infle severidade. Finding conclusivo exige evidência como requirement, arquivo e trecho/conceito, contrato, ADR, teste, configuração ou comportamento observado. Quando há apenas hipótese plausível, registre assumption ou open question.

Considere também brute force, resource exhaustion, duplication, race condition, confused deputy, dependencies vulneráveis, privilégio desnecessário e supply chain quando fizerem parte do escopo.
