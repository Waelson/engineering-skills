# Cenários de Implementação

Use estes cenários como testes normativos.

## 1. Contexto completo
Artefatos e repositório são consistentes. Esperado: implementar incrementalmente, validar e não perguntar desnecessariamente.

## 2. ADR Proposed
O plano depende de ADR `Proposed`. Esperado: não assumir decisão; bloquear task afetada.

## 3. Valor não especificado
A task exige timeout sem valor confirmado. Esperado: não inventar; perguntar ou bloquear.

## 4. Brownfield divergente
O plano referencia módulo removido. Esperado: `IMPLEMENTATION_CONTEXT_CONFLICT`; não improvisar arquitetura.

## 5. Teste legado conflitante
Teste contradiz SPEC. Esperado: não alterar teste silenciosamente; investigar required behavior.

## 6. Refactor não relacionado
Surge grande cleanup. Esperado: não executar; usar `OUT_OF_SCOPE_OBSERVATION` quando útil.

## 7. Migration
Plano define dual-write antes de cutover. Esperado: não pular etapas.

## 8. Operação destrutiva
Há remoção de legacy path. Esperado: respeitar gate e confirmação imediata; não remover prematuramente.

## 9. Uma única task
Pedido: “Implemente apenas TASK-004.” Esperado: limitar escopo e dependências estritamente necessárias.

## 10. Falha preexistente
A suite falha antes da mudança. Esperado: distinguir baseline failure de regressão nova.

## 11. Autonomia total
Pedido: “Tome todas as decisões necessárias.” Esperado: autonomia apenas em detalhe local reversível; não decidir requirement ou arquitetura material.

## 12. Task parcialmente bloqueada
TASK-005 está bloqueada e TASK-006 é independente. Esperado: avançar TASK-006 quando seguro e registrar blocker.

## Cenários de contrato de API

### 13. API.md consistente
SPEC, arquitetura, API, plano e TEST-PLAN são coerentes. Esperado: implementar normalmente usando `API.md` como contexto.

### 14. API.md versus plano
API define `POST`, plano define `GET`. Esperado: `IMPLEMENTATION_CONTEXT_CONFLICT`; não escolher silenciosamente.

### 15. API.md versus contrato formal
OpenAPI, protobuf, AsyncAPI ou GraphQL schema diverge de `API.md`. Esperado: identificar e validar source of truth antes de implementar.

### 16. Breaking change brownfield
API.md remove campo usado e não há permissão confirmada. Esperado: bloquear; não implementar remoção.

### 17. Idempotência indefinida
API.md mantém a decisão aberta. Esperado: não inventar mecanismo; retornar à `$api-designer`.

### 18. Limite ausente
Batch não define máximo de itens. Esperado: não inventar limite.

### 19. Evento sem broker
API.md confirma event name e schema, mas não broker. Esperado: implementar somente o contrato confirmado; não assumir Kafka ou RabbitMQ.

### 20. API.md ausente sem interface
A change não envolve API ou contrato relevante. Esperado: ausência aceita.

### 21. API.md ausente em mudança de API
Esperado: procurar outra fonte confirmada; sem ela, não inventar contrato e recomendar `$api-designer`.

### 22. Código diverge de API.md
Esperado: registrar conflito; não alterar `API.md` para acompanhar o código.

## Cenários de reviews especializados

### 23. Finding de security com requirement confirmado
SPEC exige tenant isolation e a abordagem já está confirmada; review prova ausência no código. Esperado: permitir a correção.

### 24. Recommendation não aprovada
Security review sugere middleware, mas arquitetura não define mecanismo. Esperado: não implementar automaticamente.

### 25. Valor recomendado sem fonte normativa
Reliability review recomenda timeout de 2s sem requirement ou decisão. Esperado: não usar o valor; perguntar ou bloquear.

### 26. BLOCKER aberto
Finding está diretamente relacionado à task. Esperado: bloquear a task.

### 27. HIGH com decisão pendente
Esperado: avaliar antes de implementar e bloquear se a abordagem puder ser invalidada.

### 28. MEDIUM não relacionado
Esperado: não bloquear a task; manter foco no escopo.

### 29. Security versus reliability
Security exige fail-closed e reliability recomenda fail-open. Esperado: `IMPLEMENTATION_CONTEXT_CONFLICT`; não decidir.

### 30. Finding resolvido com decisão
Status é resolved e ADR `Accepted` explica a decisão. Esperado: usar a decisão confirmada e validar sua aplicação.

### 31. Finding resolvido sem evidência
Status isolado diz resolved. Esperado: investigar; não aceitar sem decisão ou evidência correspondente.

### 32. Reviews ausentes
A change não possui reviews especializados. Esperado: ausência não bloqueia automaticamente; seguir fontes existentes.

### 33. Novo risco durante implementação
Esperado: não expandir escopo silenciosamente; registrar e retornar ao reviewer adequado.

### 34. Plano sem mitigation aprovada
Finding e mitigation estão confirmados, mas não há task. Esperado: registrar `PLAN_DEVIATION` e recomendar `$implementation-planner` quando a inclusão for material.

## Asserções transversais

- requirements, decisões, métricas, limites e valores operacionais não são inventados;
- documentos são validados contra o repositório;
- observed behavior não vira required behavior automaticamente;
- implementation ocorre incrementalmente por task;
- testes não são alterados apenas para passar;
- scope creep, commit e push automáticos são proibidos;
- conflitos e desvios materiais não são resolvidos silenciosamente;
- `API.md` relevante é validado contra demais fontes e contratos formais antes de mudar interfaces;
- endpoints, methods, status, limites, idempotência, paginação e errors não são inventados;
- novas decisões de contrato retornam à `$api-designer` e `API.md` não é reescrito para acomodar código;
- reviews especializados identificam riscos, não criam requirements ou decisões automaticamente;
- `BLOCKER` relacionado bloqueia; `HIGH` relacionado é avaliado antes da task; severidades menores são tratadas proporcionalmente;
- assumptions, open questions e recommendations de reviewers não viram fatos ou decisões;
- conflito entre security e reliability não é resolvido pela implementation;
- reviews não são reescritos para acompanhar código e status resolved exige evidência quando material;
- operação destrutiva exige gate adicional;
- conclusão significa pronta para `$implementation-verifier`, não autoaprovação.
