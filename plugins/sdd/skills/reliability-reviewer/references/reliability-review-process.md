# Processo de Reliability Review

## Contexto e readiness

Para change, consulte os artefatos aplicáveis sob `docs/changes/<change-id>/`, incluindo `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `API.md`, `IMPLEMENTATION-PLAN.md`, `TEST-PLAN.md`, `VERIFICATION.md` e `SECURITY-REVIEW.md`. Consulte baseline, ADRs e evidência técnica ou operacional relevante sem varrer o repositório inteiro.

- `RELIABILITY_DISCOVERY_REQUIRED`: faltam dados materiais sobre falha ou carga; pergunte e não conclua.
- `READY_FOR_RELIABILITY_REVIEW`: o contexto permite revisar o escopo.
- `RELIABILITY_REVIEW_COMPLETE`: os pontos avaliados possuem evidência suficiente e nenhum blocker impede conclusão.

Classifique questões como `BLOCKING`, `IMPORTANT` ou `OPTIONAL`. Uma pergunta blocking impede `Complete` somente quando afeta a conclusão do escopo.

## Evidência e saída

Relacione requirements `NFR-*`, `REL-*` ou equivalentes a código, configuração, métricas, testes, arquitetura, ADRs e evidência operacional. Se o requirement quantitativo faltar, registre `RELIABILITY_REQUIREMENT_GAP`; não invente target. Se fontes divergirem, registre `RELIABILITY_CONTEXT_CONFLICT` com fontes, impacto e validação necessária.

Quando solicitado, persista em `docs/changes/<change-id>/RELIABILITY-REVIEW.md`, atualizando o existente e preservando IDs. Use estrutura adaptativa com metadata, scope, inputs, context, critical flows, dependencies, failure model, requirements, assumptions, questions, findings, reviews temáticas, risks, status e next actions. Status: `Draft`, `Blocked` ou `Complete`.

Por padrão, entregue findings e validações necessárias sem remediação. Ausência de findings indica somente que nenhum foi identificado no escopo e evidência disponíveis.
