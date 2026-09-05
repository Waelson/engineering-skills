# Compatibilidade e Evolução

Em `EVOLUTION`, represente `Current Contract → Required Change → Target Contract`. Avalie impacto real sobre consumidores antes de remover, renomear, tornar obrigatório ou mudar tipo, default, enum, semântica ou comportamento de erro.

Mudanças aditivas podem também quebrar consumidores rígidos. Considere backward e forward compatibility, versionamento, default values, enum evolution, deprecation e consumer migration conforme o ecossistema observado. Não presuma que breaking change é permitido; pergunte se isso não estiver confirmado.

Em `MIGRATION`, trate coexistência old/new, adapters, transição de versão, migração de consumidores, deprecation e cutover apenas quando sustentados pelos artefatos. Não invente estratégia. Em `GREENFIELD`, foque consumidores e casos de uso sem simular legado inexistente.
