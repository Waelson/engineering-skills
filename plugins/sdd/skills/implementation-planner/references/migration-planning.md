# Planejamento de Migration

## Princípio

Derive a transição de `MIG-*`, `COMPAT-*`, arquitetura e ADRs confirmados. Não invente dual-write, shadowing, feature flag, backfill, canary ou estratégia de cutover.

## Sequência adaptativa

Considere somente quando aplicável:

```text
prepare
  ↓
introduce compatibility
  ↓
backfill
  ↓
dual operation
  ↓
reconciliation
  ↓
cutover
  ↓
validation
  ↓
rollback window
  ↓
legacy cleanup
```

Para cada etapa usada, registre precondições, dependências, validação, falhas, rollback e critério de avanço. Não force todas as etapas.

## Gate de decisões

Bloqueie a parte afetada quando faltarem decisões materiais sobre coexistência, source of truth, ordering, consistência, backfill, cutover, rollback ou tolerância a perda. Encaminhe requirement para `$spec-author` e decisão arquitetural para `$architecture-designer` ou `$adr-author`.

## Segurança da transição

Quando suportado pelo contexto, prefira mudanças backward-compatible antes do cutover, valide dados antes de mudar o source of truth, prepare observabilidade antes do rollout e deixe cleanup após o fim da janela de rollback. Essas são orientações condicionais, não decisões presumidas.
