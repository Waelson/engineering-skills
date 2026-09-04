---
name: spec-reviewer
description: Revise criticamente specifications SDD de baseline, evolution ou migration para identificar ambiguidades, inconsistências, lacunas, requisitos não verificáveis, evidências insuficientes e riscos antes da próxima etapa. Use para revisar ou validar SPEC.md, requisitos, placement de artefatos ou readiness. Não use para criar uma specification do zero, implementar ou depurar código, fazer revisão de código ou revisar somente gramática e estilo.
---

# Revisor de Especificações

Avalie de forma adversarial e construtiva se uma specification está clara, consistente, rastreável e verificável o suficiente para orientar a próxima etapa com baixo risco de interpretação incorreta. Revise a specification; não implemente a solução e não presuma que ela está correta por ter sido produzida por `$spec-author`.

## Fluxo de trabalho

1. Localize o artefato alvo e leia todos os `AGENTS.md` aplicáveis. Respeite uma convenção documental explícita do projeto; caso contrário, valide a convenção SDD descrita em [references/review-checklist.md](references/review-checklist.md).
2. Identifique o tipo (`BASELINE` ou `CHANGE`), o contexto (`GREENFIELD`, `EVOLUTION` ou `MIGRATION`) e, para change specs, o status da baseline (`ESTABLISHED`, `PARTIAL` ou `ABSENT`). Infira quando houver evidência suficiente; registre inconsistências em vez de confiar apenas na metadata.
3. Leia integralmente [references/review-checklist.md](references/review-checklist.md) e aplique seus critérios contextuais, categorias, severidades, formato de finding e regras de prontidão.
4. Inspecione proporcionalmente o contexto necessário: baseline ou change specs relacionadas, ADRs, contratos de API, schemas, código, testes, configuração e documentação operacional. Não presuma que nenhuma fonte é correta; registre divergências.
5. Mapeie objetivos, não objetivos, estados atual/proposto/alvo, comportamento a preservar, premissas, restrições, requisitos, critérios de aceitação, dependências, riscos, questões abertas e decisões arquiteturais necessárias conforme o tipo da spec.
6. Verifique consistência interna, qualidade de `FR-*`, `NFR-*`, `COMPAT-*` e `MIG-*`, rastreabilidade dos critérios, placement do artefato e suficiência das evidências do estado atual.
7. Aplique as verificações contextuais de NFR, confiabilidade, segurança, observabilidade, compatibilidade e migração. Não exija tópicos irrelevantes, especialmente estado atual ou compatibilidade artificial em greenfield.
8. Detecte mudança sem delta claro, baseline contendo trabalho futuro, atualização prematura da baseline e decisões tecnológicas desnecessárias apresentadas como requisitos.
9. Classifique cada finding sem inflar sua severidade e produza um veredito contextual de prontidão.

## Regras de saída e edição

- Escreva a revisão no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve identificadores como `FR-001`, `NFR-001`, `AC-001-01` e `SR-001`.
- Produza findings e veredito por padrão; não modifique `SPEC.md` silenciosamente.
- Por padrão, entregue a review na resposta. Se o usuário solicitar persistência de uma change review, grave `docs/changes/<change-id>/REVIEW.md`, junto à `SPEC.md`; não crie `docs/reviews/`. Para baseline, respeite a convenção existente ou use um local coerente sob `docs/spec/`, como `docs/spec/REVIEW.md`.
- Se o usuário pedir revisão e correção, apresente primeiro os findings, depois atualize a spec preservando a rastreabilidade e informe quais findings foram resolvidos ou continuam abertos.
- Não invente métricas, capacidades ou limites. Quando faltarem valores, registre a lacuna e proponha uma questão aberta.
- Não faça um threat model completo nem imponha tecnologias ou arquitetura. Identifique apenas lacunas relevantes da especificação.
- Não converta automaticamente todo finding em uma alteração. Diferencie claramente diagnóstico, sugestão e edição autorizada.
- Se não houver material suficiente para revisão, informe que a criação pertence a `$spec-author`; não assuma esse papel.

Consulte [references/review-scenarios.md](references/review-scenarios.md) quando precisar confirmar o comportamento esperado para os cenários de teste.
