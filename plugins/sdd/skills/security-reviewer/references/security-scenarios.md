# Cenários Normativos

1. **Contexto insuficiente:** pedido genérico sobre nova API sem authn/authz inicia discovery com perguntas curtas; nada é assumido.
2. **Autenticado sem autorização confirmada:** diferencia identidade de permissão e usa finding ou questão conforme a evidência.
3. **Internal não implica trusted:** a descrição “internal API” não comprova boundary segura.
4. **Brownfield:** endpoint novo sem middleware usado pelos antigos exige investigação e possível gap de authn/authz.
5. **Fail-open indefinido:** indisponibilidade do policy service gera pergunta `BLOCKING`; comportamento não é inventado.
6. **Dados sensíveis:** novo campo sem requirement de exposição gera questão e análise; permissão não é presumida.
7. **Token em log:** gera `SECRET_EXPOSURE` ou `DATA_EXPOSURE` conforme contexto e evidência.
8. **SPEC versus código:** requirement de admin sem role check gera `SECURITY_CONTEXT_CONFLICT` e finding adequado.
9. **Migration:** coexistência de legacy e new path com controles distintos é investigada como bypass.
10. **Draft solicitado:** produz `Security Review` com `Status: Draft`, assumptions e questões explícitas.
11. **Controle documentado não aplicado:** route sem middleware invalida a mitigation meramente documental.
12. **Review existente:** atualiza `SECURITY-REVIEW.md`, preserva IDs e não cria cópia versionada sem necessidade.

Asserções transversais: não assumir authn, authz, rede confiável, dados não sensíveis ou controle aplicado; não inventar requirements ou controles; separar observado de esperado; consultar evidências antes de perguntar; fazer rodadas curtas; não resolver conflitos; não equiparar ausência de evidência a segurança; sustentar findings; e não corrigir silenciosamente.
