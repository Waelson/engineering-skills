# Orientação de Trade-offs

## Comparação responsável

Comece pelos drivers e constraints, não por preferência tecnológica. Compare somente alternativas que poderiam resolver o problema no contexto conhecido. Não exija três opções; duas podem bastar, e uma única opção viável pode ser comparada com manter o estado atual quando isso fizer sentido.

Para cada alternativa relevante:

1. descreva a capacidade ou abordagem, sem linguagem promocional;
2. relacione-a aos drivers e constraints confirmados;
3. registre benefícios, custos, riscos e condições de validade;
4. avalie apenas dimensões aplicáveis, como complexidade, latência, throughput, consistência, disponibilidade, durabilidade, escalabilidade, carga operacional, segurança, custo, compatibilidade, reversibilidade e esforço de migração;
5. exponha desconhecidos que possam inverter a comparação.

Não afirme que uma opção é mais rápida, barata ou escalável sem evidência contextual. Não invente métricas, custos ou capacidade.

## Recomendação versus decisão

Uma recomendação é permitida quando os drivers sustentam uma preferência:

```text
Recommended Option: propagação orientada a eventos
Rationale: atende aos drivers confirmados ...
Status: Awaiting confirmation
```

Mantenha-a como `RECOMMENDED OPTION` até existir confirmação explícita. `Recommended != Accepted`. Se não houver evidência suficiente para recomendar, apresente a comparação e a pergunta que falta; nunca invente uma alternativa para completar a análise.

## Consequências e reversibilidade

Registre consequências positivas e negativas reais: consistência eventual, complexidade operacional, acoplamento, latência, dependência de plataforma, esforço de migração ou perda de reversibilidade, conforme aplicável. Classifique reversibilidade como fácil, moderada ou difícil somente quando houver base para justificar a classificação.
