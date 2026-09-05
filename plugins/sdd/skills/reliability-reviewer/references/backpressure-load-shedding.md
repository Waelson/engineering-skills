# Backpressure, Queues e Load Shedding

Avalie bounded queues, buffer, producer behavior, consumer lag, queue depth, age of oldest message, produção versus consumo, poison messages, retry loops e DLQ quando relevantes. Queue crescente pode ser sintoma, não causa; não conclua sem evidência.

Backpressure exige mecanismo pelo qual o consumidor ou sistema limite entrada. Load shedding exige definição do que pode ser rejeitado, prioridades, sinal de overload e interação com scaling. Não recomende shedding automaticamente.

Separe `offered load`, `served load`, `rejected load` e `queued load`. Throughput processado sozinho não mede demanda quando há rejeição ou backlog. Considere admission control e isolamento de pools, queues, tenants ou priority classes somente quando o risco justificar.
