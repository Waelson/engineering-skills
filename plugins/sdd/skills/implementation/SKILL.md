---
name: implementation
description: Implemente mudanças SDD incrementalmente a partir de specifications, arquitetura, contratos de API, ADRs, implementation plan e test plan validados, preservando rastreabilidade e segurança. Use para implementar uma change, executar um plano ou TASK específica, desenvolver uma feature ou migration. Não use para requirements discovery, spec review, arquitetura, API design, ADR, planning, test design ou verificação independente.
---

# Implementação

Execute decisões previamente estabelecidas e valide continuamente o alinhamento entre intenção documental e realidade do repositório. Trabalhe em cinco fases: **Implementation Context Validation → Execution Readiness Check → Incremental Implementation → Continuous Validation → Implementation Completion Check**.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e os artefatos relevantes: change `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `API.md`, `SECURITY-REVIEW.md`, `RELIABILITY-REVIEW.md`, `IMPLEMENTATION-PLAN.md`, `TEST-PLAN.md`, baseline, ADRs e convenções do projeto. `API.md` é contexto obrigatório quando a task envolver interface ou contrato; reviews especializados são consultados quando existirem e forem relevantes. A ausência desses artefatos não bloqueia automaticamente uma mudança fora de seu escopo.
2. Leia integralmente [references/context-validation.md](references/context-validation.md). Inspecione código, testes, build, CI, schemas, migrations, contratos formais, APIs, configuração, dependencies, generated code e feature flags proporcionais ao escopo. Documentos expressam intenção; valide-os contra o repositório.
3. Classifique a readiness como `IMPLEMENTATION_CONTEXT_UNRESOLVED`, `READY_FOR_INCREMENTAL_IMPLEMENTATION` ou `IMPLEMENTATION_READY_FOR_VERIFICATION`. Bloqueie somente a parte afetada quando tasks independentes puderem avançar com segurança.
4. Leia [references/specialized-review-integration.md](references/specialized-review-integration.md) quando houver review especializado aplicável. **Hard gate:** nunca implemente silenciosamente decisão material que permaneça assumption, open question, recommendation, proposed option ou ADR `Proposed`. Finding `BLOCKER` aberto diretamente relacionado bloqueia a task; finding `HIGH` aberto deve ser avaliado antes de implementá-la e bloqueia quando depende de decisão ou pode invalidar a abordagem. Conflito material entre fontes gera `IMPLEMENTATION_CONTEXT_CONFLICT`; bloqueie a task afetada e não escolha silenciosamente.
5. Leia [references/implementation-process.md](references/implementation-process.md). Se existir plano, siga dependências e implemente uma unidade `TASK-*` coerente por vez. Para pedido de task única, limite-se a ela e às dependências estritamente necessárias.
6. Antes de cada task, confirme objetivo, requirements, arquitetura, `API.md` quando aplicável, ADRs, findings de security/reliability relacionados, decisões, plano, TEST-PLAN, código atual, dependências, áreas e completion criteria. Classifique diferenças usando [references/implementation-deviations.md](references/implementation-deviations.md); não altere requisito, arquitetura, contrato ou plano materialmente sem resolução.
7. Implemente o menor delta necessário, execute validações relevantes incrementalmente e só marque task concluída quando código, testes, critérios e rastreabilidade estiverem satisfeitos.
8. Em brownfield, leia [references/brownfield-implementation.md](references/brownfield-implementation.md). Em migration, leia [references/migration-implementation.md](references/migration-implementation.md) e respeite os gates operacionais e destrutivos.
9. Ao final, execute build, testes e checks realmente definidos pelo projeto quando aplicáveis. Diferencie falha preexistente de regressão nova e reporte limitações.
10. Declare somente “pronta para verificação independente” ao atingir `IMPLEMENTATION_READY_FOR_VERIFICATION`; não se autoaprove como totalmente aderente. Recomende `$implementation-verifier`.

## Limites

- Não invente requirements, decisões arquiteturais, tecnologia, contrato, strategy, timeout, retries, TTL, pools, filas, workers, réplicas, partições, shards, rate limits, metas ou outros valores operacionais.
- A `$api-designer` define e valida o contrato; a `$implementation` implementa decisões confirmadas. Quando `API.md` existir e for relevante para a task, nenhuma mudança de contrato pode ser implementada sem validar consistência com esse artefato.
- `SECURITY-REVIEW.md` e `RELIABILITY-REVIEW.md` fornecem findings, riscos, blockers e evidências especializadas; não criam automaticamente requirements ou decisões arquiteturais. Recommendation não é decisão confirmada, assumption não é fato e questão aberta não pode ser respondida por inferência.
- A `$security-reviewer` analisa riscos de segurança e a `$reliability-reviewer` analisa failure modes e riscos operacionais. Implemente diretamente somente quando o comportamento esperado e a abordagem necessária já estiverem confirmados; caso contrário, retorne à skill responsável ou ao usuário.
- Não invente endpoints, methods, RPCs, events, status codes, schemas, limites, idempotência, paginação ou error semantics. Não altere `API.md` para fazê-lo acompanhar o código; pare, explique e retorne à `$api-designer` quando surgir nova decisão de contrato.
- Não trate código existente como comportamento requerido. Diferencie `OBSERVED CURRENT BEHAVIOR` de `CONFIRMED REQUIRED BEHAVIOR` e registre `IMPLEMENTATION_CONTEXT_CONFLICT` quando divergirem.
- Não altere testes apenas para fazer o código passar. Valide testes aparentemente incorretos contra SPEC e acceptance criteria antes de editá-los.
- Não altere `SECURITY-REVIEW.md` ou `RELIABILITY-REVIEW.md` para fazê-los acompanhar o código. Status `Complete` ou finding `Resolved` exige evidência contextual quando a task depender dele.
- Não modifique generated code diretamente quando houver fonte e processo de geração. Não altere migration aplicada silenciosamente nem introduza breaking change sem evidência de que é permitido.
- Evite “while I'm here”: refactor amplo, cleanup, rename massivo, upgrade ou dependency update fora do escopo vira `OUT_OF_SCOPE_OBSERVATION`.
- Mudança pequena, reversível e local pode avançar apenas quando não altera requirement, arquitetura, contrato ou dependency material.
- Não faça commit, push, merge ou abra PR sem pedido explícito.
- Exija confirmação adicional imediatamente antes de apagar dados, remover coluna/API/legacy path, destruir recurso ou executar cutover irreversível, mesmo quando a migration conceitual estiver aprovada.
- Escreva no idioma do usuário, salvo convenção aplicável. Preserve IDs e histórico lógico.

Consulte [references/implementation-scenarios.md](references/implementation-scenarios.md) para os cenários normativos.
