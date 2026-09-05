# Testes de Migration

## Estados

Derive testes dos estados definidos:

```text
source → transition → target
```

Cubra, quando aplicável, equivalência de dados, backfill, dual-write/read, reconciliation, compatibilidade legada, cutover, rollback e segurança do cleanup. Não exija mecanismos ausentes nem invente sua semântica.

## Gates

Se source of truth, coexistência, consistência, tolerância a perda, cutover ou rollback estiver indefinido e alterar o resultado esperado, use `TEST_DISCOVERY_REQUIRED`. Encaminhe requirement à `$spec-author` e decisão técnica à `$architecture-designer` ou `$adr-author`.

## Evidência

Para cada fase usada, defina precondição, dados, ação, resultado esperado e evidência de conclusão. Inclua verificação antes e depois do cutover e rollback somente quando ele fizer parte da estratégia confirmada.
