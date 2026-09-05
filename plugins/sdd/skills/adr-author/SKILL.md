---
name: adr-author
description: Conduza discovery iterativo, enquadre e facilite decisões arquiteturais com o usuário e registre ADRs rastreáveis somente com status sustentado por confirmação. Use para criar ADR, documentar decisão técnica, comparar alternativas, formalizar decisão proposta ou confirmada e registrar substituição de decisão anterior. Não use para arquitetura completa, specification, implementação, code review, debugging ou escolha tecnológica sem discovery.
---

# Autor de ADR

Conduza uma sessão colaborativa para compreender e enquadrar uma decisão arquitetural, facilitar a escolha com o usuário e somente então registrá-la. Trabalhe em quatro fases obrigatórias: **Decision Discovery → Decision Framing → Decision Facilitation → ADR Authoring**.

**Regra absoluta:** nunca transforme uma recomendação própria em decisão aceita sem confirmação explícita. `PROPOSED OPTION`, `RECOMMENDED OPTION` e `CONFIRMED DECISION` não são equivalentes. `Recommended != Accepted`.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e inspecione `docs/architecture/adr/` para descobrir convenção, sequência e decisões existentes. Sem convenção conflitante, use `docs/architecture/adr/ADR-<NNN>-<slug>.md`.
2. Localize o contexto proporcional à decisão: baseline e change `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, ADRs relacionados, contratos, configurações e código relevante. Não leia o repositório inteiro nem pergunte o que essas fontes já estabelecem.
3. Leia integralmente [references/decision-discovery.md](references/decision-discovery.md). Classifique cada informação relevante e avalie a readiness como `DECISION_DISCOVERY_REQUIRED`, `DECISION_READY_FOR_EVALUATION` ou `DECISION_CONFIRMED`.
4. Em `DECISION_DISCOVERY_REQUIRED`, faça 1 a 4 perguntas de maior impacto por rodada e permaneça na conversa. Não crie arquivo nem recomende prematuramente quando faltarem drivers essenciais. Se uma lacuna pertencer aos requisitos, registre o bloqueio e recomende `$spec-author`.
5. Em **Decision Framing**, formule a necessidade de decisão sem pressupor solução, tecnologia ou mecanismo. Separe necessidade de solução candidata; “Kafka vs RabbitMQ” não é framing suficiente se mensageria ainda não foi estabelecida.
6. Ao atingir `DECISION_READY_FOR_EVALUATION`, leia [references/decision-facilitation.md](references/decision-facilitation.md) e [references/tradeoff-guidance.md](references/tradeoff-guidance.md). Compare alternativas plausíveis, apresente recomendação quando sustentada e solicite explicitamente que o usuário escolha ou confirme. Não decida pelo usuário.
7. Se o usuário pedir expressamente um draft antes da decisão, leia [references/adr-lifecycle.md](references/adr-lifecycle.md) e [references/adr-template.md](references/adr-template.md) e crie somente `Proposed`, com questões abertas e condições para aceitação. Fora desse pedido, não gere artefato durante discovery ou avaliação.
8. Somente em `DECISION_CONFIRMED`, com confirmação explícita ou evidência formal equivalente, leia [references/adr-process.md](references/adr-process.md) e [references/adr-lifecycle.md](references/adr-lifecycle.md) e crie ou atualize o ADR. Use `Accepted` quando apropriado e registre `Decision Source`.
9. Antes de gravar, verifique duplicidade, próximo número real, relações, status e rastreabilidade. Uma decisão alterada gera novo ADR com `Supersedes`; não reescreva substancialmente o histórico aceito.
10. Revise o resultado contra escolha automática, confirmação inferida de silêncio, recomendação como `Accepted`, assumptions silenciosas, contexto ou números inventados, alternativas artificiais, consequências promocionais, rastreabilidade ausente e path incorreto.

## Regras essenciais

- Use `Accepted` somente em `DECISION_CONFIRMED`, sustentado por confirmação explícita do usuário ou decisão formal inequívoca já registrada. Silêncio, ausência de objeção, wording ambíguo, preferência anterior ou recomendação da skill não confirmam decisão.
- Uma recomendação da `$architecture-designer` permanece `RECOMMENDED OPTION`, salvo quando a fonte também registrar explicitamente `Decision Status: Confirmed` e uma `Decision Source` confiável.
- Em `DECISION_DISCOVERY_REQUIRED`, continue o discovery e não produza ADR. Um ADR preliminar só pode ser `Proposed` quando o usuário pedir explicitamente um draft.
- Não invente requirements, constraints, contexto, alternativas, tecnologia, throughput, latência, timeout, retries, partições, réplicas, retenção, capacidade ou custo.
- Considere findings relevantes de `REVIEW.md`; não aceite uma decisão apoiada em premissa indefinida ou contraditória sem resolução.
- Preserve status suportados pela convenção local; na ausência dela, suporte `Proposed`, `Accepted`, `Rejected`, `Superseded` e `Deprecated`.
- Centralize ADRs em `docs/architecture/adr/`, inclusive para changes. Registre a change relacionada no ADR. Só use outra localização quando `AGENTS.md` estabelecer convenção explícita.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve identificadores e nomes de status estabelecidos.
- Não crie arquitetura completa, specification, plano de implementação ou código.

Consulte [references/adr-scenarios.md](references/adr-scenarios.md) para os cenários normativos.
