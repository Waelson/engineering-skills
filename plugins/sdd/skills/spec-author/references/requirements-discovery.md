# Requirements Discovery

## Princípio

Não comece pela specification. Comece pelo entendimento do problema:

```text
Necessidade inicial → Discovery → Clarificação → Entendimento consolidado → Specification
```

Conduza discovery de forma natural e incremental. Identifique as lacunas de maior impacto, faça poucas perguntas, use as respostas para refinar o entendimento e repita somente quando necessário. Se o usuário já forneceu contexto suficiente, avance sem perguntas artificiais.

## Classificação das perguntas

- `BLOCKING`: respostas diferentes alteram materialmente a specification, como comportamento central, regra de negócio, permissões, erro, source of truth, exclusão ou consistência crítica. Priorize antes da escrita.
- `IMPORTANT`: melhora precisão, mas pode permanecer como questão aberta em um draft, como volume futuro, retenção, limite operacional, preferência de rollout ou métrica ainda indefinida.
- `OPTIONAL`: detalhe que não deve bloquear a primeira spec, como naming, estética, implementação ou decisão pertencente a outra skill.

Não é necessário mostrar os rótulos ao usuário. Use-os para ordenar as perguntas. Faça normalmente 2 a 5 perguntas por rodada, sem repetir o que já foi respondido ou pode ser inferido com alta confiança.

## Readiness para escrita

- `DISCOVERY_REQUIRED`: faltam respostas críticas para uma specification coerente. Faça perguntas e, se útil, consolide apenas o entendimento parcial; não gere uma spec completa.
- `READY_FOR_DRAFT`: problema, atores, resultado e regras essenciais permitem uma primeira versão útil. Registre premissas e questões não bloqueantes; não invente respostas.
- `READY_FOR_SPEC`: comportamento essencial, contratos e riscos relevantes estão suficientemente compreendidos para uma specification madura.

O pedido “faça uma primeira versão com o que temos” permite avançar para `READY_FOR_DRAFT` quando existe entendimento mínimo coerente. Uma questão realmente bloqueante continua exigindo esclarecimento breve sobre por que a resposta é necessária.

## Classificação do conhecimento

- `CONFIRMED FACT`: informação confirmada pelo usuário ou fonte confiável do projeto.
- `REQUIREMENT`: necessidade ou comportamento esperado explicitamente confirmado.
- `ASSUMPTION`: hipótese temporária usada para avançar; deve permanecer identificável.
- `OPEN QUESTION`: informação relevante ainda desconhecida.
- `CONSTRAINT`: restrição já existente ou imposta ao problema.
- `PROPOSED SOLUTION`: mecanismo sugerido que ainda não foi confirmado como requisito ou restrição.

Nunca promova silenciosamente uma premissa, evidência observada ou solução proposta a requisito. Requisitos importantes devem derivar de confirmação, restrição estabelecida ou comportamento atual explicitamente confirmado para preservação.

## Necessidade versus solução

Ao ouvir “API Kafka para processar pedidos”, não presuma Kafka, REST, novo serviço ou persistência como requisitos. Separe, por exemplo:

```text
Necessidade: processar pedidos de forma assíncrona.
Solução proposta: Kafka.
```

Confirme se Kafka é uma constraint já decidida. Caso contrário, mantenha como solução proposta ou **Decisão Arquitetural Necessária**.

## Áreas de investigação

Selecione somente os tópicos relevantes:

- problema atual, impacto e pessoas afetadas;
- usuários, sistemas, operadores ou administradores consumidores;
- resultado que caracteriza sucesso;
- regras de negócio, exceções, estados proibidos e condições especiais;
- happy path, fluxos alternativos e erros esperados;
- dados, origem, sensibilidade, retenção e consistência;
- contratos e compatibilidade que precisam ser preservados;
- escala, pico, cardinalidade e crescimento, sem inventar métricas;
- confiabilidade: dependências, repetição, duplicação, fail-open/closed;
- segurança: sujeito, recurso, ação, tenants, dados sensíveis e auditoria.

### Greenfield

Priorize problema, atores, casos de uso, regras, restrições, interfaces esperadas, escala, segurança e confiabilidade. Não force estado atual, compatibilidade ou migração sem necessidade.

### Evolution

Além da necessidade nova, descubra comportamento atual, delta desejado, comportamento a preservar, consumidores afetados, compatibilidade e regressões. Consulte primeiro evidências relevantes do repositório.

### Migration

Descubra motivação, estados atual e alvo, restrições, coexistência, compatibilidade, dados, cutover, rollback e riscos aplicáveis. Não escolha tecnologia automaticamente.

## Evidência versus intenção

Use o repositório para reduzir perguntas em brownfield, mas não leia tudo indiscriminadamente. Quando o código demonstrar fail-open sem confirmação documental, registre:

```text
Comportamento observado: a implementação atual usa fail-open quando a dependência está indisponível.
Confirmação pendente: esse comportamento é intencional e deve ser preservado?
```

## Checkpoint de entendimento

Depois de uma ou mais rodadas, consolide quando isso ajudar o usuário a corrigir interpretações:

```text
Entendimento atual

Problema: ...
Usuários/consumidores: ...
Comportamento atual: ...
Comportamento desejado: ...
Regras confirmadas:
- ...
Premissas:
- ...
Ainda precisamos definir:
- ...
```

Não exija aprovação formal a cada checkpoint. Se o entendimento estiver claro e a readiness for suficiente, avance.

## Exemplo: batch authorization

Não invente `1000` itens nem `POST /authorize/batch`. Primeiro confirme, conforme necessário:

1. Cada item retorna sua própria decisão?
2. Uma falha invalida o batch ou permite resultado parcial?
3. Existe limite conhecido de itens?
4. A semântica da autorização individual deve ser preservada integralmente?

Somente então formalize os comportamentos confirmados como requisitos e critérios verificáveis.
