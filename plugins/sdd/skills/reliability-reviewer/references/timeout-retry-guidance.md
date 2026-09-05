# Timeouts, Retries e Idempotência

Para timeouts, verifique camada, alinhamento ao latency budget confirmado, deadlines encadeados e propagação de cancelamento. Não invente valores nem assuma que timeout configurado é adequado.

Para retries, identifique erros elegíveis, backoff/jitter, budget, número de camadas e efeito sobre carga. Calcule ou descreva amplification quando client, gateway e service repetem a mesma operação. Retry não é automaticamente benéfico e pode agravar falha.

Antes de repetir operação com side effects, confirme idempotência, tolerância a duplicação, idempotency key ou deduplication. Não presuma delivery única ou ordering. Fail-open/fail-closed, fallback e circuit breaker são decisões contextuais; pergunte quando materiais e não os recomende por padrão.
