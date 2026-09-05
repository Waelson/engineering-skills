# Processo e Lifecycle de ADR

## Convenção documental

Na ausência de convenção explícita diferente em `AGENTS.md`, use:

```text
docs/
├── spec/
│   └── SPEC.md
├── architecture/
│   ├── ARCHITECTURE.md
│   └── adr/
│       └── ADR-<NNN>-<slug>.md
└── changes/
    └── <change-id>/
        ├── SPEC.md
        ├── REVIEW.md
        └── ARCHITECTURE.md
```

Mesmo quando a decisão pertence a uma change, mantenha o ADR centralizado em `docs/architecture/adr/` e registre `Related Change` e `Related Architecture`.

## Numeração e nome

Inspecione os ADRs existentes e sua convenção antes de criar o arquivo. No padrão `ADR-<NNN>-<slug>.md`, use o próximo número não utilizado, preserve padding e gere slug específico em kebab-case. Nunca reutilize número nem suponha que a listagem começou em `001`. Respeite outro padrão já estabelecido.

Antes de criar, procure a mesma decisão ou uma decisão relacionada. Se já existir ADR equivalente, informe-o em vez de duplicá-lo.

## Status

- `Proposed`: análise registrável, mas escolha ainda não confirmada.
- `Accepted`: decisão confirmada por fonte aceitável.
- `Rejected`: proposta explicitamente rejeitada e historicamente relevante.
- `Superseded`: decisão substituída por ADR posterior.
- `Deprecated`: decisão ainda histórica, mas descontinuada sem substituição direta.

Respeite a semântica local quando o projeto tiver outra convenção. Não use `Accepted` porque a opção foi recomendada.

## Imutabilidade e supersede

Um ADR aceito preserva o entendimento e os trade-offs da época. Não o reescreva substancialmente para fazer uma decisão posterior parecer original. Quando a decisão mudar:

1. crie novo ADR com novo número;
2. registre `Supersedes: ADR-<antigo>` no novo documento;
3. recomende atualizar o status ou relação do anterior para `Superseded by ADR-<novo>` quando apropriado e autorizado;
4. preserve ambos no histórico.

## Entradas SDD e conflitos

Consulte as fontes proporcionais à decisão antes de perguntar:

- baseline e change `SPEC.md` para requirements e constraints;
- `REVIEW.md` para findings ainda abertos;
- baseline e change `ARCHITECTURE.md` para contexto e `Architecture Decision Required`;
- ADRs para decisões existentes e relações.

Uma recomendação da `$architecture-designer` é insumo, não confirmação. Somente evidência explícita como `Decision Status: Confirmed` acompanhada de fonte confiável evita nova confirmação. Um finding indefinido ou contraditório não pode sustentar silenciosamente um ADR `Accepted`.

## Rastreabilidade

Registre quando aplicável:

```text
Related Requirements:
- NFR-004
- COMPAT-002

Related Change:
- docs/changes/batch-authorization/

Related Architecture:
- docs/changes/batch-authorization/ARCHITECTURE.md

Related Decisions:
- ADR-002

Decision Source:
- User confirmation | <fonte formal inequívoca>
```

Use somente relações reais. A seção `Decisão` diz o que foi escolhido; `Justificativa` explica por que essa escolha atende aos drivers confirmados.
