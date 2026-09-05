# Segurança de APIs e Eventos

Para APIs, avalie authn, authz, campos sensíveis, enumeration, error leakage, paginação abusiva, mass assignment, replay, idempotency abuse, input/output validation e rate limiting somente quando relevantes. Não invente rate limit, status ou modelo de autenticação.

Considere input não confiável, schema validation, injection, unsafe deserialization, path traversal, output encoding e dangerous defaults com base no stack e no fluxo real.

Para eventos, examine confiança em producer e consumer, forged events, replay, tampering, payload sensível, isolamento de tenant, DLQ e evolução de schema. Não assuma broker seguro. Diferencie retry legítimo de replay malicioso e verifique controle no consumidor efetivo.
