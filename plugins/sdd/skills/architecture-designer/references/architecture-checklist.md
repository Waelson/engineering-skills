# Checklist de Design Arquitetural

Use somente os tópicos relevantes aos requisitos e ao contexto.

## Componentes e boundaries

Para cada componente relevante, registre responsabilidade, inputs, outputs, dependências, ownership de dados e failure boundary. Evite nomes vazios como Manager, Helper ou Processor sem responsabilidade explícita.

## Dados

Esclareça source of truth, quem escreve e lê, cache versus dado autoritativo, replicação, retenção e consistência esperada. Não introduza armazenamento ou cache sem requisito.

## Comunicação

Para interações importantes, avalie sincronismo, request/response, events, commands ou streaming, além de timeout, retry, idempotência, ordering e delivery guarantees. Escolha protocolo somente quando necessário e justificado.

## Confiabilidade e falhas

Pergunte “o que acontece quando este componente falha?”. Conforme o contexto, avalie indisponibilidade, latência, falha parcial, network partition, inconsistência, consumer lag e overload, além de timeout, retry budget, jitter, circuit breaker, bulkhead, backpressure, load shedding, queue bounds, rate limiting, degradação, fallback e recovery.

Não aplique todos os mecanismos indiscriminadamente. Cada mecanismo deve responder a um failure mode ou requisito real.

## Escalabilidade e capacidade

Use dados reais de throughput e capacidade. Avalie horizontal/vertical scaling, partitioning, sharding, replication, boundaries stateful/stateless, hotspots, cardinalidade, fan-out e crescimento de filas quando relevantes. Se faltarem valores essenciais, crie `ARCH-QUESTION-*`; não use “escalável” como justificativa.

## Segurança

Mapeie requisitos de autenticação, autorização, isolamento entre tenants, trust boundaries, secrets, dados sensíveis, encryption, auditoria e privilégios. Destaque security boundaries quando melhorarem a compreensão.

## Observabilidade

Defina sinais arquiteturais suficientes para operar e diagnosticar: logs, métricas, traces, auditoria, saturação, profundidade de fila, latência de dependências, taxa de erro e capacidade. Não crie dashboards detalhados.

## APIs e contratos

Defina características arquiteturais necessárias das interfaces sem detalhar schemas completos quando isso pertencer a uma etapa posterior. Relacione contratos públicos, compatibilidade e versionamento aos requisitos.

## Data e failure flows

Descreva o fluxo normal e os principais caminhos de falha. Use Mermaid quando o relacionamento ou a sequência ficar materialmente mais claro:

```mermaid
flowchart LR
    Client --> AccessLayer
    AccessLayer --> Registry
```

Use sequence diagram somente quando o comportamento temporal for relevante.

## Rastreabilidade

Mapeie requisitos arquiteturalmente relevantes de forma concisa:

```text
FR-004 → Component: Batch Authorization Handler
NFR-003 → Decision: bounded queue + load shedding
```

Não crie mapeamento mecânico para requisitos sem impacto arquitetural.

## Incertezas

Use:

```text
ARCH-ASSUMPTION-001: <hipótese não confirmada usada no draft>
ARCH-QUESTION-001: <informação necessária para decisão>
```

Não converta assumption em fato. Se a incerteza impedir design responsável, marque `ARCHITECTURE_DISCOVERY_REQUIRED`.

## Anti-over-engineering

Questione qualquer microservice, broker, cache distribuído, CQRS, event sourcing, service mesh ou multi-region sem requisito claro. A arquitetura deve ser tão simples quanto possível e tão complexa quanto necessário.
