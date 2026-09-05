# Revisão de Corretude

Rastreie control flow, precondições, branches, retornos, estado e efeitos. Procure condição invertida, off-by-one, edge case concreto, resultado parcial indevido, branch ausente, write parcial, overwrite, transaction boundary incorreta e incompatibilidade de request/response ou error mapping.

Em error handling, verifique erro ignorado, mascarado, substituído ou retornado como sucesso; cleanup e rollback; preservação de causa e comportamento consistente. Em resources, examine conexões, files, transactions, contexts, goroutines/threads e executors conforme linguagem e framework.

Adapte à linguagem: em Go, context, defer, nil, wrapping, channels e lifecycle; em Java, resources, transactions, nullability, exceptions e executors; em JavaScript/TypeScript, async/await, rejection, narrowing, mutation e event-loop blocking. Use somente checks relevantes e não limite a review a essas linguagens.
