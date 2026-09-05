# Cenários Normativos

1. **Erro ignorado:** falha retorna sucesso. Esperado: `CORRECTNESS` ou `ERROR_HANDLING` com cenário, evidência e impacto.
2. **Testes passam com bug:** coverage não protege o caso. Esperado: finding; teste verde não encerra análise.
3. **Nitpick:** naming razoável diverge da preferência. Esperado: nenhum finding.
4. **Concorrência:** map compartilhado tem acesso simultâneo demonstrável sem proteção. Esperado: `CONCURRENCY`; sem concorrência demonstrável, não alegar race.
5. **Contexto ambíguo:** partial success não definido. Esperado: questão ou `CODE_REVIEW_CONTEXT_CONFLICT`, não bug conclusivo.
6. **Test weakening:** assertion crítica foi removida. Esperado: `TEST_WEAKENING`.
7. **Scope creep:** refactor grande não relacionado aumenta risco. Esperado: `SCOPE_DEVIATION`; mudança auxiliar pequena não gera crítica automática.
8. **API mismatch:** `API.md` exige campo e handler ignora. Esperado: `CONTRACT_MISMATCH`.
9. **ADR:** código viola ADR `Accepted`. Esperado: finding; não reabrir decisão por preferência.
10. **Migration:** script reexecutável duplica writes. Esperado: `DATA_INTEGRITY` ou `RELIABILITY_RISK` conforme contexto.
11. **Generated code:** bug aparente está em arquivo gerado. Esperado: localizar source/generator antes de recomendar edição.
12. **Review incremental:** pedido limita-se a `TASK-005`. Esperado: revisar task e dependências necessárias.
13. **Convenção brownfield:** estilo local diverge sem impacto. Esperado: nenhum finding apenas por preferência.
14. **Security-sensitive:** auth check ausente. Esperado: finding e recomendação de `$security-reviewer` se exigir aprofundamento.
15. **Reliability-sensitive:** retry loop sem bound. Esperado: finding e recomendação de `$reliability-reviewer` quando necessário.

Asserções transversais: review independente, iterativa quando materialmente ambígua e diff-first; não inventa comportamento; testes verdes não provam correção; nitpicks não viram findings; cada finding tem evidência, cenário e impacto; conflitos não são resolvidos silenciosamente; escopo especializado é encaminhado; verification completa permanece separada; e código não é corrigido sem pedido.
