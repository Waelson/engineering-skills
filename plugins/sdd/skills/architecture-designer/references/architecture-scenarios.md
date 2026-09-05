# Cenários de Discovery e Design Arquitetural

Use estes cenários como testes normativos de decisão.

## 1. Requirement insuficiente

Entrada: “Precisamos processar eventos assincronamente.”

- Readiness: `ARCHITECTURE_DISCOVERY_REQUIRED`
- Esperado: não escolher Kafka; perguntar sobre durability, ordering, replay e constraints relevantes.

## 2. Tecnologia sugerida

Entrada: “Acho que podemos usar Redis para isso.”

- Esperado: classificar Redis como `PROPOSED OPTION`, não como constraint ou decisão confirmada.

## 3. Tecnologia obrigatória

Um ADR válido determina Kafka.

- Esperado: classificar Kafka como `EXISTING DECISION` com fonte; não perguntar desnecessariamente qual broker usar.

## 4. Número desconhecido

A escala não foi especificada.

- Esperado: não inventar RPS, partições ou réplicas; registrar `ARCH-QUESTION-*` ou `ARCH-ASSUMPTION-*` apropriada.

## 5. Duas opções válidas

Síncrono e assíncrono atendem parcialmente aos requisitos.

- Esperado: comparar trade-offs, perguntar a prioridade relevante e não decidir silenciosamente.

## 6. Draft solicitado

Entrada: “Faça uma proposta inicial com o que temos.”

- Readiness: `READY_FOR_ARCHITECTURE_DRAFT`
- Esperado: criar proposta preliminar com assumptions e decisões `Proposed`, sem inventar dados.

## 7. Brownfield com evidência

Código e ADRs já respondem parte das decisões.

- Esperado: usar o contexto antes de perguntar e questionar somente lacunas restantes.

## 8. Conflito de contexto

A spec afirma fail-closed e o código indica fail-open.

- Esperado: registrar `ARCHITECTURE_CONTEXT_CONFLICT` e não escolher uma das fontes silenciosamente.

## Asserções transversais

- arquitetura deriva de requisitos, não de preferência tecnológica;
- requisitos, constraints, tecnologias e números ausentes não são inventados;
- contexto do repositório é consultado antes de perguntar;
- perguntas são progressivas e de alto impacto;
- documentação só ocorre a partir de `READY_FOR_ARCHITECTURE_DRAFT`;
- decisões confirmadas, propostas, assumptions e questões permanecem separadas;
- recomendação não se torna decisão sem confirmação.
