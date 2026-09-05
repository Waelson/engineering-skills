# Estratégia de Testes

## Menor camada suficiente

Escolha a camada mais barata e determinística que valide corretamente o comportamento:

- regra de domínio → unit;
- interação entre componentes → integration;
- contrato público ou compatibilidade → contract/API;
- fluxo crítico entre boundaries → E2E.

Evite concentrar cobertura em E2E. Considere regression, compatibility, migration, performance, load, resilience, security e observability somente quando requirements ou riscos justificarem.

## Caminhos e falhas

Para cada comportamento relevante, avalie conforme o contexto happy path, entrada inválida, dado ausente, unauthorized, dependência indisponível ou lenta, duplicação, partial failure e boundary conditions. Para sistemas distribuídos, considere timeout, retry, idempotência, network failure, saturation, backpressure, degraded mode e recovery somente quando aplicáveis.

Não invente a resposta esperada. Se fail-open/closed, partial failure, ordering ou retry behavior estiver indefinido, crie `TEST-QUESTION-*` e aplique o gate.

## Performance e capacidade

Crie testes quantitativos somente com métricas confirmadas. Sem throughput, percentil, latência, carga ou tamanho definidos, registre pergunta aberta; nunca preencha valores de exemplo como metas reais.

## Segurança e observabilidade

Derive segurança apenas de requirements aplicáveis: authentication, authorization, privilege boundaries, tenant isolation, auditabilidade, dados sensíveis, invalid input e abuse paths. Não substitua security review.

Quando houver requisito de observabilidade, valide emissão e correlação de métricas, logs, traces, eventos de auditoria ou visibilidade de falha conforme definido.

## Dados, ambientes e flakiness

Prefira dados sintéticos, fixtures determinísticas ou dados anonimizados. Não use dados reais sensíveis. Não presuma local, CI, staging ou ambiente efêmero; descubra a convenção ou registre necessidade.

Identifique riscos de flakiness por dependência externa, timing, consistência eventual, relógio, concorrência ou estado compartilhado. Recomende isolamento ou controle determinístico quando a causa estiver sustentada.

## Sequência

Quando fizer sentido, antecipe contract/unit, depois integration, compatibility/migration, E2E e por fim performance/resilience. Essa ordem é condicional às dependências e aos riscos, não um template obrigatório.
