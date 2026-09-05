# Processo e Convenção de Arquitetura

## Entradas e sequência SDD

Trabalhe preferencialmente a partir de uma specification existente e considere reviews persistidas como insumo importante:

```text
spec-author → SPEC.md → spec-reviewer → architecture-designer → ARCHITECTURE.md → adr-author → implementation-planner
```

`architecture-designer` não assume os papéis das outras etapas. Uma lacuna de requisito que bloqueie arquitetura retorna ao author/reviewer; uma decisão arquitetural relevante pode recomendar ADR posterior.

## Preflight da specification

Não execute review completa. Verifique se decisões arquiteturais responsáveis possuem base suficiente, especialmente consistência, failure semantics, compatibilidade, capacidade essencial e segurança. Considere findings de `REVIEW.md`:

- blocker relevante impede a decisão associada;
- finding `HIGH` pode bloquear ou exigir esclarecimento conforme impacto;
- incerteza não crítica pode virar `ARCH-ASSUMPTION-*` ou `ARCH-QUESTION-*`.

Não escolha silenciosamente um consistency model quando a review disser que ele está indefinido.

## Readiness arquitetural

- `ARCHITECTURE_DISCOVERY_REQUIRED`: falta informação crítica. Registre bloqueio, impacto, localização e pergunta necessária; recomende `$spec-author` ou `$spec-reviewer` quando a lacuna pertencer aos requisitos.
- `READY_FOR_ARCHITECTURE_DRAFT`: é possível criar proposta preliminar com assumptions e questões explícitas.
- `ARCHITECTURE_READY`: design suficientemente definido para ADRs e planejamento posterior.

## Convenção documental

```text
docs/
├── spec/
│   └── SPEC.md
├── architecture/
│   ├── ARCHITECTURE.md
│   └── adr/
└── changes/
    └── <change-id>/
        ├── SPEC.md
        ├── REVIEW.md
        └── ARCHITECTURE.md
```

- `docs/architecture/ARCHITECTURE.md` representa a arquitetura baseline vigente.
- `docs/changes/<change-id>/ARCHITECTURE.md` representa a arquitetura proposta para a mudança.

Uma change architecture não altera automaticamente a baseline. Respeite convenção conflitante documentada em `AGENTS.md`.

## Roteamento e atualização

### Baseline

Use `docs/architecture/ARCHITECTURE.md` para greenfield, reconstrução arquitetural explícita ou visão estrutural vigente. Se o arquivo existir, atualize-o sem criar duplicata.

### Change

Use `docs/changes/<change-id>/ARCHITECTURE.md` para feature, evolution ou migration. Limite o design ao delta necessário. Se o arquivo existir, atualize-o preservando decisões válidas, rastreabilidade, assumptions e questões.

## Greenfield

Derive a arquitetura da baseline spec. Defina boundaries, componentes, dados, comunicação, segurança, observabilidade, escala, failure domains, deployment e trade-offs relevantes. Prefira a solução mais simples que satisfaça os requisitos; não introduza distribuição por antecipação.

## Evolution

Leia a arquitetura baseline e ADRs relevantes quando existirem, depois confirme evidências necessárias. Expresse `Current Architecture → Required Delta → Target Architecture`. Preserve constraints e comportamento aplicáveis e não redesenhe componentes não relacionados.

Se `docs/architecture/ARCHITECTURE.md` estiver ausente, isso não bloqueia automaticamente. Reconstrua somente o contexto necessário a partir de código, deployments, APIs, ADRs, schemas, configurações, testes e documentação. Inclua **Evidências da Arquitetura Atual** quando útil.

## Migration

Expresse `Current Architecture → Transition Architecture → Target Architecture`. Avalie conforme o caso coexistência, dual-write/read, shadowing, dados, sincronização, reconciliação, cutover, rollback, compatibilidade, observabilidade de transição e recuperação. Não exija mecanismos irrelevantes.

## Estrutura adaptativa de ARCHITECTURE.md

```markdown
# Arquitetura: <título>

## Metadata
## Contexto
## Objetivos Arquiteturais
## Restrições
## Arquitetura Atual
## Evidências da Arquitetura Atual
## Arquitetura Proposta
## Decisões Confirmadas
## Decisões Pendentes
## Responsabilidades dos Componentes
## Ownership de Dados
## Modelo de Comunicação
## Fluxo de Dados
## Modelo de Consistência
## Confiabilidade
## Modos de Falha
## Escalabilidade e Capacidade
## Segurança
## Observabilidade
## Compatibilidade
## Arquitetura de Migração / Transição
## Trade-offs
## Alternativas Consideradas
## Decisões Arquiteturais Necessárias
## Assumptions Arquiteturais
## Questões Arquiteturais Abertas
```

Omita seções irrelevantes.

Não misture decisões confirmadas, propostas, assumptions e questões abertas. Uma recomendação dependente de confirmação permanece `Proposed`, nunca `Accepted`.

Metadata baseline:

```text
Architecture Type: BASELINE
Development Context: GREENFIELD
Related Specification: docs/spec/SPEC.md
Status: Draft
```

Metadata change:

```text
Architecture Type: CHANGE
Development Context: EVOLUTION | MIGRATION
Related Specification: docs/changes/<change-id>/SPEC.md
Status: Draft
```
