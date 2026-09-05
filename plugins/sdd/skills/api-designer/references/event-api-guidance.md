# Orientação para Eventos

Use somente quando eventos ou interface assíncrona estiverem confirmados. Não assuma broker. Descubra event name, producer, consumidores, payload, evolução de schema, ordering, partition key, delivery semantics, duplicação, idempotência, replay, versionamento e dead-letter behavior apenas quando relevantes.

Um requirement de processamento assíncrono não confirma Kafka nem o interaction model completo. Semânticas como at-least-once devem ser explicadas brevemente e confirmadas quando afetarem duplicação, retry ou consumidor.
