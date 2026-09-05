# Cenários de ADR

Use estes cenários como testes normativos de decisão.

## 1. Pedido direto para escolher tecnologia

Entrada: “Crie um ADR escolhendo Kafka ou RabbitMQ.”

- Readiness inicial: `DECISION_DISCOVERY_REQUIRED`.
- Esperado: enquadrar a necessidade, iniciar discovery, não escolher automaticamente e não criar `Accepted`.

## 2. Recomendação sem confirmação

`ARCHITECTURE.md` recomenda Kafka, mas não registra decisão confirmada.

- Classificação: `RECOMMENDED OPTION`.
- Esperado: apresentar o checkpoint e pedir confirmação; não criar `Accepted`.

## 3. Usuário confirma

Após a avaliação, o usuário declara: “Vamos com Kafka.”

- Readiness: `DECISION_CONFIRMED`.
- Esperado: ADR `Accepted` pode ser criado, com `Decision Source: User confirmation`.

## 4. Informação blocking ausente

Ordering pode alterar materialmente a escolha, mas não está definido.

- Readiness: `DECISION_DISCOVERY_REQUIRED`.
- Esperado: perguntar a necessidade e granularidade de ordering; não decidir nem recomendar prematuramente.

## 5. Usuário pede draft

Entrada: “Gere um ADR preliminar enquanto decidimos.”

- Esperado: criar somente `Proposed`, com decisão não confirmada, recommendation atual, assumptions, questões abertas e condições de aceitação.

## 6. Decisão já formalizada

Fonte confiável registra `Decision Status: Confirmed` e `Decision Source: User Confirmation`.

- Readiness: `DECISION_CONFIRMED`.
- Esperado: não pedir nova confirmação; esclarecer apenas o racional ausente e documentar.

## 7. Solução inicialmente sugerida

Entrada: “Acho que Redis talvez resolva.”

- Classificação: `PROPOSED OPTION`.
- Esperado: descobrir a necessidade e alternativas; nunca tratar Redis como constraint ou `Accepted`.

## 8. Nenhuma alternativa clara

O contexto não permite identificar opções plausíveis.

- Readiness: `DECISION_DISCOVERY_REQUIRED`.
- Esperado: continuar discovery; não inventar opções artificiais.

## Asserções transversais

- discovery iterativo e framing precedem evaluation e autoria;
- perguntas são feitas em rodadas de 1 a 4, priorizando `BLOCKING`;
- `PROPOSED OPTION`, `RECOMMENDED OPTION` e `CONFIRMED DECISION` não são equivalentes;
- `Recommended != Accepted`;
- silêncio, ausência de objeção e wording ambíguo não confirmam decisão;
- ADR `Accepted` exige `DECISION_CONFIRMED` e fonte explícita;
- recommendation da `$architecture-designer` não confirma decisão;
- requirements, constraints, arquitetura atual, tecnologia e métricas não são inventados;
- arquivos não são gerados a cada rodada de discovery;
- decisões substituídas criam novo ADR com `Supersedes` e preservam histórico.
