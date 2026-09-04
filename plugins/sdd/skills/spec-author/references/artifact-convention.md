# Convenção de Artefatos SDD

## Diretórios e responsabilidades

Use por padrão:

```text
project-root/
├── AGENTS.md
├── README.md
└── docs/
    ├── spec/
    │   └── SPEC.md
    ├── changes/
    │   └── <change-id>/
    │       └── SPEC.md
    └── architecture/
        ├── ARCHITECTURE.md
        └── adr/
```

`spec-author` escreve somente specifications. Não crie `ARCHITECTURE.md`, ADRs, planos de implementação ou reviews. Uma convenção conflitante explicitamente documentada em `AGENTS.md` prevalece; sem ela, todos os artefatos gerados ficam sob `docs/` e nenhum `SPEC.md` é criado na raiz.

## Semântica de source of truth

- `docs/spec/SPEC.md` é a source of truth documental da baseline vigente: **o que o sistema faz atualmente**.
- `docs/changes/<change-id>/SPEC.md` é a source of truth documental de uma mudança proposta, em discovery, implementação ou migração: **o que estamos mudando**.

Código, testes, contratos e configuração podem comprovar o estado atual, sobretudo quando a baseline está ausente ou parcial. Eles não comprovam automaticamente a intenção correta do negócio. Registre divergências e incertezas como premissas ou questões abertas.

## Classificação

Infira as classificações quando o pedido e o repositório forem suficientes; não pergunte ao usuário para confirmar rótulos evidentes.

### Contexto de desenvolvimento

- `GREENFIELD`: sistema ou componente novo, ainda sem implementação relevante.
- `EVOLUTION`: mudança funcional ou não funcional em um sistema existente.
- `MIGRATION`: transformação de tecnologia, dados, contratos ou operação de um sistema existente.

### Status da baseline

- `ESTABLISHED`: `docs/spec/SPEC.md` existe e cobre adequadamente a área relevante.
- `PARTIAL`: a baseline existe, mas é incompleta ou não cobre a área alterada.
- `ABSENT`: não existe baseline.

## Operações e roteamento

### CREATE_BASELINE

Use normalmente para `GREENFIELD`. Crie `docs/spec/SPEC.md`, descrevendo o sistema ou componente base. Não adicione estado atual, migração ou compatibilidade artificialmente.

### CREATE_CHANGE_SPEC

Use para `EVOLUTION` ou `MIGRATION`. Crie `docs/changes/<change-id>/SPEC.md`, descrevendo o delta entre estado atual e estado desejado. A baseline permanece inalterada.

### UPDATE_CHANGE_SPEC

Use quando o arquivo `docs/changes/<change-id>/SPEC.md` já existir e novas informações forem descobertas. Atualize o mesmo arquivo; preserve IDs quando possível, rastreabilidade, premissas, questões abertas e o histórico lógico. Não crie cópia paralela.

### RECONSTRUCT_BASELINE

Use em sistema existente somente quando o usuário solicitar explicitamente estabelecer, reconstruir, reconciliar ou atualizar a baseline. Escreva `docs/spec/SPEC.md` com base em evidências verificadas.

Para reconstrução sem baseline, considere código, testes, APIs, schemas, ADRs, documentação, configurações e change specs. Para reconciliar uma mudança concluída, combine a baseline existente, a change spec concluída e a implementação ou o contexto verificado. A baseline final deve representar o estado vigente consolidado, não uma concatenação da change spec.

## Regras por cenário

### Greenfield

Sem baseline relevante, execute `CREATE_BASELINE` em `docs/spec/SPEC.md`. Foque no sistema base sem criar `docs/changes/`.

### Evolução com baseline estabelecida

Leia a baseline, confirme o estado atual necessário e execute `CREATE_CHANGE_SPEC`. Expresse `Current State → Proposed Change → Target State`. Não altere a baseline enquanto a mudança ainda for proposta ou estiver em andamento.

### Evolução sem baseline

Classifique `Development Context: EVOLUTION` e `Baseline Status: ABSENT`. Não invente nem reconstrua toda a baseline e não bloqueie uma mudança pequena. Inspecione somente o necessário e crie `docs/changes/<change-id>/SPEC.md`.

Declare na seção de estado atual que não existe baseline e que o comportamento foi reconstruído da implementação e dos artefatos de suporte no escopo da mudança. Inclua **Evidências do Estado Atual** quando útil, citando paths de código, testes, APIs, schemas, ADRs, migrações, configurações ou documentação. Trate dúvidas como `ASSUMPTION-*` ou `OPEN-QUESTION-*`.

### Evolução com baseline parcial

Use a baseline onde aplicável e complete o entendimento com evidências relevantes. Não expanda automaticamente toda a baseline. Crie a change spec normalmente se houver evidência suficiente.

### Migração

Trate como change spec em `docs/changes/<change-id>/SPEC.md`; não crie `MIGRATION.md`. Descreva estados atual, de transição e alvo quando aplicáveis, além de compatibilidade, migração de dados, coexistência, reconciliação, cutover, rollback e descontinuação conforme o contexto.

### Reconciliação após conclusão

Não atualize a baseline automaticamente quando uma change spec for criada ou alterada. Atualize `docs/spec/SPEC.md` somente mediante intenção explícita de incorporar uma mudança concluída ao estado documentado do sistema.

## Change ID

Crie um identificador curto, específico e estável em kebab-case, como `batch-authorization`, `migrate-policy-storage`, `oauth-rate-limit` ou `cache-invalidation`. Evite `new-feature`, `change-1`, `update` e `misc`. Preserve convenções locais de tickets, como `psc-3492-cache-invalidation`.

## Metadata concisa

Baseline greenfield:

```text
Specification Type: BASELINE
Development Context: GREENFIELD
Status: Draft
```

Change spec:

```text
Specification Type: CHANGE
Development Context: EVOLUTION
Baseline Status: ESTABLISHED | PARTIAL | ABSENT
Status: Draft
```

Migration:

```text
Specification Type: CHANGE
Development Context: MIGRATION
Baseline Status: ESTABLISHED | PARTIAL | ABSENT
Status: Draft
```

Mantenha a metadata simples e use o valor real inferido.

## Comportamento existente a preservar

Em `EVOLUTION` e `MIGRATION`, registre **Comportamento Existente a Preservar** quando aplicável. Limite-se a invariantes relevantes à mudança: contratos de API, semântica de erros e autorização, auditoria, garantias de dados e compatibilidade, fallback, SLOs existentes e expectativas de consumidores.

Não documente o sistema inteiro. Use `COMPAT-*` para requisitos de compatibilidade quando eles melhorarem a rastreabilidade.
