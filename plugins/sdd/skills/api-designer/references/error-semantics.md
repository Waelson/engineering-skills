# Semântica de Erros

Descubra primeiro quais falhas o consumidor precisa distinguir, quais são domain/client errors, quais são transient failures, quais permitem retry e que informação pode ser exposta. Só então mapeie-as para HTTP, gRPC ou semântica de eventos.

Não invente códigos, status ou envelopes. Considere autenticação, autorização, tenant context, campos sensíveis, leakage e auditabilidade quando relevantes. Quando distinguir “não existe” de “sem permissão” alterar segurança ou comportamento do consumidor, faça uma pergunta explícita.

Documente condição, representação, retryability e impacto para cada falha material confirmada. Não confunda falha de transporte com erro de domínio.
