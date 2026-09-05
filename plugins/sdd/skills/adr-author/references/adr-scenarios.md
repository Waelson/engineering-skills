# Cenários de ADR

Use estes cenários como testes normativos de decisão.

## 1. Decisão insuficientemente definida
Entrada: “Crie um ADR para usar Kafka.”
- Readiness: `DECISION_DISCOVERY_REQUIRED`.
- Esperado: não criar `Accepted`; descobrir a necessidade e perguntar se Kafka é constraint ou `PROPOSED OPTION`.

## 2. Decisão explicitamente confirmada
O usuário afirma que Kafka foi decidido para propagação de eventos, e spec e arquitetura sustentam os drivers.
- Readiness: `DECISION_CONFIRMED`.
- Esperado: criar ADR `Accepted`, com drivers, alternativas, consequências, trade-offs e rastreabilidade.

## 3. Recomendação arquitetural
`ARCHITECTURE.md` recomenda event-driven, sem confirmação da escolha.
- Esperado: no máximo ADR `Proposed`; recommendation não se torna decision.

## 4. Requirement ausente
A decisão depende de ordering, mas o requirement não existe.
- Esperado: discovery; não inventar ordering; registrar bloqueio por requisito ausente e recomendar `$spec-author` quando crítico.

## 5. ADR existente
A mesma decisão já está registrada.
- Esperado: não criar duplicata; informar o ADR existente.

## 6. Decisão substituída
Uma nova escolha substitui ADR aceito anterior.
- Esperado: criar novo ADR, usar `Supersedes` e preservar o histórico anterior.

## 7. Technology bias
Entrada: “Redis ou Kafka?”
- Esperado: investigar problema, drivers e constraints antes de comparar; não escolher por preferência.

## 8. Draft solicitado
Entrada: “Faça um ADR preliminar com o que temos.”
- Readiness: `READY_FOR_ADR_DRAFT`, quando houver base coerente.
- Esperado: `Status: Proposed`, com assumptions e open questions explícitas.

## Asserções transversais

- lacunas materiais tornam a interação iterativa;
- fatos, constraints, assumptions, questões, opções, recomendações e decisões confirmadas permanecem separados;
- requisitos, contexto, tecnologias e números não são inventados;
- ADR `Accepted` exige confirmação;
- ADRs ficam em `docs/architecture/adr/` por padrão;
- numeração deriva da inspeção dos arquivos existentes;
- mudanças de decisão criam novo ADR e preservam o anterior;
- spec, review, architecture e ADRs existentes são consultados antes de perguntas desnecessárias.
