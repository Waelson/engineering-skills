# Facilitação da Decisão

## Papel

Facilite a escolha; não atue como autoridade final. Apresente opções e trade-offs em `DECISION_READY_FOR_EVALUATION`, recomende somente quando houver base e sempre mantenha a recomendação separada da decisão.

## Formato adaptativo

```text
Decisão:
<necessidade enquadrada sem pressupor solução>

Drivers confirmados:
- ...

Constraints confirmadas e fontes:
- ...

Opção A:
...
Vantagens:
- ...
Desvantagens:
- ...

Opção B:
...
Vantagens:
- ...
Desvantagens:
- ...

Recomendação:
<opção e racional, quando houver evidência>

Decision Status:
Awaiting user confirmation
```

Não force alternativas artificiais. Se nenhuma opção plausível estiver clara, retorne ao discovery.

## Confirmação obrigatória

Antes de `Accepted`, apresente um checkpoint curto com problema, drivers, constraints, alternativas, recomendação, trade-off principal e questões blocking restantes. Se não houver questão blocking, faça uma pergunta inequívoca, por exemplo:

```text
Com base nos requisitos confirmados, recomendo a opção B porque ...
Você confirma a opção B como decisão arquitetural?
```

Confirmações válidas incluem “Sim, vamos com essa opção”, “Escolha a opção B”, “Decidimos usar Kafka”, “Essa é a decisão” ou decisão formal inequívoca já registrada com fonte. Não inferir confirmação de silêncio, ausência de objeção, wording ambíguo, preferência passada ou recomendação própria.

Quando o usuário já trouxer uma decisão explícita, não reabra a escolha. Verifique apenas o contexto necessário para documentar o racional; perguntas adicionais devem esclarecer drivers, consequências ou rastreabilidade.

## Estados não equivalentes

- `PROPOSED OPTION`: alternativa plausível ainda em análise.
- `RECOMMENDED OPTION`: preferência analítica da skill, aguardando escolha.
- `CONFIRMED DECISION`: alternativa explicitamente escolhida ou formalmente confirmada.

Somente `CONFIRMED DECISION` permite `DECISION_CONFIRMED`. Uma recommendation da arquitetura continua `RECOMMENDED OPTION` até confirmação explícita, exceto quando a própria fonte registrar decisão confirmada e sua origem.
