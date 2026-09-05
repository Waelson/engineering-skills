# Cenários de Planejamento

Use estes cenários como testes normativos.

## 1. Change completa
SPEC, REVIEW, ARCHITECTURE e ADRs aplicáveis estão maduros.
- Esperado: criar `docs/changes/<change-id>/IMPLEMENTATION-PLAN.md`, com tarefas rastreáveis e ordem coerente.

## 2. ADR pendente
A arquitetura exige decisão, mas o ADR está `Proposed`.
- Readiness: `IMPLEMENTATION_DISCOVERY_REQUIRED`.
- Esperado: não assumir decisão; bloquear tarefas dependentes e recomendar `$adr-author`.

## 3. Brownfield
A feature altera comportamento existente.
- Esperado: incluir trabalho relevante de regressão e compatibilidade; não planejar como greenfield.

## 4. Greenfield
Baseline e arquitetura existem.
- Esperado: plano fundacional em `docs/plans/IMPLEMENTATION-PLAN.md`; não inventar stack ou infraestrutura adicional.

## 5. Migration
- Esperado: incluir fases aplicáveis de transição, validation, cutover e rollback sustentadas pelos artefatos; não exigir fluxo completo artificialmente.

## 6. Conflito entre artefatos
SPEC exige fail-closed e ADR define fail-open.
- Esperado: registrar `IMPLEMENTATION_CONTEXT_CONFLICT`, bloquear parte afetada e não escolher uma fonte.

## 7. Draft solicitado
Entrada: “Faça um plano preliminar com o que temos.”
- Esperado: `Status: Draft`, assumptions, open questions e blockers explícitos; nunca `Ready` com blocker material.

## 8. Arquitetura incompleta
Data ownership não está definido e altera decomposição.
- Esperado: perguntar ou recomendar `$architecture-designer`; não inventar ownership.

## 9. Plano existente
Já existe `IMPLEMENTATION-PLAN.md`.
- Esperado: atualizar o mesmo arquivo e preservar `TASK-*` quando possível.

## 10. Tarefas paralelas
Duas tarefas não dependem entre si e compartilham precondição satisfeita.
- Esperado: indicar paralelização possível; não forçar sequência artificial.

## Asserções transversais

- a skill não implementa código nem produz suites detalhadas de testes;
- requirements, decisões arquiteturais, tecnologia, números e constraints não são inventados;
- ADR `Proposed` não é decisão confirmada;
- perguntas são progressivas e dependem do contexto já inspecionado;
- blockers materiais impedem `Status: Ready`;
- tarefas são rastreáveis a requirements, arquitetura, ADRs, risks ou acceptance criteria;
- planos de change ficam em `docs/changes/<change-id>/IMPLEMENTATION-PLAN.md`;
- conflitos entre artefatos não são resolvidos silenciosamente.
