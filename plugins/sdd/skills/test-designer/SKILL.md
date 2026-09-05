---
name: test-designer
description: Projete estratégias e casos de teste rastreáveis a partir de requirements, acceptance criteria, arquitetura, ADRs e planos de implementação, validando consistência entre as fontes. Use para criar ou atualizar TEST-PLAN.md, derivar casos, planejar coverage, regression ou testes de migration. Não use para requirements discovery, spec review, arquitetura, ADR, implementation planning, implementação da aplicação ou code review.
---

# Designer de Testes

Defina evidências capazes de demonstrar o comportamento esperado sem presumir que qualquer artefato ou implementação está correto. Trabalhe em quatro fases: **Test Context Discovery → Test Readiness Validation → Test Strategy Design → Test Coverage Validation**.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e identifique se o alvo é change, baseline greenfield ou migration. Respeite convenções documentais e de testes estabelecidas.
2. Para change, leia `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md` e `IMPLEMENTATION-PLAN.md` em `docs/changes/<change-id>/` quando aplicáveis. Consulte ADRs relacionados e, quando necessário, baseline, arquitetura vigente, testes, contratos, schemas, código, fixtures, CI e ferramentas existentes.
3. Leia integralmente [references/test-design-process.md](references/test-design-process.md). Trate cada fonte como evidência falível: valide clareza, verificabilidade, acceptance criteria, consistência, comportamento legado e divergências entre documentação e implementação.
4. Diferencie rigorosamente `OBSERVED BEHAVIOR` de `EXPECTED BEHAVIOR`. Código e testes existentes demonstram o que ocorre hoje, não necessariamente o que deve continuar ocorrendo.
5. Classifique a readiness como `TEST_DISCOVERY_REQUIRED`, `READY_FOR_TEST_DRAFT` ou `TEST_PLAN_READY`. Quando uma ambiguidade material impedir definir o resultado correto, faça 1 a 4 perguntas de alto impacto por rodada ou recomende corrigir a fonte responsável.
6. **Hard gate:** não marque o plano como `Ready` quando o comportamento esperado de fluxo crítico depender de assumption não confirmada, requirement não testável ou fontes conflitantes. Se o usuário pedir draft, use `Status: Draft` ou `Blocked` e exponha blockers.
7. Quando houver base suficiente, leia [references/test-strategy.md](references/test-strategy.md) e [references/traceability.md](references/traceability.md). Escolha a camada de teste mais barata que valide corretamente o comportamento e crie IDs simples e estáveis.
8. Em brownfield, leia [references/brownfield-testing.md](references/brownfield-testing.md). Em migration, leia [references/migration-testing.md](references/migration-testing.md). Aplique somente técnicas relevantes.
9. Crie ou atualize `docs/changes/<change-id>/TEST-PLAN.md` para change. Para baseline greenfield sem convenção existente, use `docs/plans/TEST-PLAN.md`. Preserve IDs ao atualizar e não crie versões paralelas sem necessidade.
10. Valide cobertura de requirements e acceptance criteria, conflitos, assumptions, test data, ambientes, riscos, flakiness, relação com `TASK-*` e exit criteria. Identifique lacunas como `TEST_COVERAGE_GAP`.

## Limites

- Não implemente código de aplicação. A responsabilidade principal é estratégia, casos, cobertura, rastreabilidade e condições de validação; não escreva suites de testes salvo pedido explícito fora deste workflow.
- Não invente comportamento esperado, status codes, mensagens, limites, timeout, retries, ordering, durability, consistency, throughput, latência, payload, ambiente, infraestrutura ou dados reais.
- Não aceite SPEC, REVIEW, ARCHITECTURE, ADR ou PLAN como verdade absoluta. Registre `TEST_CONTEXT_CONFLICT` e bloqueie a parte afetada quando fontes divergirem.
- Use `TEST-ASSUMPTION-*` com hipótese, motivo e impacto. Use `TEST-QUESTION-*` para gaps; questão `BLOCKING` impede `Ready`.
- Não transforme teste de caracterização em requirement confirmado nem congele comportamento observado que contradiga o esperado.
- Considere unit, integration, contract, API, E2E, regression, compatibility, migration, performance, resilience, security e observability somente quando aplicáveis; não exija todos.
- Não substitua `$spec-author`, `$spec-reviewer`, `$architecture-designer`, `$adr-author` ou `$implementation-planner`.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve IDs existentes.

Consulte [references/test-scenarios.md](references/test-scenarios.md) para os cenários normativos.
