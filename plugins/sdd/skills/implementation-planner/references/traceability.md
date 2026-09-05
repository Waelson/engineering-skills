# Rastreabilidade do Plano

## Cadeia de evidência

Preserve a cadeia:

```text
Requirement → Architecture → ADR → TASK → Validation
```

Nem toda tarefa precisa referenciar todos os níveis, mas cada tarefa material deve derivar de pelo menos um requirement, acceptance criterion, architecture decision, ADR, risk ou obrigação de migration/compatibility.

## Mapeamento por tarefa

```text
TASK-007
Related:
- FR-006
- COMPAT-002
- ADR-004
```

Não invente IDs. Quando o documento fonte não usar identificadores, cite seção e path de forma estável.

## Cobertura final

Inclua uma visão concisa suficiente para detectar lacunas:

```text
FR-001 → TASK-001, TASK-004
FR-002 → TASK-003
NFR-004 → TASK-007
COMPAT-002 → TASK-005
MIG-001 → TASK-006, TASK-008
```

Não crie matriz grande quando poucas relações bastarem. Verifique também requirements sem tarefa, tarefas sem origem, decisões confirmadas sem reflexo e validation sem responsável ou ponto de execução.

## Atualizações

Quando SPEC, ARCHITECTURE ou ADR mudar, identifique `Affected Tasks`, atualize somente as relações e tarefas afetadas e preserve IDs sempre que possível. Não crie `IMPLEMENTATION-PLAN-v2.md` para evitar reconciliar mudanças.

Essa rastreabilidade deve permitir ao `$test-designer` derivar cobertura e ao verificador futuro comparar SPEC, ARCHITECTURE, ADRs, PLAN e CODE.
