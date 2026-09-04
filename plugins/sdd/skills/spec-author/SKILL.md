---
name: spec-author
description: Crie ou atualize especificações de software prontas para implementação usando Spec-Driven Development. Use quando solicitarem a criação de uma especificação ou SPEC.md, a formalização de uma funcionalidade ou de requisitos, a preparação de um trabalho antes da implementação, a definição de requisitos funcionais ou não funcionais ou a escrita de critérios de aceitação. Não use para depuração, implementação direta, revisão de código isolada ou uma pequena alteração de código que já esteja suficientemente especificada.
---

# Autor de Especificações

Transforme um problema, necessidade, funcionalidade ou mudança de software em uma especificação que possa orientar uma tarefa posterior de implementação. Produza ou atualize o arquivo `SPEC.md`; não implemente o software.

## Fluxo de trabalho

1. Leia todos os arquivos `AGENTS.md` aplicáveis e, em seguida, inspecione o repositório e a documentação relacionada à funcionalidade. Preserve a terminologia, as restrições e as decisões estabelecidas.
2. Entenda o problema e identifique as partes interessadas e o contexto disponíveis. Faça somente perguntas que impeçam a criação de uma primeira versão coerente; classifique as demais informações desconhecidas como questões abertas importantes ou detalhes opcionais.
3. Separe as evidências em fatos, requisitos, restrições, premissas e questões abertas. Nunca transforme silenciosamente uma premissa em um requisito confirmado.
4. Defina o problema, os objetivos, os não objetivos e o escopo antes de detalhar o comportamento.
5. Escreva os requisitos funcionais como `FR-001`, `FR-002` e assim por diante. Escreva os requisitos não funcionais como `NFR-001`, `NFR-002` e assim por diante. Cada requisito deve ser claro, verificável, testável e suficientemente preciso para uma implementação posterior.
6. Aborde interfaces e dados quando forem relevantes e, depois, avalie restrições, dependências, modos de falha, segurança, observabilidade, compatibilidade e implantação gradual ou migração.
7. Escreva critérios de aceitação mensuráveis vinculados aos IDs dos requisitos, usando identificadores como `AC-003-01`. Prefira Dado/Quando/Então quando esse formato tornar o comportamento mais claro.
8. Registre informações importantes não resolvidas como premissas ou questões abertas numeradas. Produza uma primeira versão útil em vez de buscar respostas exaustivas quando as informações ausentes não forem bloqueantes.
9. Revise o resultado em busca de contradições, linguagem vaga, escolhas arquiteturais ocultas, critérios não testáveis e falta de rastreabilidade.

## Limites

- Escreva a especificação no idioma do usuário, a menos que ele solicite outro idioma ou que o repositório estabeleça um idioma diferente para a documentação. Uma escolha explícita do usuário prevalece sobre a convenção do repositório. Mantenha identificadores estruturais como `FR-001`, `NFR-001`, `AC-001-01`, `ASSUMPTION-001` e `OPEN-QUESTION-001` inalterados em todos os idiomas.
- Não invente metas de desempenho, escala, disponibilidade ou latência. Registre a métrica ausente como `OPEN-QUESTION-NNN` ou `ASSUMPTION-NNN`.
- Especifique o comportamento necessário sem selecionar desnecessariamente uma arquitetura irreversível. Se uma decisão como broker, banco de dados ou protocolo ainda não estiver definida por uma restrição, adicione-a em **Decisões Arquiteturais Necessárias** e recomende um ADR separado.
- Diferencie o que é conhecido do que está sendo proposto. Cite evidências do repositório com caminhos de arquivos quando elas sustentarem materialmente a especificação.
- Adapte o documento à mudança: omita seções irrelevantes, mas não omita riscos relevantes ou informações operacionais apenas para encurtar a especificação.

Antes de criar ou atualizar uma especificação, leia [references/spec-template.md](references/spec-template.md) para conhecer a estrutura de saída, os identificadores e o padrão dos critérios de aceitação.
