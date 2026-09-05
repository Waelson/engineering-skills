# Revisão de Testes

Teste verde não prova corretude. Confirme que cenário e assertion exercitam o comportamento relevante, inclusive erros, branches e boundary conditions quando materiais. Verifique falso positivo, assertion fraca, mock que mascara integração, teste removido e comportamento esperado relaxado.

Registre `TEST_WEAKENING` quando a mudança reduz proteção de comportamento importante, com diff e cenário que deixou de ser coberto. Use `TEST_GAP` quando o código introduz branch ou risco material sem validação adequada. Não exija teste para todo detalhe nem altere teste apenas por preferência.

Ao revisar testes existentes, não transforme seu expected value em requirement automaticamente. Compare com SPEC, API, ADR e comportamento confirmado; divergência material é conflito de contexto.
