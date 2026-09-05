# Análise de Trade-offs

## Requisitos antes de tecnologia

Comece pela capacidade, restrição ou quality attribute. “Processamento assíncrono e durável” é requisito; Kafka é uma opção. Não selecione Redis, Kubernetes, PostgreSQL, ClickHouse, DynamoDB, gRPC, REST ou service mesh por preferência.

## Estrutura de decisão

Para cada decisão relevante:

1. Cite os requisitos, constraints e failure modes que motivam a decisão.
2. Defina critérios relevantes, como complexidade, latência, disponibilidade, consistência, escala, custo operacional, compatibilidade e comportamento de falha.
3. Apresente alternativas viáveis, incluindo manter a arquitetura atual quando aplicável.
4. Compare benefícios, custos, riscos e condições de validade.
5. Recomende somente quando houver evidência suficiente; não trate recomendação como decisão confirmada.
6. Registre `Status: Proposed` quando depender de confirmação e `Status: Accepted` somente com fonte confiável.
7. Indique **Decisão Arquitetural Necessária** quando a escolha merecer ADR.

Exemplo:

```markdown
### Propagação de atualizações

Requisitos relacionados: NFR-004, COMPAT-002

#### Opção A — Propagação síncrona

Benefícios:
- consistência imediata mais simples de compreender;

Custos e riscos:
- disponibilidade acoplada ao downstream;
- latência no caminho de escrita.

#### Opção B — Propagação orientada a eventos

Benefícios:
- desacoplamento de disponibilidade;
- reprocessamento independente.

Custos e riscos:
- consistência eventual;
- semântica adicional de retry, ordering e duplicação.

Recomendação: <opção e justificativa baseada nos requisitos>
Status: Proposed | Accepted
Source: <requirement, ADR, constraint ou confirmação>
ADR necessário: sim | não
```

Não invente números nem afirme que uma opção “escala” sem relacioná-la a volume, cardinalidade, particionamento ou outro requisito verificável.
