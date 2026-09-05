# Revisão de Concorrência

Demonstre que acessos podem ocorrer concorrentemente antes de registrar race. Identifique shared mutable state, execução paralela, sincronização e ordem de eventos. Avalie data race, check-then-act, lost update, atomicity, lock ordering, deadlock, channel misuse e lifecycle de worker/goroutine/thread.

Não infira concorrência apenas porque há map, cache ou async function. Considere transaction/isolation semantics e cancelamento reais. Se o bug depender de garantia não definida, registre questão ou conflito; não invente scheduling extremo sem caminho plausível.
