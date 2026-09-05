# Processo de Security Review

## Contexto e readiness

Para changes, consulte `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `API.md`, `IMPLEMENTATION-PLAN.md`, `TEST-PLAN.md` e `VERIFICATION.md` sob `docs/changes/<change-id>/`, quando existirem. Consulte também baseline, ADRs e evidência técnica relevante sem varrer o repositório inteiro.

- `SECURITY_DISCOVERY_REQUIRED`: falta contexto para avaliar risco material; faça perguntas e não conclua.
- `READY_FOR_SECURITY_REVIEW`: fontes e contexto bastam para avaliar o escopo.
- `SECURITY_REVIEW_COMPLETE`: pontos avaliados possuem evidência suficiente e nenhum blocker impede a conclusão.

Perguntas podem ser `BLOCKING`, `IMPORTANT` ou `OPTIONAL`. Questão blocking impede `Complete` somente quando afeta a conclusão do escopo.

## Revisão baseada em evidência

Relacione intention, requisito, contrato, configuração e comportamento observado. Uma afirmação de que middleware, IAM, encryption ou validação mitiga risco exige evidência de aplicação ao path e de que o controle produz o comportamento necessário. Testes passando não provam segurança absoluta; examine as assertions.

Se a evidência for insuficiente, use `OPEN SECURITY QUESTION`. Se fontes divergirem, registre `SECURITY_CONTEXT_CONFLICT` com fontes, impacto e validação necessária. Não resolva o conflito silenciosamente.

## Artefato e conclusão

Persista somente quando solicitado em `docs/changes/<change-id>/SECURITY-REVIEW.md`, atualizando o arquivo existente e preservando IDs. Use estrutura adaptativa com metadata, scope, inputs, context, boundaries, requirements, assumptions, questions, findings, reviews temáticas, risks, status e next actions. Status permitidos: `Draft`, `Blocked` e `Complete`.

Por padrão, encerre com findings e validações necessárias; não remedeie. Ausência de findings significa apenas que nenhum foi identificado no escopo e com a evidência disponível, nunca prova de segurança absoluta.
