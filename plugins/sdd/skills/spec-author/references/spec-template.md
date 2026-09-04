# Template de Especificação de Software

Use este template como ponto de partida, não como uma checklist obrigatória. Omita seções que não se aplicam e adicione seções específicas do domínio quando elas melhorarem a capacidade de implementação. Preserve explicitamente as informações desconhecidas em vez de inventar fatos.

Escreva os títulos e o conteúdo no idioma do usuário, a menos que ele solicite outro idioma ou que o repositório tenha um idioma estabelecido para a documentação. Uma escolha explícita do usuário prevalece sobre a convenção do repositório. Não traduza nem localize identificadores estruturais como `FR-001`, `NFR-001`, `AC-001-01`, `ASSUMPTION-001` e `OPEN-QUESTION-001`.

# Especificação: <título>

## Metadados

- **Status:** Rascunho | Em revisão | Aprovada
- **Autores / Responsáveis:** <nomes ou papéis>
- **Partes interessadas:** <nomes ou papéis>
- **Criada em:** <data>
- **Última atualização:** <data>
- **Artefatos relacionados:** <issues, documentos, ADRs, designs>

## Contexto

Descreva o sistema atual, o contexto do usuário ou do negócio, as evidências relevantes do repositório e o evento que motiva este trabalho.

## Definição do Problema

Declare o problema e seu impacto sem prescrever uma implementação.

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

## Requisitos Funcionais

- FR-001: <comportamento observável, ator, condições e resultado>
- FR-002: <comportamento observável, ator, condições e resultado>

Cada requisito deve ser claro, verificável, testável e suficientemente preciso para implementação. Evite incorporar uma solução, a menos que ela seja uma restrição estabelecida.

## Requisitos Não Funcionais

- NFR-001: <requisito mensurável de qualidade, segurança, confiabilidade, conformidade ou desempenho>

Não escreva requisitos vagos como “deve ser rápido” nem invente limites. Se uma meta for desconhecida, registre-a em **Questões Abertas** ou **Premissas**.

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
