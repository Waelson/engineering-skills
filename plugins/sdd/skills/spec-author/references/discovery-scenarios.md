# Cenários de Requirements Discovery

Use estes cenários como testes normativos de decisão.

## 1. Pedido muito vago

Entrada: “Quero criar um serviço para gerenciar clientes.”

- Readiness: `DISCOVERY_REQUIRED`
- Esperado: não criar uma spec completa; perguntar progressivamente sobre problema, consumidores e casos de uso.

## 2. Informação suficiente

A entrada já contém problema, usuários, comportamento, regras, constraints e NFRs.

- Readiness: `READY_FOR_DRAFT` ou `READY_FOR_SPEC`
- Esperado: fazer poucas ou nenhuma pergunta adicional e avançar para o artefato apropriado.

## 3. Solução disfarçada de requisito

Entrada: “Precisamos usar Kafka para melhorar o processamento.”

- Esperado: descobrir a necessidade real e determinar se Kafka é `CONSTRAINT` ou `PROPOSED SOLUTION`; não promovê-lo automaticamente a requisito.

## 4. Brownfield

Entrada: “Adicione batch authorization.” O repositório possui implementação atual.

- Esperado: inspecionar somente o contexto relevante; perguntar apenas o que as evidências não respondem; não inventar limites, endpoint ou contrato.

## 5. Regra crítica ambígua

Um batch não define o comportamento de falha parcial.

- Pergunta: `BLOCKING`
- Esperado: confirmar se a falha é parcial ou atômica antes de criar requisito ou critério de aceitação.

## 6. NFR desconhecido

O usuário não sabe o throughput esperado.

- Pergunta: normalmente `IMPORTANT`
- Esperado: registrar `OPEN-QUESTION-*`; não inventar RPS e não bloquear o draft se o restante estiver coerente.

## 7. Draft rápido

Entrada: “Faça uma primeira versão com o que temos.”

- Readiness: `READY_FOR_DRAFT`, quando houver entendimento mínimo coerente
- Esperado: gerar o draft, explicitando `ASSUMPTION-*` e `OPEN-QUESTION-*` não bloqueantes.

## 8. Migration

Entrada: “Quero migrar o storage atual.”

- Contexto: `MIGRATION`
- Esperado: perguntar progressivamente sobre motivação, estados atual e alvo, compatibilidade e riscos relevantes; não escolher tecnologia automaticamente.

## Asserções transversais

- não gerar uma specification completa enquanto houver ambiguidade bloqueante;
- usar poucas perguntas por rodada e evitar questionário mecânico;
- consultar evidências relevantes em brownfield antes de perguntar;
- não inventar regras, métricas, contratos ou intenção;
- não converter solução proposta em requirement sem confirmação;
- permitir draft com dúvidas não bloqueantes explícitas;
- preservar o roteamento de artefatos sob `docs/`;
- não implementar código nem assumir arquitetura detalhada ou revisão independente.
