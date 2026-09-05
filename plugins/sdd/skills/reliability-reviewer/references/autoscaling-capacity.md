# Autoscaling, Saturation e Capacity

Valide qual métrica aciona scaling, se representa offered ou served load, tempo de reação, minimum replicas, scale-down, cold start e limites conhecidos. Autoscaling não garante resposta rápida nem cria capacidade ilimitada.

Não use apenas CPU/memória para inferir saturação. Considere queue depth/age, concurrency, pools, threads/goroutines, event loop, downstream latency, datastore saturation, broker lag e file descriptors conforme o sistema.

Use somente métricas confirmadas. Para NFR quantitativo, verifique plano e evidência de load test; sem target ou medição, registre gap. Observability relevante pode incluir offered, served, rejected e queued load, dependency latency, retries, timeouts, saturation, lag, shed rate e scaling lag, mas não exija todos os sinais em todos os sistemas.
