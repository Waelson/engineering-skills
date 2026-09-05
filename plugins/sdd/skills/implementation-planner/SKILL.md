---
name: implementation-planner
description: Transforme specifications maduras, arquitetura correspondente e ADRs confirmados em planos de implementação incrementais, rastreáveis e verificáveis. Use para criar ou atualizar IMPLEMENTATION-PLAN.md, decompor uma mudança em tarefas, preparar execução técnica ou planejar implementação de migration. Não use para requirements discovery, spec review, arquitetura, ADR, implementação, code review ou desenho detalhado de testes.
---

# Planejador de Implementação

Converta requisitos e decisões já estabelecidos em uma sequência executável de trabalho sem resolver silenciosamente lacunas anteriores. Trabalhe em quatro fases: **Implementation Discovery → Planning Readiness Check → Plan Construction → Plan Validation**.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e identifique se o alvo é change, baseline greenfield ou migration. Respeite convenções documentais explícitas do projeto.
2. Para change, leia `SPEC.md`, `REVIEW.md` e `ARCHITECTURE.md` sob `docs/changes/<change-id>/` quando existirem; para baseline, leia `docs/spec/SPEC.md` e `docs/architecture/ARCHITECTURE.md`. Consulte ADRs relacionados em `docs/architecture/adr/`.
3. Leia integralmente [references/planning-process.md](references/planning-process.md). Inspecione proporcionalmente estrutura real, testes, módulos, CI, build, contratos, schemas e migrations necessários para tornar o plano realista. Não pergunte o que o repositório já estabelece.
4. Identifique requirements, acceptance criteria, boundaries, decisões confirmadas, dependências, riscos, comportamento a preservar, assumptions, open questions e conflitos. Nunca transforme ADR `Proposed`, recommendation ou assumption em decisão confirmada.
5. Classifique a readiness como `IMPLEMENTATION_DISCOVERY_REQUIRED`, `READY_FOR_IMPLEMENTATION_DRAFT` ou `IMPLEMENTATION_PLAN_READY`. Em lacunas materiais, faça 1 a 4 perguntas de alto impacto por rodada ou recomende retorno à skill responsável.
6. **Hard gate:** não produza `IMPLEMENTATION-PLAN.md` tratado como pronto para execução enquanto requirement ou decisão arquitetural `BLOCKING` que altere materialmente a implementação estiver sem resolução. Se o usuário pedir draft, use `Status: Draft` e exponha blockers.
7. Quando houver base suficiente, leia [references/task-decomposition.md](references/task-decomposition.md) e [references/traceability.md](references/traceability.md). Decomponha trabalho em `TASK-001`, `TASK-002`, ... com dependências reais, validação e condição de conclusão; preserve IDs ao atualizar.
8. Para migration, leia também [references/migration-planning.md](references/migration-planning.md). Inclua somente etapas de coexistência, dados, cutover, rollback e cleanup sustentadas pelos artefatos.
9. Crie ou atualize `docs/changes/<change-id>/IMPLEMENTATION-PLAN.md` para change. Para implementação fundacional greenfield, use `docs/plans/IMPLEMENTATION-PLAN.md`, salvo convenção existente. Não crie versão paralela desnecessária.
10. Valide cobertura, ordem de dependências, paralelização possível, riscos, status e rastreabilidade. Se SPEC, ARCHITECTURE e ADR divergirem, registre `IMPLEMENTATION_CONTEXT_CONFLICT` e bloqueie a parte afetada; não escolha a fonte correta.

## Limites

- Não implemente código, crie packages ou migrations, altere APIs, instale dependências, execute refactors ou escreva suites detalhadas de testes.
- Não invente requirements, tecnologia, protocolo, banco, rollout, feature flag, migration strategy, package layout, API naming, consistency, constraints, números, paths ou arquivos inexistentes.
- Siga decisões confirmadas. Quando uma decisão material estiver ausente, pergunte ou recomende `$spec-author`, `$spec-reviewer`, `$architecture-designer` ou `$adr-author`, conforme a responsabilidade.
- Use `IMPL-ASSUMPTION-*` somente para hipótese explícita, com motivo e impacto se estiver errada. Use `IMPL-QUESTION-*` para lacunas; uma questão `BLOCKING` impede status `Ready`.
- Indique tipos e pontos de validação necessários, mas deixe casos e suites detalhadas para `$test-designer`.
- Diferencie dependency order de business priority. Não invente prioridade, paralelismo ou sequência genérica.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve IDs existentes.

Consulte [references/planning-scenarios.md](references/planning-scenarios.md) para os cenários normativos.
