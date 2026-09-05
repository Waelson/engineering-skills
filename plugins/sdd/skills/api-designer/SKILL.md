---
name: api-designer
description: Conduza discovery e design iterativo de contratos de API rastreáveis a partir de requisitos, arquitetura, constraints e decisões confirmadas. Use para criar, revisar ou evoluir contratos REST, gRPC, GraphQL, eventos ou outras interfaces, definir operações, erros, compatibilidade e versionamento. Não use para discovery amplo de requisitos, arquitetura completa, implementação, planning, code review ou test design completo.
---

# Designer de APIs

Conduza uma sessão colaborativa para definir o contrato que representa requisitos confirmados, preserva compatibilidade quando necessário e oferece semântica clara a consumidores e implementadores. Trabalhe em quatro fases: **API Context Discovery → Contract Decision Facilitation → API Contract Design → Contract Validation**.

Não comece criando endpoints, métodos, mensagens ou schemas. Primeiro entenda consumidores, problema, operações, dados, falhas, constraints e contratos a preservar. Não presuma protocolo nem conhecimento técnico do usuário.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e localize `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, ADRs e contratos relacionados. Inspecione somente OpenAPI, protobuf, GraphQL, AsyncAPI, handlers, clientes, testes e documentação relevantes.
2. Leia integralmente [references/api-discovery.md](references/api-discovery.md). Diferencie requirement, constraint, contrato existente, assumption, questão aberta e decisão proposta ou confirmada; não pergunte o que o repositório já estabelece.
3. Classifique o contexto como `GREENFIELD`, `EVOLUTION` ou `MIGRATION` e a readiness como `API_DISCOVERY_REQUIRED`, `READY_FOR_API_DRAFT` ou `API_CONTRACT_READY`.
4. Em lacunas materiais, faça 1 a 4 perguntas de alto impacto por rodada. Explique brevemente conceitos como idempotência, paginação por cursor ou entrega at-least-once antes de pedir uma decisão técnica; se necessário, reformule em linguagem de comportamento.
5. Quando existirem alternativas plausíveis, compare drivers e trade-offs, separe recomendação de decisão e solicite confirmação. Nunca transforme `PROPOSED CONTRACT DECISION` em `CONFIRMED CONTRACT DECISION` por conta própria.
6. Após `READY_FOR_API_DRAFT`, leia [references/api-contract-design.md](references/api-contract-design.md) e produza ou atualize `docs/changes/<change-id>/API.md`. Use `Status: Draft` enquanto houver assumptions ou decisões materiais abertas.
7. Leia condicionalmente [references/rest-guidance.md](references/rest-guidance.md), [references/grpc-guidance.md](references/grpc-guidance.md) ou [references/event-api-guidance.md](references/event-api-guidance.md) somente quando esse estilo estiver confirmado. Para compatibilidade, leia [references/api-compatibility.md](references/api-compatibility.md); para falhas, leia [references/error-semantics.md](references/error-semantics.md).
8. Valide semântica, dados, erros, idempotência, consistência, segurança, compatibilidade, versionamento, observabilidade e rastreabilidade somente quando aplicáveis. Atualize `API.md` existente e preserve decisões confirmadas e IDs.
9. **Hard gate:** nunca marque o contrato como `Ready` enquanto houver decisão `BLOCKING` não confirmada sobre semântica, compatibilidade, erros, idempotência, dados ou comportamento operacional.

## Limites

- Não invente requirements, contratos, protocolo, códigos de erro ou status, limites, timeouts, tamanhos, paginação, filtros, ordenação, auth, broker, delivery semantics ou migration strategy.
- Não assuma REST, gRPC, GraphQL, eventos, WebSocket, streaming, RPC ou HTTP síncrono. Respeite protocolo confirmado por arquitetura, ADR ou constraint; caso contrário, trate-o como decisão aberta.
- Não redesenhe toda a API em brownfield. Represente `Current Contract → Required Change → Target Contract` e preserve compatibilidade confirmada.
- Registre conflito material como `API_CONTEXT_CONFLICT`; não escolha silenciosamente entre SPEC, arquitetura, ADR, contrato, código ou testes.
- Quando surgir regra de negócio ausente, pergunte ou recomende `$spec-author`. Quando a decisão for arquiteturalmente significativa, registre `Architecture Decision Required` e recomende `$adr-author`; não crie ADR automaticamente.
- Não implemente handlers ou código, não decomponha tasks e não desenhe uma suite completa de testes. O contrato deve permitir planning e derivação posterior de contract, compatibility, negative e idempotency tests.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável. Preserve IDs de requisitos e use `API-ASSUMPTION-*` e `API-QUESTION-*`.

Consulte [references/api-scenarios.md](references/api-scenarios.md) para os cenários normativos.
