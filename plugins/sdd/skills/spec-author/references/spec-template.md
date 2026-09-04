# Template de Especificação de Software

Use este template como um conjunto adaptativo de seções, não como uma checklist obrigatória. Primeiro determine o artefato conforme [artifact-convention.md](artifact-convention.md). Omita seções que não se aplicam e adicione seções específicas do domínio quando elas melhorarem a capacidade de implementação. Preserve explicitamente as informações desconhecidas em vez de inventar fatos.

Escreva os títulos e o conteúdo no idioma do usuário, a menos que ele solicite outro idioma ou que o repositório tenha um idioma estabelecido para a documentação. Uma escolha explícita do usuário prevalece sobre a convenção do repositório. Não traduza nem localize identificadores estruturais como `FR-001`, `NFR-001`, `AC-001-01`, `ASSUMPTION-001` e `OPEN-QUESTION-001`.

# Especificação: <título>

## Metadados

- **Status:** Rascunho | Em revisão | Aprovada
- **Autores / Responsáveis:** <nomes ou papéis>
- **Partes interessadas:** <nomes ou papéis>
- **Criada em:** <data>
- **Última atualização:** <data>
- **Artefatos relacionados:** <issues, documentos, ADRs, designs>
- **Tipo da specification:** BASELINE | CHANGE
- **Contexto de desenvolvimento:** GREENFIELD | EVOLUTION | MIGRATION
- **Status da baseline:** ESTABLISHED | PARTIAL | ABSENT <somente para change specs>
- **Status do discovery:** READY_FOR_DRAFT | READY_FOR_SPEC <quando útil>

## Contexto

Descreva o sistema atual, o contexto do usuário ou do negócio, as evidências relevantes do repositório e o evento que motiva este trabalho.

## Estado Atual

Use em evolution ou migration para descrever somente o comportamento vigente relevante à mudança. Quando a baseline estiver ausente ou parcial, declare que esse estado foi reconstruído de evidências da implementação e não representa automaticamente intenção de negócio confirmada.

## Evidências do Estado Atual

- `<path para baseline, ADR, contrato público, teste, implementação, configuração ou documentação>`

Inclua quando a proveniência do estado atual for importante, especialmente em brownfield sem baseline.

## Definição do Problema

Declare o problema e seu impacto sem prescrever uma implementação.

## Mudança Proposta

Use em change specs para descrever o delta pretendido sem confundi-lo com o estado vigente.

## Estado Alvo

Use em evolution ou migration quando explicitar o resultado final reduzir ambiguidades.

## Estado de Transição

Use em migrations quando o período intermediário tiver comportamento, riscos ou obrigações próprios.

## Objetivos

- G-001: <resultado desejado>

## Não Objetivos

- NG-001: <resultado explicitamente excluído>

## Escopo

Defina o que está dentro e fora do escopo, incluindo atores, sistemas e workflows afetados.

## Definições

| Termo | Definição |
| --- | --- |
| <termo> | <significado inequívoco nesta especificação> |

## Premissas

- ASSUMPTION-001: <premissa não confirmada usada nesta versão>

Não expresse uma premissa como um requisito confirmado. Quando for útil, declare a consequência caso a premissa se mostre falsa.

## Restrições

- CONSTRAINT-001: <limite técnico, de negócio, jurídico ou operacional estabelecido>

## Comportamento Existente a Preservar

- <contrato, semântica, garantia ou expectativa relevante à mudança>

Use em evolution ou migration; não documente o sistema inteiro.

## Requisitos Funcionais

- FR-001: <comportamento observável, ator, condições e resultado>
- FR-002: <comportamento observável, ator, condições e resultado>

Cada requisito deve ser claro, verificável, testável e suficientemente preciso para implementação. Evite incorporar uma solução, a menos que ela seja uma restrição estabelecida.

## Requisitos Não Funcionais

- NFR-001: <requisito mensurável de qualidade, segurança, confiabilidade, conformidade ou desempenho>

Não escreva requisitos vagos como “deve ser rápido” nem invente limites. Se uma meta for desconhecida, registre-a em **Questões Abertas** ou **Premissas**.

## Requisitos de Migração

- MIG-001: <obrigação verificável da transformação>

Use somente em migrations quando IDs específicos melhorarem a rastreabilidade.

## Requisitos de Compatibilidade

- COMPAT-001: <comportamento ou consumidor que deve permanecer compatível>

Use em evolution ou migration quando necessário; não crie requisitos de compatibilidade artificiais em greenfield.

## Requisitos de API / Interface

Especifique contratos observáveis externamente, entradas, saídas, erros, expectativas de compatibilidade e comportamento de versionamento sem selecionar prematuramente a arquitetura interna.

## Requisitos de Dados

Descreva as entradas e saídas de dados e as necessidades aplicáveis de propriedade, validação, retenção, classificação, privacidade, integridade e ciclo de vida.

## Segurança

Descreva fronteiras de confiança relevantes, comportamentos de autenticação e autorização, dados sensíveis, casos de abuso, necessidades de auditoria e controles necessários.

## Confiabilidade e Modos de Falha

| Modo de falha | Comportamento esperado | Recuperação / mitigação | Requisito relacionado |
| --- | --- | --- | --- |
| <falha> | <comportamento observável> | <expectativa de recuperação> | <ID de FR/NFR> |

## Observabilidade

Especifique os sinais necessários para verificar a operação e diagnosticar falhas, como logs, métricas, traces, eventos de auditoria, dashboards ou alertas. Não invente limites numéricos.

## Dependências

- DEP-001: <equipe, serviço, decisão, contrato ou pré-requisito externo>

## Compatibilidade

Descreva a compatibilidade retroativa ou futura, os clientes ou as versões compatíveis e o comportamento de descontinuação, quando aplicável.

## Migração / Implantação Gradual

Descreva os requisitos de migração, implantação gradual, sinalizadores de funcionalidade, preenchimento retroativo de dados, reversibilidade, reversão e comunicação, quando aplicável.

### Migração de Dados

### Coexistência

### Reconciliação

### Critérios de Cutover

### Requisitos de Rollback

### Descontinuação

Use apenas os subtópicos relevantes à migration.

## Riscos de Regressão

- <comportamento vigente que pode ser degradado pela mudança e como verificá-lo>

## Critérios de Aceitação

Vincule cada critério a um ou mais requisitos e torne o resultado esperado objetivamente verificável.

### FR-003 — Identificadores de ferramentas duplicados

- AC-003-01:
  - Dado um identificador de ferramenta existente,
  - quando outro registro tentar usar o mesmo identificador,
  - então o registro será rejeitado.
- AC-003-02: A rejeição expõe o erro padronizado de conflito definido pelo contrato da API.

## Questões Abertas

- OPEN-QUESTION-001: <questão importante não resolvida, responsável se conhecido e impacto>

Classifique uma questão como bloqueante somente quando não for possível produzir uma especificação coerente sem a resposta. Mantenha as questões importantes não bloqueantes visíveis na primeira versão; detalhes opcionais não precisam atrasá-la.

## Decisões Arquiteturais Necessárias

- ADR-NEEDED-001: <decisão que deve ser tratada separadamente, opções disponíveis e por que ela importa>

Use esta seção quando o requisito for conhecido, mas o mecanismo arquitetural não. Por exemplo, “processar eventos de forma assíncrona” não implica o uso de Kafka, a menos que Kafka já seja uma restrição ou decisão estabelecida.

## Seleção adaptativa de seções

### Baseline / Greenfield

Normalmente use Contexto, Definição do Problema, Objetivos, Não Objetivos, Escopo, Requisitos, Segurança, Confiabilidade, Observabilidade, Critérios de Aceitação e Questões Abertas. Não adicione estado atual, migração ou compatibilidade sem necessidade real.

### Evolution

Acrescente quando aplicável Estado Atual, Evidências do Estado Atual, Mudança Proposta, Estado Alvo, Comportamento Existente a Preservar, Requisitos de Compatibilidade e Riscos de Regressão.

### Migration

Acrescente quando aplicável Estado Atual, Estado de Transição, Estado Alvo, Requisitos de Migração e Compatibilidade, Migração de Dados, Coexistência, Reconciliação, Cutover, Rollback, Descontinuação e Riscos de Regressão.
