# Processo de Implementação

## Ciclo por task

```text
TASK
  ↓
inspect affected code
  ↓
validate assumptions
  ↓
implement smallest coherent delta
  ↓
run relevant tests
  ↓
validate completion criteria and traceability
  ↓
next TASK
```

Antes de editar, confirme objetivo, FR/NFR/COMPAT/MIG e acceptance criteria relacionados, arquitetura, `API.md` quando a task envolver interface, ADRs, findings relevantes de `SECURITY-REVIEW.md` e `RELIABILITY-REVIEW.md`, plano, TEST-PLAN, contrato existente, código atual, dependências, áreas, validation e completion criteria. Considere somente findings relacionados ao componente, operação, requirement, dependency, contrato ou fluxo da task. Siga dependency order; se a realidade exigir ordem materialmente diferente, explique impacto e peça confirmação.

Para tasks de contrato, derive o delta somente de decisões confirmadas: operação, request, response, error, idempotência, paginação, versioning, compatibility ou event semantics. Não implemente operação extra por conveniência, broker não definido ou limite ausente. Valide que o TEST-PLAN cobre o comportamento descrito no `API.md`; gap como partial success sem teste deve ser registrado e encaminhado ao `$test-designer`, não corrigido silenciosamente.

Para mitigation especializada, confirme o comportamento normativo, o mecanismo aprovado e sua presença no plano. Um finding de ausência de tenant isolation pode ser corrigido diretamente quando requirement e abordagem já estiverem confirmados; recomendação de middleware sem decisão de mecanismo não pode. Timeout sugerido sem valor normativo permanece bloqueado ou aberto. Se a mitigation aprovada não estiver no plano e sua inclusão for material, registre `PLAN_DEVIATION`.

## Validação contínua

Use somente comandos declarados em `AGENTS.md`, manifests, scripts ou CI. Execute testes focados após cada delta e suite/build/lint definidos ao final, conforme custo e risco. Se a baseline já falhar, reproduza quando necessário e diferencie falha preexistente de regressão.

Não altere teste válido para acomodar código incorreto. Se teste e comportamento requerido divergirem, aplique o gate de contexto.

## Task status e conclusão

Use `Pending`, `In Progress`, `Completed` e `Blocked` somente se o plano adotar status. Código escrito não basta para `Completed`: validações devem passar ou ter falha justificada, blockers precisam estar resolvidos e rastreabilidade preservada.

Atualize status no plano apenas quando a convenção permitir. Mudança material pertence ao `$implementation-planner` ou exige confirmação explícita.

## Completion check

Antes de `IMPLEMENTATION_READY_FOR_VERIFICATION`, confirme tasks do escopo, testes previstos, build/checks, migrations, aderência ao `API.md` e contrato formal aplicáveis, findings especializados relevantes, compatibilidade, blockers e desvios documentados. Reporte progresso, validações, blockers, desvios e próxima task quando um checkpoint ajudar; não peça aprovação após cada detalhe pequeno.
