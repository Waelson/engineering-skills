# Discovery de API

## Fontes e escopo

Para uma change, consulte `docs/changes/<change-id>/SPEC.md`, `REVIEW.md` e `ARCHITECTURE.md`; quando aplicáveis, consulte `docs/spec/SPEC.md`, `docs/architecture/ARCHITECTURE.md`, `docs/architecture/adr/` e `AGENTS.md`. Inspecione contratos, handlers, clientes e testes apenas o suficiente para responder questões materiais.

Descubra quem consome a interface, qual problema resolve, operações necessárias, entradas e saídas, falhas distinguíveis, efeitos, constraints e contratos a preservar. Não confunda implementação observada com intenção confirmada.

## Classificação do conhecimento

- `CONFIRMED REQUIREMENT`: necessidade ou comportamento confirmado e rastreável.
- `EXISTING CONTRACT`: contrato atual observado e validado.
- `EXISTING CONSTRAINT`: restrição confirmada por fonte confiável.
- `API ASSUMPTION`: hipótese explícita ainda não confirmada.
- `OPEN API QUESTION`: lacuna cuja resposta pode alterar o contrato.
- `PROPOSED CONTRACT DECISION`: alternativa ou recomendação aguardando confirmação.
- `CONFIRMED CONTRACT DECISION`: escolha confirmada pelo usuário ou por fonte formal inequívoca.

Use `API-ASSUMPTION-001` com hipótese, motivo e impacto se incorreta. Use `API-QUESTION-001` com pergunta objetiva, classificação `BLOCKING`, `IMPORTANT` ou `OPTIONAL` e impacto.

## Readiness

- `API_DISCOVERY_REQUIRED`: existem lacunas materiais; pergunte e não consolide contrato final.
- `READY_FOR_API_DRAFT`: há informação suficiente para proposta inicial com assumptions, decisões propostas e questões abertas explícitas.
- `API_CONTRACT_READY`: decisões materiais foram confirmadas e o contrato pode orientar implementação.

Perguntas `BLOCKING` impedem `Ready`. Faça 1 a 4 perguntas por rodada, priorizando protocolo/interaction model, semântica, partial success, compatibilidade, erros, idempotência e dados quando alterarem materialmente o contrato.

## Checkpoint

Antes de consolidar uma proposta material, quando isso reduzir risco, resuma consumidores, casos de uso, operações, contrato atual, comportamento a preservar, decisões confirmadas, decisões abertas e assumptions. Permita correção sem exigir aprovação burocrática de fatos já estabelecidos.
