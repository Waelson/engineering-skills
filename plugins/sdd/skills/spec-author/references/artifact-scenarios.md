# Cenários de Roteamento de Artefatos

Use estes cenários como testes de decisão. O comportamento esperado é normativo; adapte o conteúdo da specification ao projeto.

## 1. Greenfield

Repositório com `README.md` e `src/`, sem implementação relevante. Pedido: “Crie uma especificação para um novo MCP Registry.”

- Contexto: `GREENFIELD`
- Operação: `CREATE_BASELINE`
- Resultado: criar `docs/spec/SPEC.md`
- Invariante: não criar diretório de change.

## 2. Brownfield com baseline

Existe `docs/spec/SPEC.md`. Pedido: “Adicione autorização em lote à API de autorização existente.”

- Contexto: `EVOLUTION`
- Baseline: `ESTABLISHED` ou `PARTIAL`, conforme cobertura
- Operação: `CREATE_CHANGE_SPEC`
- Resultado: criar `docs/changes/batch-authorization/SPEC.md`
- Invariante: manter a baseline inalterada.

## 3. Brownfield sem baseline

Existem implementação e testes, mas não `docs/spec/SPEC.md`. Pedido: “Adicione autorização em lote.”

- Contexto: `EVOLUTION`
- Baseline: `ABSENT`
- Operação: `CREATE_CHANGE_SPEC`
- Resultado: criar `docs/changes/batch-authorization/SPEC.md`
- Conteúdo: estado atual reconstruído somente para o escopo, com evidências
- Invariante: não criar automaticamente `docs/spec/SPEC.md`.

## 4. Migração

Pedido: “Migre o armazenamento de políticas do MySQL para a nova camada de storage.”

- Contexto: `MIGRATION`
- Operação: `CREATE_CHANGE_SPEC`
- Resultado: criar `docs/changes/migrate-policy-storage/SPEC.md`
- Conteúdo: aspectos relevantes dos estados atual, de transição e alvo.

## 5. Reconstrução explícita da baseline

Sistema existente sem baseline. Pedido: “Crie uma specification baseline documentando o sistema atual.”

- Contexto: `EVOLUTION`
- Baseline: `ABSENT`
- Operação: `RECONSTRUCT_BASELINE`
- Resultado: criar `docs/spec/SPEC.md` a partir de evidências do projeto.

## 6. Reconciliação de mudança concluída

Existem `docs/spec/SPEC.md` e `docs/changes/batch-authorization/SPEC.md`. Pedido: “A funcionalidade de autorização em lote foi concluída. Atualize a baseline.”

- Operação: `RECONSTRUCT_BASELINE`
- Resultado: atualizar `docs/spec/SPEC.md`
- Evidências: baseline existente, change spec e implementação ou contexto verificado
- Invariante: consolidar o estado final; não copiar ou concatenar a change spec.

## Asserções transversais

Para todos os cenários:

- gerar no máximo um artefato de specification por operação;
- usar `docs/` por padrão e nunca a raiz do repositório;
- não criar arquitetura, ADR, plano, review ou código;
- não inventar uma baseline completa quando ela estiver ausente ou parcial;
- não alterar a baseline por consequência implícita de uma change spec.
