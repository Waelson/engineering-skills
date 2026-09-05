# Implementação de Migration

Execute apenas estados e etapas confirmados no plano, como prepare, compatibility layer, backfill, dual operation, reconciliation, cutover, verification e cleanup. Não invente a estratégia nem pule safety gates.

Respeite `MIG-*`, `COMPAT-*`, source of truth, rollback e validações. Não altere migration aplicada silenciosamente. Mudança de sequência, coexistência, consistency ou rollback é desvio material.

Antes de apagar dados, remover coluna/API/legacy path, destruir recurso ou executar cutover irreversível, valide estado, alvo, rollback e autorização; exija confirmação explícita imediatamente antes da ação. Aprovação conceitual da migration não autoriza automaticamente operação destrutiva.

Se a parte destrutiva estiver bloqueada, tasks independentes e reversíveis podem avançar quando seguro, com blocker registrado.
