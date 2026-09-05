---
name: adr-author
description: Conduza discovery e facilitação de decisões arquiteturais e registre ADRs rastreáveis com status apropriado. Use para criar ADR, documentar decisão técnica, comparar alternativas para um ADR, formalizar decisão proposta ou confirmada e registrar substituição de decisão anterior. Não use para arquitetura completa, specification, implementação, code review, debugging ou escolha tecnológica sem discovery.
---

# Autor de ADR

Conduza uma sessão colaborativa para compreender uma decisão arquitetural relevante e somente então registrá-la. Trabalhe em três fases: **Decision Discovery → Decision Facilitation → ADR Authoring**. Um ADR registra uma decisão realmente tomada; recomendação não equivale a decisão aceita.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e inspecione `docs/architecture/adr/` para descobrir convenção, sequência e decisões existentes. Sem convenção conflitante, use `docs/architecture/adr/ADR-<NNN>-<slug>.md`.
2. Localize o contexto proporcional à decisão: baseline e change `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, ADRs relacionados, contratos, configurações e código relevante. Não leia o repositório inteiro nem pergunte o que essas fontes já estabelecem.
3. Leia integralmente [references/decision-discovery.md](references/decision-discovery.md). Classifique cada informação relevante e avalie a readiness como `DECISION_DISCOVERY_REQUIRED`, `READY_FOR_ADR_DRAFT` ou `DECISION_CONFIRMED`.
4. Em discovery, faça normalmente 2 a 5 perguntas de maior impacto por rodada. Se uma lacuna pertencer aos requisitos, não a invente: registre o bloqueio e recomende retorno a `$spec-author`.
5. Leia [references/tradeoff-guidance.md](references/tradeoff-guidance.md). Compare somente alternativas plausíveis e dimensões aplicáveis. Considere manter o estado atual quando relevante; não force quantidade fixa de opções.
6. Facilite a escolha separando `PROPOSED OPTION`, `RECOMMENDED OPTION` e `CONFIRMED DECISION`. Quando necessário, consolide problema, drivers, constraints, alternativas, recomendação, trade-offs e decisão confirmada antes de escrever um ADR `Accepted`.
7. Somente após atingir `READY_FOR_ADR_DRAFT`, leia [references/adr-process.md](references/adr-process.md) e [references/adr-template.md](references/adr-template.md). Crie no máximo um ADR por decisão, com estrutura adaptada ao contexto.
8. Antes de gravar, verifique duplicidade, próximo número real, relações, status e rastreabilidade. Uma decisão alterada gera novo ADR com `Supersedes`; não reescreva substancialmente o histórico aceito.
9. Revise o resultado contra decisão não confirmada como `Accepted`, contexto ou números inventados, alternativas artificiais, consequências promocionais, rastreabilidade ausente e path incorreto.

## Regras essenciais

- Use `Accepted` somente com `CONFIRMED DECISION` sustentada por confirmação explícita, decisão formal existente ou constraint institucional inequívoca. Uma recomendação da arquitetura permanece `Proposed` até confirmação.
- Em `DECISION_DISCOVERY_REQUIRED`, continue o discovery e não produza ADR final. Em `READY_FOR_ADR_DRAFT`, um ADR preliminar pode ser `Proposed`, com assumptions, questões abertas e condição para aceitação explícitas.
- Não invente requirements, constraints, contexto, alternativas, tecnologia, throughput, latência, timeout, retries, partições, réplicas, retenção, capacidade ou custo.
- Considere findings relevantes de `REVIEW.md`; não aceite uma decisão apoiada em premissa indefinida ou contraditória sem resolução.
- Preserve status suportados pela convenção local; na ausência dela, suporte `Proposed`, `Accepted`, `Rejected`, `Superseded` e `Deprecated`.
- Centralize ADRs em `docs/architecture/adr/`, inclusive para changes. Registre a change relacionada no ADR. Só use outra localização quando `AGENTS.md` estabelecer convenção explícita.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve identificadores e nomes de status estabelecidos.
- Não crie arquitetura completa, specification, plano de implementação ou código.

Consulte [references/adr-scenarios.md](references/adr-scenarios.md) para os cenários normativos.
