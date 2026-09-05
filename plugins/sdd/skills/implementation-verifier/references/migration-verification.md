# Verificação de Migration

Verifique estados source, transition e target e, quando definidos, dual-write/read, backfill, reconciliation, compatibility, cutover, rollback e cleanup. Código do estado final não comprova segurança da transição.

Relacione cada `MIG-*` e `COMPAT-*` a evidência de execução ou validação. Se rollback ou cutover previsto não foi testado, use `MIGRATION_GAP` ou `NOT_VERIFIED`; não invente resultado.

Não execute operação destrutiva para verificar sem autorização explícita e ambiente adequado. Verificação documental ou em ambiente seguro deve declarar seus limites.
