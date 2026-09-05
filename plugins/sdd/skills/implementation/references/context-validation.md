# Validação do Contexto

## Fontes

Para change, consulte quando aplicável `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `IMPLEMENTATION-PLAN.md` e `TEST-PLAN.md` sob `docs/changes/<change-id>/`, além de baseline, ADRs e `AGENTS.md`. Compare com código, testes, contracts, schemas, migrations, build, CI, configuração e dependencies reais.

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

Sources: PLAN, repository, SPEC, ARCHITECTURE, ADR ou TEST-PLAN
Conflict: <diferença verificável>
Impact: <task, comportamento ou risco afetado>
Action required: <confirmação ou artefato a reconciliar>
```

Não escolha silenciosamente uma fonte. ADR `Proposed`, assumption, open question ou proposed option nunca equivale a decisão confirmada.
