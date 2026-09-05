# Processo de Code Review

## Contexto e diff-first

Defina alvo, intenção, requirements/tasks, contratos, testes e convenções relevantes. Se houver diff, leia arquivos e linhas adicionadas/removidas, testes, contracts, migrations, configs e dependencies; abra contexto adjacente somente para entender comportamento, chamadas e impacto. Não varra o repositório inteiro.

Consulte quando útil `docs/changes/<change-id>/SPEC.md`, `ARCHITECTURE.md`, `API.md`, `IMPLEMENTATION-PLAN.md`, `TEST-PLAN.md`, ADRs e `AGENTS.md`, além de `SECURITY-REVIEW.md` ou `RELIABILITY-REVIEW.md` relevantes. Documentação evidencia intenção; código e testes evidenciam comportamento observado. Conflito material vira `CODE_REVIEW_CONTEXT_CONFLICT`, nunca escolha silenciosa.

## Readiness e interação

- `CODE_REVIEW_CONTEXT_UNRESOLVED`: falta informação material para determinar defeito.
- `READY_FOR_CODE_REVIEW`: contexto suficiente para avaliar o escopo.
- `CODE_REVIEW_COMPLETE`: escopo solicitado foi revisado.

Faça 1 a 3 perguntas por rodada somente se a resposta puder criar, remover ou mudar severidade/recomendação de finding. Em review extensa, forneça checkpoint conciso com arquivos revisados, contagem de findings, área em análise e questão material.

## Saída

Por padrão, apresente findings e resumo na interação. Quando persistência for solicitada ou útil para uma change, atualize `docs/changes/<change-id>/CODE-REVIEW.md`, preservando IDs. Use estrutura adaptativa com metadata, scope, inputs, summary, findings, questions, test observations, scope deviations, risks e status `Draft`, `Blocked` ou `Complete`. Não use verdict global de compliance.
