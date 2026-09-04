# Checklist de Revisão de Especificações

Use esta referência para estruturar uma revisão. Aplique cada verificação somente quando ela for relevante ao sistema e ao escopo da especificação.

## Modelo documental SDD

Na ausência de convenção conflitante em `AGENTS.md`, reconheça:

```text
docs/
├── spec/
│   └── SPEC.md
└── changes/
    └── <change-id>/
        ├── SPEC.md
        └── REVIEW.md
```

- `docs/spec/SPEC.md` é uma `BASELINE`: a source of truth documental do comportamento vigente.
- `docs/changes/<change-id>/SPEC.md` é uma `CHANGE`: a source of truth documental de uma evolução ou migração proposta ou em andamento.
- `docs/changes/<change-id>/REVIEW.md` é o local padrão para persistir a review da change spec quando o usuário solicitar um artefato.

Uma change spec na raiz ou sobrescrevendo `docs/spec/SPEC.md` pode exigir `INCORRECT_ARTIFACT_PLACEMENT`. Não mova arquivos sem solicitação.

## Independência e inspeção de evidências

Não confie automaticamente na spec, em `$spec-author`, na baseline, no código, nos testes ou em outra documentação. Inspecione somente o contexto proporcional ao escopo: `AGENTS.md`, baseline e changes relacionadas, ADRs, OpenAPI, protobuf, schemas, código, testes, configurações e documentação operacional.

Não imponha ordem absoluta de autoridade. Quando fontes relevantes divergirem, registre `EVIDENCE_CONFLICT` ou `BASELINE_CONFLICT` e indique o que precisa ser confirmado.

## Revisão por tipo e contexto

### Baseline

Verifique se `docs/spec/SPEC.md` representa o comportamento vigente: escopo, objetivos atuais, contratos públicos, requisitos, invariantes, segurança, confiabilidade, observabilidade, dependências e falhas. Gere finding se misturar propostas ativas, features futuras, backlog ou planos detalhados de implementação com o estado atual.

Em reconciliação explícita de mudança concluída, verifique se o estado final foi consolidado, detalhes transitórios foram removidos e a baseline não virou cópia da change spec.

### Greenfield

Revise problema, objetivos e não objetivos, escopo, requisitos, restrições, interfaces, dados, segurança, confiabilidade, observabilidade, critérios de aceitação, questões abertas e decisões arquiteturais necessárias. Não exija estado atual, compatibilidade, migração ou risco de regressão sem relevância real.

### Evolution

Uma change spec deve esclarecer `Current State → Proposed Change → Target State`: o que existe, o problema, o delta, o que deve permanecer, contratos compatíveis, riscos de regressão e critérios que comprovam o novo comportamento. Um estado futuro sem delta suficiente requer `MISSING_CURRENT_STATE` ou `INSUFFICIENT_CHANGE_CONTEXT`.

Com baseline `ESTABLISHED`, compare o estado atual e os invariantes da change spec com a baseline e com evidências relevantes. Não escolha silenciosamente qual fonte está correta.

Com baseline `ABSENT`, não reprove a change spec apenas pela ausência da baseline. Verifique se a ausência está explícita, se o estado atual foi reconstruído somente no escopo necessário, se as evidências sustentam as afirmações e se comportamento derivado do código não foi promovido automaticamente a intenção de negócio. Avalie premissas e questões abertas.

Com baseline `PARTIAL`, verifique o que ela cobre, quais inferências dependem de outras fontes e se essas inferências estão explícitas. Não exija reconstrução global.

### Migration

Avalie `Current State → Transition State → Target State` conforme o contexto. Considere coexistência, compatibilidade, migração de dados, backfill, dual-write/read, shadow traffic, reconciliação, cutover, rollback, descontinuação, remoção de legado e falha durante a migração sem exigir todos os mecanismos indiscriminadamente.

Para `MIG-*`, verifique sequência, condições de início e conclusão, falhas, rollback e consistência. Para `COMPAT-*`, verifique consumidores protegidos, comportamento e contrato preservados, período e condições de remoção.

### Atualização da baseline

Uma change spec ativa não deve atualizar silenciosamente a baseline. Se a baseline já apresentar como vigente uma feature ainda proposta ou em andamento, registre `PREMATURE_BASELINE_UPDATE`.

## Categorias de finding

Use uma destas categorias estáveis:

- `AMBIGUITY`: texto com mais de uma interpretação plausível.
- `MISSING_REQUIREMENT`: obrigação necessária ausente.
- `CONTRADICTION`: afirmações incompatíveis entre si.
- `UNTESTABLE_REQUIREMENT`: requisito sem forma objetiva de verificação.
- `UNMEASURABLE_NFR`: atributo de qualidade vago ou sem métrica definida.
- `MISSING_FAILURE_MODE`: falha relevante sem comportamento esperado.
- `MISSING_SECURITY_REQUIREMENT`: comportamento ou controle de segurança necessário ausente.
- `MISSING_OBSERVABILITY_REQUIREMENT`: sinais operacionais necessários ausentes.
- `MISSING_DEPENDENCY`: dependência necessária implícita ou não registrada.
- `MISSING_CONSTRAINT`: limite estabelecido ou necessário não documentado.
- `MISSING_ACCEPTANCE_CRITERIA`: requisito relevante sem critério ou outra verificação clara.
- `TRACEABILITY_GAP`: relação ausente ou incorreta entre requisito e critério.
- `ARCHITECTURE_LEAK`: decisão tecnológica desnecessária disfarçada de requisito.
- `OVER_SPECIFICATION`: detalhe de solução restringe desnecessariamente a implementação.
- `OPEN_QUESTION`: decisão ou informação ainda precisa ser confirmada.
- `MISSING_CURRENT_STATE`: estado atual essencial ausente.
- `MISSING_BEHAVIOR_TO_PRESERVE`: invariantes relevantes não identificados.
- `BASELINE_CONFLICT`: change spec e baseline descrevem estados incompatíveis.
- `EVIDENCE_CONFLICT`: fontes relevantes sustentam comportamentos diferentes.
- `PREMATURE_BASELINE_UPDATE`: baseline incorpora uma mudança ainda ativa.
- `MISSING_COMPATIBILITY_REQUIREMENT`: compatibilidade necessária não especificada.
- `MISSING_MIGRATION_REQUIREMENT`: obrigação crítica de transição ausente.
- `INSUFFICIENT_CHANGE_CONTEXT`: delta ou contexto da mudança insuficiente.
- `INCORRECT_ARTIFACT_PLACEMENT`: baseline, change spec ou review está no local semântico incorreto.

## Severidade

- `BLOCKER`: a spec não pode orientar corretamente a implementação sem a resolução. Use para contradição central, requisito essencial ausente, contrato principal indefinido ou premissa crítica não validada.
- `HIGH`: pode produzir uma implementação incorreta, incompatível ou insegura.
- `MEDIUM`: afeta qualidade, operabilidade ou manutenção, mas não impede necessariamente uma primeira implementação.
- `LOW`: melhora clareza, consistência ou documentação sem risco material imediato.

Não eleve a severidade apenas para destacar um finding. Considere impacto, probabilidade e capacidade de detectar ou reverter o erro.

## Qualidade dos requisitos

Para cada `FR-*`, `NFR-*`, `COMPAT-*` e `MIG-*`, verifique:

- obrigação clara, coerente e suficientemente atômica;
- comportamento objetivamente verificável e testável;
- ausência de contradições com outros requisitos;
- termos definidos e atores identificáveis;
- dependências e restrições explícitas;
- condições de contorno e casos negativos relevantes;
- comportamento de erro e resultado esperado;
- origem ou responsável quando isso for necessário para resolver conflitos;
- ausência de decisões arquiteturais que não sejam restrições estabelecidas.

Detecte tanto subespecificação, que transfere decisões importantes para a implementação, quanto superespecificação, que escolhe soluções sem necessidade.

## Requisitos não funcionais

Avalie, quando aplicável, latência, throughput, capacidade, disponibilidade, durabilidade, consistência, recuperação, escalabilidade, limites de recursos, segurança, observabilidade e manutenibilidade.

Termos como “rápido”, “robusto”, “seguro”, “altamente disponível”, “baixa latência”, “altamente escalável” ou “em larga escala” não são verificáveis sem critérios objetivos. Não invente números: registre `UNMEASURABLE_NFR` ou `OPEN_QUESTION` e indique quais métricas ou condições precisam ser definidas.

## Confiabilidade e modos de falha

Para sistemas distribuídos ou críticos, verifique conforme o contexto:

- timeouts e comportamento de retry;
- amplificação de retries e idempotência;
- processamento duplicado e falha parcial;
- dependência indisponível ou lenta;
- saturação de fila, backpressure e sobrecarga;
- load shedding e degradação controlada;
- recuperação e consistência de dados após falhas.

Não exija todos os itens para toda aplicação. Registre somente lacunas plausíveis e relevantes.

## Segurança

Verifique, quando aplicável:

- autenticação e autorização, incluindo sujeito, recurso e ação;
- isolamento entre tenants e fronteiras de privilégio;
- dados sensíveis e secrets;
- auditabilidade e casos de abuso;
- validação de entradas;
- semântica fail-open ou fail-closed.

Identifique lacunas da especificação sem transformar a revisão em um threat model completo.

## Observabilidade

Verifique se a spec torna o sistema operável por meio de sinais relevantes, como métricas, logs, traces, eventos de auditoria, visibilidade de falhas, sinais de capacidade, sinais relacionados a SLOs e possibilidade de alertas. Não prescreva Datadog, Prometheus, OpenTelemetry ou outra ferramenta salvo quando ela já for uma restrição.

## Critérios de aceitação e rastreabilidade

Confirme que:

1. Cada requisito relevante possui critérios de aceitação ou outra forma clara de verificação.
2. Cada critério testa de fato o requisito ao qual está vinculado.
3. Caminhos de erro e casos negativos relevantes aparecem além do happy path.
4. Os resultados esperados são objetivos.
5. A relação entre `FR-003` e IDs como `AC-003-01` segue a convenção da spec e é semanticamente correta.
6. Requisitos `COMPAT-*` e `MIG-*` possuem critérios verificáveis quando aplicáveis.

Procure também contradições entre objetivos e não objetivos, `FR` e `FR`, `FR` e `NFR`, requisito e critério de aceitação, requisito e restrição, premissa e requisito, rollout e compatibilidade, ou segurança e disponibilidade.

## Vazamento de arquitetura

Pergunte se a tecnologia citada é realmente uma restrição estabelecida ou apenas uma possível solução. Por exemplo, “eventos devem ser enviados pelo Kafka” pode esconder a necessidade “a entrega de eventos deve ser assíncrona e durável”. Registre `ARCHITECTURE_LEAK` e recomende um ADR quando a decisão precisar de avaliação separada; não remova a decisão automaticamente.

## Formato de cada finding

```markdown
### SR-001

**Severidade:** HIGH  
**Categoria:** AMBIGUITY  
**Localização:** FR-004

**Finding:**  
“O sistema deve processar solicitações rapidamente” não é mensurável.

**Por que importa:**  
Implementações diferentes podem adotar expectativas incompatíveis de latência.

**Resolução sugerida:**  
Definir o percentil alvo, o objetivo de latência e a condição de carga.

**Exemplo:**  
`NFR-003: A latência de processamento deve permanecer abaixo de X ms no P95 sob Y RPS sustentadas.`

**Status:** Open
```

Não invente valores para `X` ou `Y`. Quando eles não estiverem disponíveis, proponha uma `OPEN-QUESTION`.

## Classificação de prontidão

- `NOT_READY`: existem blockers ou múltiplas lacunas fundamentais.
- `NEEDS_REVISION`: não há blockers, mas existem findings `HIGH` que devem ser corrigidos antes da implementação.
- `IMPLEMENTATION_READY_WITH_RISKS`: a spec é implementável, mas mantém riscos ou questões abertas não bloqueantes claramente registrados.
- `IMPLEMENTATION_READY`: a spec está suficientemente clara e verificável para avançar para arquitetura, planejamento ou implementação.

Não use percentuais arbitrários. Baseie o veredito nos findings e explique a relação entre eles.

### Prontidão contextual

- `GREENFIELD` pode ser `IMPLEMENTATION_READY` sem estado atual, compatibilidade ou migração quando essas seções não forem relevantes.
- `EVOLUTION` não deve ser `IMPLEMENTATION_READY` quando o estado atual essencial, o delta, o comportamento a preservar ou a compatibilidade crítica estiverem indefinidos.
- `MIGRATION` não deve ser `IMPLEMENTATION_READY` quando elementos de transição necessários, como estado alvo, coexistência, cutover, rollback ou consistência, estiverem indefinidos.

## Estrutura da revisão

```markdown
# Revisão da Especificação

## Metadata

- **Tipo da specification:** BASELINE | CHANGE
- **Contexto de desenvolvimento:** GREENFIELD | EVOLUTION | MIGRATION
- **Status da baseline:** ESTABLISHED | PARTIAL | ABSENT <quando aplicável>

## Veredito

<status>

## Resumo Executivo

<avaliação breve da qualidade geral>

## Resumo dos Findings

| Severidade | Quantidade |
| --- | ---: |
| BLOCKER | ... |
| HIGH | ... |
| MEDIUM | ... |
| LOW | ... |

## Findings

### SR-001

<finding no formato definido acima>

## Cobertura dos Requisitos

<mapeamento conciso dos requisitos e problemas>

## Cobertura dos Critérios de Aceitação

<lacunas relevantes>

## Consistência com a Baseline

<comparação e divergências relevantes, quando aplicável>

## Questões Abertas

<decisões ou confirmações necessárias>

## Próximas Ações Recomendadas

<lista priorizada de correções>
```

Omita seções que não se aplicam; não crie conteúdo artificial para preencher o formato.
