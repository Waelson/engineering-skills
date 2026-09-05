# Validação do Contexto

## Fontes

Para change, consulte quando aplicável `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `API.md`, `SECURITY-REVIEW.md`, `RELIABILITY-REVIEW.md`, `IMPLEMENTATION-PLAN.md` e `TEST-PLAN.md` sob `docs/changes/<change-id>/`, além de `docs/spec/SPEC.md`, `docs/architecture/ARCHITECTURE.md`, ADRs e `AGENTS.md`. Compare com código, testes, contracts, schemas, migrations, build, CI, configuração e dependencies reais.

`API.md` é obrigatório como contexto quando a mudança envolve REST, gRPC, GraphQL, eventos, AsyncAPI, WebSocket, streaming, request/response, schema de interface, versionamento, errors, idempotência, paginação, compatibilidade ou contratos entre producer e consumer. Se a mudança não envolver interface relevante, sua ausência não é erro. Se uma mudança explicitamente de API não possuir `API.md`, procure contrato confirmado em outra fonte; não invente o contrato e recomende `$api-designer` quando o contexto continuar insuficiente.

Valide a cadeia aplicável:

```text
SPEC ↕ ARCHITECTURE ↕ API.md ↕ ADRs ↕ SECURITY-REVIEW.md ↕ RELIABILITY-REVIEW.md ↕ IMPLEMENTATION-PLAN ↕ TEST-PLAN ↕ REPOSITÓRIO REAL
```

O `API.md` é fonte de contrato e intenção, não verdade absoluta. Confira operações, paths/methods ou services/RPCs, request/response, fields, required/optional, validation, defaults, result/partial success, errors/status/retryability, idempotência, paginação, versioning, compatibility e contratos de evento somente quando definidos e relevantes.

Quando houver OpenAPI, protobuf, AsyncAPI ou GraphQL schema, identifique a source of truth formal. Divergência entre ela e `API.md` é conflito até reconciliação; não escolha silenciosamente. Em brownfield, compare também contrato atual, consumidores, handlers e contract tests antes de concluir que o legado está errado.

Interprete a autoridade semanticamente: SPEC define comportamento necessário; arquitetura e ADRs confirmados definem decisões estruturais; `API.md` define contrato confirmado; reviews especializados identificam riscos, gaps, blockers e evidências; IMPLEMENTATION-PLAN decompõe execução; TEST-PLAN define validação planejada; repository mostra estrutura e comportamento observados. Reviews não substituem fontes normativas nem transformam recommendation em decisão.

Quando reviews existirem, identifique findings relacionados à task por componente, operação, requirement, dependency, contrato ou fluxo. Verifique `BLOCKER` e `HIGH` abertos, assumptions, open questions e evidência de findings `Resolved`. A ausência de review não bloqueia automaticamente; `Complete` não prova ausência de riscos.

Nenhuma fonte é infalível. Separe:

```text
OBSERVED CURRENT BEHAVIOR: o que código e testes demonstram hoje.
CONFIRMED REQUIRED BEHAVIOR: o que requirements e decisões reconciliados exigem.
```

Não perpetue comportamento legado conflitante nem assuma que o documento desatualizado prevalece.

## Readiness

- `IMPLEMENTATION_CONTEXT_UNRESOLVED`: conflito ou lacuna material impede execução segura da parte afetada.
- `READY_FOR_INCREMENTAL_IMPLEMENTATION`: uma unidade delimitada possui contexto suficiente.
- `IMPLEMENTATION_READY_FOR_VERIFICATION`: todas as tasks do escopo cumpriram critérios e validações previstas.

Faça 1 a 4 perguntas `BLOCKING` por rodada quando a ausência puder violar requirement, compatibilidade, arquitetura, dados, segurança ou rollback. Questions `IMPORTANT` podem permitir progresso independente; `OPTIONAL` não devem interromper.

## Conflito

```text
IMPLEMENTATION_CONTEXT_CONFLICT

Sources: API.md, SECURITY-REVIEW.md, RELIABILITY-REVIEW.md, contrato formal, contrato existente, PLAN, repository, SPEC, ARCHITECTURE, ADR ou TEST-PLAN
Conflict: <diferença verificável>
Impact: <task, comportamento ou risco afetado>
Action required: <confirmação ou artefato a reconciliar>
```

Não escolha silenciosamente uma fonte. ADR `Proposed`, assumption, open question ou proposed option nunca equivale a decisão confirmada.
