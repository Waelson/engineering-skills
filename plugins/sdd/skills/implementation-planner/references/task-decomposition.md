# Decomposição de Tarefas

## Unidade de implementação

Crie unidades pequenas, coerentes e verificáveis no nível de componente, contrato, dado ou capacidade. Cada tarefa inclui somente campos aplicáveis:

```text
TASK-003 — <resultado específico>

Objetivo:
<mudança observável ou capacidade entregue>

Related:
- FR-004
- ADR-002

Dependências:
- TASK-001

Áreas impactadas:
- <path real ou área conceitual>

Trabalho esperado:
- ...

Validation required:
- ...

Riscos:
- ...

Condição de conclusão:
- ...
```

Use paths existentes em brownfield. Em greenfield sem layout definido, use áreas conceituais em vez de inventar diretórios ou arquivos.

## Granularidade e ordem

- preserve `TASK-*` existentes ao atualizar um plano;
- agrupe em phases somente quando isso esclarecer entregas ou dependências;
- ordene por dependências reais, não por template;
- considere contratos antes de consumidores, migrations antes de dependentes, compatibilidade antes de cutover e observabilidade antes de rollout somente quando o contexto exigir;
- prefira incrementos validáveis, pequenos commits e rollback possível;
- não exija feature flag, coexistência ou big bang sem decisão registrada.

## Paralelização

Indique tarefas paralelas somente quando nenhuma depender da outra e ambas tiverem precondições satisfeitas. Expresse, por exemplo: `TASK-004 e TASK-005 podem ocorrer em paralelo após TASK-002`. Não confunda independência técnica com prioridade de negócio.

## Greenfield e brownfield

Em greenfield, planeje fundações, domínio, interfaces, storage, observabilidade, segurança e deployment somente quando SPEC e arquitetura as definirem.

Em brownfield, inclua comportamento a preservar, regressão, compatibilidade, schema evolution, rollout, migration e cleanup somente quando aplicáveis. Não trate mudança em sistema existente como construção do zero.

## Completion criteria

Defina conclusão verificável: requisitos e acceptance criteria cobertos, migrations e rollout concluídos quando no escopo, regressões relevantes verificadas e sinais operacionais disponíveis quando exigidos. Não escreva a suite completa de testes.
