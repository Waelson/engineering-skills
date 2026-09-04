---
name: spec-author
description: Crie ou atualize especificações de software prontas para implementação usando Spec-Driven Development, incluindo baselines, mudanças evolutivas e migrações sob docs/. Use quando solicitarem uma specification, a formalização de uma funcionalidade ou de requisitos, a preparação de trabalho antes da implementação, critérios de aceitação ou a reconciliação explícita da baseline. Não use para depuração, implementação, revisão de código ou planejamento de arquitetura.
---

# Autor de Especificações

Transforme um problema, necessidade, funcionalidade ou mudança de software em uma especificação que possa orientar uma tarefa posterior de implementação. Produza ou atualize somente artefatos de specification sob `docs/`; não implemente software nem crie arquitetura, ADRs, planos de implementação ou reviews.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e inspecione a estrutura de `docs/`, a documentação relacionada e o contexto relevante do repositório.
2. Leia integralmente [references/artifact-convention.md](references/artifact-convention.md). Classifique, sem perguntar quando as evidências forem suficientes, o contexto (`GREENFIELD`, `EVOLUTION` ou `MIGRATION`), o status da baseline (`ESTABLISHED`, `PARTIAL` ou `ABSENT`) e a operação (`CREATE_BASELINE`, `CREATE_CHANGE_SPEC`, `UPDATE_CHANGE_SPEC` ou `RECONSTRUCT_BASELINE`).
3. Selecione exatamente um artefato de specification conforme a convenção. Respeite uma convenção conflitante documentada em `AGENTS.md`; caso contrário, nunca crie `SPEC.md` na raiz.
4. Inspecione apenas o contexto necessário. Em brownfield, estabeleça o estado atual a partir da baseline e de evidências do projeto; não trate automaticamente o código como intenção correta de negócio.
5. Identifique o estado atual, a mudança proposta e o comportamento existente a preservar quando aplicável. Separe fatos, requisitos, restrições, premissas e questões abertas.
6. Defina problema, objetivos, não objetivos, escopo e requisitos. Use `FR-*` e `NFR-*`; use `MIG-*` e `COMPAT-*` quando trouxerem rastreabilidade útil para migração ou compatibilidade.
7. Avalie interfaces, dados, dependências, modos de falha, segurança, observabilidade, riscos de regressão, compatibilidade e transição somente quando relevantes.
8. Escreva critérios de aceitação mensuráveis vinculados aos requisitos, usando IDs como `AC-003-01`. Prefira Dado/Quando/Então quando tornar o comportamento mais claro.
9. Preserve IDs e histórico lógico ao atualizar uma change spec. Registre informações importantes não resolvidas como `ASSUMPTION-*` ou `OPEN-QUESTION-*` sem bloquear desnecessariamente a primeira versão.
10. Revise o resultado em busca de contradições, linguagem vaga, escolhas arquiteturais ocultas, critérios não testáveis, falta de rastreabilidade e path incorreto.

## Limites

- Escreva a especificação no idioma do usuário, a menos que ele solicite outro idioma ou que o repositório estabeleça um idioma diferente para a documentação. Uma escolha explícita do usuário prevalece sobre a convenção do repositório. Mantenha identificadores estruturais como `FR-001`, `NFR-001`, `AC-001-01`, `ASSUMPTION-001` e `OPEN-QUESTION-001` inalterados em todos os idiomas.
- Não invente metas de desempenho, escala, disponibilidade ou latência. Registre a métrica ausente como `OPEN-QUESTION-NNN` ou `ASSUMPTION-NNN`.
- Especifique o comportamento necessário sem selecionar desnecessariamente uma arquitetura irreversível. Se uma decisão como broker, banco de dados ou protocolo ainda não estiver definida por uma restrição, adicione-a em **Decisões Arquiteturais Necessárias** e recomende um ADR separado.
- Diferencie o que é conhecido do que está sendo proposto. Cite evidências do repositório com caminhos de arquivos quando elas sustentarem materialmente a especificação.
- Adapte o documento à mudança: omita seções irrelevantes, mas não omita riscos relevantes ou informações operacionais apenas para encurtar a especificação.
- Não reconstrua uma baseline completa apenas porque ela não existe ou é parcial. Não incorpore uma change spec ativa à baseline sem intenção explícita do usuário.
- Não duplique a mesma specification em paths diferentes.

Antes de escrever, leia [references/spec-template.md](references/spec-template.md) para selecionar as seções adaptativas. Consulte [references/artifact-scenarios.md](references/artifact-scenarios.md) quando precisar confirmar o roteamento esperado pelos cenários de teste.
