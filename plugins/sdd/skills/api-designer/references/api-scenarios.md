# Cenários Normativos

1. **Pedido vago:** “Crie uma API para consultar clientes” inicia discovery; não gera endpoint imediatamente.
2. **Paginação sem conhecimento técnico:** explica o efeito de inserções durante navegação e pergunta pelo comportamento, sem exigir jargão.
3. **Brownfield REST:** inspeciona contrato e convenções existentes, preserva-os e pergunta somente gaps materiais.
4. **gRPC obrigatório:** trata o ADR confirmado como constraint e não debate REST sem necessidade.
5. **Partial success indefinido:** em batch, pergunta se falha é total ou por item e não inventa semântica.
6. **Breaking change:** remoção de campo exige análise e confirmação; não presume quebra permitida.
7. **Limite desconhecido:** batch size permanece `OPEN API QUESTION`; nenhum número é inventado.
8. **Event API:** processamento assíncrono não implica Kafka; contrato vem após confirmação do interaction model.
9. **Draft solicitado:** usa `Status: Draft` com assumptions e questões abertas explícitas.
10. **Conflito:** divergência entre SPEC e contrato atual gera `API_CONTEXT_CONFLICT`; nenhuma fonte é escolhida silenciosamente.
11. **Idempotência desconhecida:** explica retry e efeito duplicado em linguagem concreta antes de validar a necessidade.
12. **API existente:** atualiza `API.md`, preserva decisões confirmadas e não cria `API-v2.md` sem necessidade.

Asserções transversais: a skill é interativa diante de lacunas materiais; não assume conhecimento, protocolo ou semântica; não inventa requisitos, status, limites, timeouts ou paginação; recommendation não vira decisão; conflitos não são resolvidos silenciosamente; blockers impedem `Ready`; brownfield prioriza compatibilidade; e nenhum handler é implementado.
