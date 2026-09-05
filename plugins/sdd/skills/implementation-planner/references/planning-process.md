# Processo de Planejamento

## Entradas e discovery

Para change, consulte quando aplicável:

```text
docs/changes/<change-id>/SPEC.md
docs/changes/<change-id>/REVIEW.md
docs/changes/<change-id>/ARCHITECTURE.md
docs/architecture/adr/
```

Para baseline greenfield:

```text
docs/spec/SPEC.md
docs/architecture/ARCHITECTURE.md
docs/architecture/adr/
```

Complete o entendimento com `AGENTS.md`, estrutura de módulos, testes, CI, scripts, contratos, schemas e migrations somente quando relevante. Código evidencia o estado atual, mas não substitui intenção documentada.

## Readiness

- `IMPLEMENTATION_DISCOVERY_REQUIRED`: falta requirement, arquitetura, decisão, ownership, estado atual, compatibilidade ou sequencing capaz de mudar materialmente decomposição ou ordem. Pergunte e não gere plano final.
- `READY_FOR_IMPLEMENTATION_DRAFT`: há base para plano preliminar, mas existem assumptions, dependências ou blockers explicitamente registrados. Use `Status: Draft` ou `Blocked`, conforme impacto.
- `IMPLEMENTATION_PLAN_READY`: decomposição, decisões, dependências e validação estão suficientemente definidas e não há blocker material. Use `Status: Ready`.

Perguntas são `BLOCKING`, `IMPORTANT` ou `OPTIONAL`. Faça 1 a 4 por rodada, priorizando as que alteram tarefas, ordem, compatibilidade, rollout, migration ou critérios de conclusão.

## Hard gate e routing

Não marque plano como pronto enquanto `OPEN-QUESTION-*`, `ARCH-QUESTION-*`, ADR `Proposed`, finding relevante ou conflito alterar materialmente a implementação. Não resolva essas lacunas durante planning:

- requirement ausente ou ambíguo → `$spec-author` ou `$spec-reviewer`;
- boundary, ownership ou arquitetura pendente → `$architecture-designer`;
- escolha arquitetural relevante não confirmada → `$adr-author`.

Se o usuário pedir uma primeira versão, produza `Draft` com blockers e tarefas dependentes claramente bloqueadas. Não esconda lacunas dentro das tarefas.

## Status do plano

- `Draft`: preliminar; assumptions e open questions são permitidas e visíveis.
- `Blocked`: não é executável na parte afetada até blockers indicados serem resolvidos.
- `Ready`: executável, sem decisões ou requisitos materiais pendentes.

## Conflitos

Quando fontes relevantes divergirem, registre:

```text
IMPLEMENTATION_CONTEXT_CONFLICT

Sources: SPEC, ARCHITECTURE, ADR-004
Conflict: <afirmações incompatíveis>
Affected Tasks: <TASK IDs ou área ainda não decomponível>
Resolution Required: <documento ou decisão a reconciliar>
```

Não escolha silenciosamente uma fonte. Quando ADR ou arquitetura mudar, identifique tarefas afetadas e preserve o histórico lógico do plano.

## Estrutura adaptativa

```markdown
# Implementation Plan: <título>

## Metadata
## Scope
## Inputs
## Planning Status
## Preconditions
## Confirmed Decisions
## Assumptions
## Open Questions
## Implementation Strategy
## Phases
### Phase 1
#### TASK-001
## Requirement Traceability
## Validation Strategy
## Migration / Rollout
## Risks
## Completion Criteria
```

Omita seções irrelevantes. Para change, registre `Plan Type: CHANGE`, contexto, specification e architecture relacionadas. O plano complementa e referencia os artefatos; não os substitui.
