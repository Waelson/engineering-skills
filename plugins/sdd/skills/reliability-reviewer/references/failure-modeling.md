# Modelagem de Falhas

Descubra fluxos críticos, dependências, failure domains, caminhos sync/async, estado, componentes que acumulam backlog, guarantees, SLOs/NFRs e cenários de overload. Pergunte “como isso falha?” sem inventar indisponibilidade, volume ou comportamento.

Considere quando relevantes: dependency indisponível ou lenta, network partition, overload, datastore saturation, queue buildup, consumer lag, partial region/shard failure, restart, duplicate delivery, stale cache, partial write e lost update.

Explicite cascading chains, por exemplo: dependency lenta → workers bloqueados → fila cresce → latência aumenta → clientes repetem → offered load aumenta. Avalie partial failure, bulkheads, graceful degradation, fallback, reconciliation, replay, state rebuild, backlog drain, recovery point e recovery time somente quando aplicáveis e confirmados.

Em `GREENFIELD`, priorize failure model, capacity assumptions, dependências, retry/timeout, degradação, scaling signals e recovery sem impor arquitetura excessiva. Em `EVOLUTION`, procure regressões, retry loops, fan-out, queueing, coupling e mudança de capacity profile. Em `MIGRATION`, examine dual-write, duplicação, backlog, reconciliação, rollback, coexistência, consistência e saturação de cutover.
