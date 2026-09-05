# Convenção de Diretórios SDD

## Estrutura padrão

Use na ausência de convenção explícita incompatível:

```text
project-root/
├── AGENTS.md
├── README.md
└── docs/
    ├── spec/
    ├── changes/
    └── architecture/
        └── adr/
```

Prepare diretórios, não artefatos de conteúdo. Diretórios vazios podem receber `.gitkeep` somente para persistirem no Git.

## Semântica dos artefatos futuros

- `docs/spec/SPEC.md`: baseline vigente; pertence a `$spec-author`.
- `docs/changes/<change-id>/SPEC.md`: specification de uma mudança; pertence a `$spec-author`.
- `docs/changes/<change-id>/REVIEW.md`: review persistida da mudança; pertence a `$spec-reviewer`.
- `docs/changes/<change-id>/ARCHITECTURE.md`: arquitetura proposta da mudança; pertence a `$architecture-designer`.
- `docs/architecture/ARCHITECTURE.md`: arquitetura baseline vigente; pertence a `$architecture-designer`.
- `docs/architecture/adr/ADR-<NNN>-<slug>.md`: decisão arquitetural; pertence a `$adr-author`.

Não crie esses arquivos durante o bootstrap. A ausência de qualquer baseline é válida nessa etapa.

## Conflitos e mapeamento

Uma convenção existente tem precedência até que o usuário autorize mudança. Quando paths diferentes já possuírem a mesma responsabilidade, evite duplicidade e registre no `AGENTS.md` o mapeamento escolhido. Não crie `docs/architecture/adr/` se isso contradisser uma decisão pendente sobre `design/adr/` ou equivalente.
