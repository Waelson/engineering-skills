# Design do Contrato

## Semântica antes da forma

Para cada operação, descreva finalidade, precondições, entrada, efeito, resultado, side effects, falhas, idempotência e consistência aplicáveis. Derive dados, filtros e operações dos casos de uso confirmados. Naming deve seguir o projeto sem consumir discovery quando não for material.

Ao comparar estilos de interface, apresente decisão, alternativas, drivers, trade-offs, recomendação e status. Recomendação permanece proposta até confirmação.

## Artefato

Para change, crie ou atualize `docs/changes/<change-id>/API.md`. Não crie `API-v2.md` sem necessidade. Só altere OpenAPI, protobuf, AsyncAPI ou outro source of truth formal quando isso fizer parte explicitamente do escopo. Não crie baseline global apenas porque uma change possui API.

Use estrutura adaptativa:

```markdown
# API Design: <título>
## Metadata
## Context
## Consumers
## Use Cases
## Existing Contract
## Proposed Contract
## Operations
## Data Model
## Error Semantics
## Idempotency
## Pagination / Filtering
## Consistency
## Security
## Compatibility
## Versioning
## Deprecation
## Observability
## Contract Decisions
## Assumptions
## Open Questions
## Traceability
```

Omita seções artificiais. Metadata pode registrar `API Design Type: CHANGE`, contexto de desenvolvimento, SPEC e arquitetura relacionadas e `Status: Draft`, `Ready` ou `Blocked`. Relacione decisões e operações a IDs como `FR-*` e `COMPAT-*`.

## Validação

Confirme que consumidores conseguem interpretar sucesso, erro e retry; implementadores conseguem executar sem inventar semântica; mudanças preservam constraints; e contract tests podem ser derivados. Não marque `Ready` com blocker aberto.
