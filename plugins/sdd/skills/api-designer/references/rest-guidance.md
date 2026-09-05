# Orientação REST

Use somente quando REST estiver confirmado. Avalie resources, URIs, métodos, status, request/response, headers, paginação, filtering, sorting, idempotência, conditional requests, concorrência, erros e versionamento apenas quando aplicáveis.

Evite RPC disfarçado quando a necessidade for naturalmente uma consulta ou recurso, mas não imponha REST purista a commands/actions reais. Não derive idempotência apenas de `POST` ou `PUT`; derive-a do efeito de domínio.

Não adicione `/v1`, page size, filtros ou status codes por hábito. Paginação exige necessidade confirmada; escolha offset, cursor ou token considerando volume, ordering stability e consistência durante navegação. Se isso mudar o contrato e estiver indefinido, pergunte.
