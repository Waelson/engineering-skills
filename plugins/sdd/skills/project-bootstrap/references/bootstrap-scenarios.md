# Cenários de Bootstrap SDD

Use estes cenários como testes normativos.

## 1. Greenfield vazio

Existe apenas `README.md`.

- Esperado: criar `AGENTS.md` e preparar `docs/spec/`, `docs/changes/` e `docs/architecture/adr/`.
- Invariante: não criar `SPEC.md` nem `ARCHITECTURE.md`.

## 2. Brownfield Go

Existem `go.mod`, `README.md`, `Makefile` e código.

- Esperado: detectar Go, registrar somente comandos realmente definidos pelo projeto, criar ou atualizar `AGENTS.md` e preparar a documentação.

## 3. AGENTS.md existente

- Esperado: preservar conteúdo e adicionar apenas orientações novas, estáveis e compatíveis; não sobrescrever pelo template.

## 4. Convenção conflitante

O projeto usa `design/adr/`.

- Readiness: `BOOTSTRAP_DISCOVERY_REQUIRED` para o path conflitante.
- Esperado: não mover nem duplicar; perguntar se deve preservar, adotar ou mapear.

## 5. Parcialmente preparado

Já existem `docs/spec/` e `docs/changes/`.

- Contexto: `PARTIALLY_BOOTSTRAPPED`.
- Esperado: criar somente o que faltar.

## 6. Stack desconhecida

O repositório está quase vazio.

- Esperado: não inventar linguagem, framework ou comandos; o bootstrap documental pode prosseguir.

## 7. Comando de teste detectado

O `Makefile` define `make test`.

- Esperado: registrar `make test` e não acrescentar comandos presumidos.

## 8. Brownfield sem SPEC

Há projeto existente, mas não `docs/spec/SPEC.md`.

- Esperado: bootstrap válido e possível `SDD_READY`; não criar baseline automaticamente.

## Asserções transversais

- `$project-bootstrap` precede `$spec-author`;
- somente instruções estáveis entram em `AGENTS.md`;
- nenhuma specification, review, arquitetura, ADR, plano, teste ou código é criado;
- stack, comandos e convenções não são inventados;
- conflitos materiais geram interação antes de mudança;
- diretórios são preparados sem artefatos vazios de outras fases;
- brownfield sem baseline pode chegar a `SDD_READY`.
