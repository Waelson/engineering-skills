# Cenários Normativos

1. **Contexto insuficiente:** pedido genérico sem failure semantics inicia discovery; nenhuma resiliência é presumida.
2. **Retry amplification:** retries em múltiplas camadas geram finding rastreável.
3. **Queue sem limite:** producer acima do consumer leva a `UNBOUNDED_QUEUE` ou `BACKPRESSURE_GAP` conforme evidência.
4. **Shedding sem offered load:** scaling baseado apenas em served load exige análise da demanda rejeitada invisível.
5. **CPU como único sinal:** saturação anterior em queue/latency gera `AUTOSCALING_GAP` ou `SATURATION_RISK`.
6. **Fail-open indefinido:** gera pergunta `BLOCKING`; a skill não decide.
7. **NFR vago:** “alta disponibilidade” gera `RELIABILITY_REQUIREMENT_GAP`; nenhum target é inventado.
8. **Migration:** dual-write com carga temporária maior gera capacity risk sem presumir suporte.
9. **Retry sem idempotência:** side effects repetíveis geram `IDEMPOTENCY_GAP` ou `RETRY_RISK`.
10. **Dependency lenta:** ausência comprovada de timeout gera `TIMEOUT_GAP`.
11. **SPEC versus código:** fail-fast versus retries longos gera `RELIABILITY_CONTEXT_CONFLICT`.
12. **Review existente:** atualiza `RELIABILITY-REVIEW.md`, preserva IDs e não cria cópia versionada.

Asserções transversais: não assumir retry, timeout, fallback, backpressure, shedding, scaling ou capacity; não inventar métricas; separar observado de esperado; consultar evidências antes de perguntar; fazer rodadas curtas; não resolver conflitos; sustentar findings; e não corrigir silenciosamente.
