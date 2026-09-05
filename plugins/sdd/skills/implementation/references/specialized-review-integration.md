# Integração de Reviews Especializados

## Papel e autoridade

`SECURITY-REVIEW.md` e `RELIABILITY-REVIEW.md` são fontes de findings, riscos, blockers, assumptions, questões e evidências. Não são fontes automáticas de novos requirements, arquitetura ou mecanismo de implementação.

Use a cadeia: review identifica risco ou gap → fonte normativa ou decisão confirmada define comportamento e abordagem → implementation executa. Diferencie `FINDING`, `RECOMMENDED MITIGATION` e `CONFIRMED IMPLEMENTATION DECISION`; somente a última autoriza uma mudança material direta.

Uma correção pode avançar quando o finding demonstra violação, o comportamento esperado e a abordagem estão confirmados, e a correção não exige novo requirement, decisão arquitetural ou mudança contratual. Caso contrário, use `IMPLEMENTATION_CONTEXT_UNRESOLVED` e pergunte ou encaminhe.

## Severidade e status

- `BLOCKER` aberto e diretamente relacionado: bloqueie a task.
- `HIGH` aberto: avalie antes da task; bloqueie se decisão estiver pendente ou a abordagem puder ser invalidada.
- `MEDIUM` ou `LOW`: não bloqueie automaticamente; avalie relação, impacto, mitigation planejada e risco de piora. Não ignore quando relevante.

Open questions permanecem questões; se `BLOCKING`, pergunte. Assumptions permanecem hipóteses até evidência ou confirmação. Recommendation como “circuit breaker”, “middleware” ou “timeout de 2s” não autoriza mecanismo ou valor. Finding `Resolved` exige conferir decisão ou evidência quando a task depender dele; status isolado não basta.

## Conflitos e trade-offs

Se review contradisser SPEC, arquitetura, ADR, API, plano ou outro review, registre `IMPLEMENTATION_CONTEXT_CONFLICT`. Não otimize silenciosamente availability, confidentiality, integrity, authorization, latency, recovery ou complexidade operacional.

Conflito security versus reliability, como fail-closed versus fail-open, requer decisão confirmada. Encaminhe regra ou comportamento a `$spec-author`, estrutura a `$architecture-designer` e trade-off arquitetural material a `$adr-author`.

## Planning, testes e novas descobertas

Finding confirmado com mitigation aprovada deve idealmente estar no IMPLEMENTATION-PLAN. Se faltar task e incluí-la alterar o plano materialmente, registre `PLAN_DEVIATION` e retorne a `$implementation-planner`. Validação ausente deve ser encaminhada a `$test-designer`.

Novo risco material descoberto durante implementação não autoriza expansão silenciosa: registre-o e recomende `$security-reviewer` ou `$reliability-reviewer`. Nunca edite o review para fazê-lo acompanhar o código.
