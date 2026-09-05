# Orientação gRPC

Use somente quando gRPC estiver confirmado. Defina services, methods, unary ou streaming, request/response messages, status semantics, deadlines, idempotência e paginação apenas conforme requisitos e constraints.

Preserve compatibilidade de field numbers e nunca reutilize números removidos. Avalie adição e remoção de campos, defaults e evolução de enums com base nos consumidores. Não invente deadline, limite de mensagem ou estratégia de retry.
