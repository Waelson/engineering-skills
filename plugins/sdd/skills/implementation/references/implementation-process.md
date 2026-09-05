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

Antes de editar, confirme objetivo, FR/NFR/COMPAT/MIG e acceptance criteria relacionados, decisões, dependências, áreas, validation e completion criteria. Siga dependency order; se a realidade exigir ordem materialmente diferente, explique impacto e peça confirmação.

## Validação contínua

Use somente comandos declarados em `AGENTS.md`, manifests, scripts ou CI. Execute testes focados após cada delta e suite/build/lint definidos ao final, conforme custo e risco. Se a baseline já falhar, reproduza quando necessário e diferencie falha preexistente de regressão.

Não altere teste válido para acomodar código incorreto. Se teste e comportamento requerido divergirem, aplique o gate de contexto.

## Task status e conclusão

Use `Pending`, `In Progress`, `Completed` e `Blocked` somente se o plano adotar status. Código escrito não basta para `Completed`: validações devem passar ou ter falha justificada, blockers precisam estar resolvidos e rastreabilidade preservada.

Atualize status no plano apenas quando a convenção permitir. Mudança material pertence ao `$implementation-planner` ou exige confirmação explícita.

## Completion check

Antes de `IMPLEMENTATION_READY_FOR_VERIFICATION`, confirme tasks do escopo, testes previstos, build/checks, migrations, contratos, compatibilidade, blockers e desvios documentados. Reporte progresso, validações, blockers, desvios e próxima task quando um checkpoint ajudar; não peça aprovação após cada detalhe pequeno.
