# Orientação de Evidências

## Evidência suficiente

Combine fontes conforme o claim: código/diff para implementação, teste e assertion para comportamento, benchmark para performance, contratos para compatibilidade, migrations e consultas para dados, logs/métricas/traces para observabilidade e comandos reais para build/checks.

Teste passando não prova conformidade sozinho. Verifique se cobre o requirement correto, afirma resultado relevante, não foi enfraquecido e não usa mock que oculte integração essencial. Teste que verifica apenas HTTP 200 pode ser `PARTIAL` para AC que exige conteúdo específico.

## NFRs

Não declare latência ou throughput como `PASS` sem medição adequada. Retry não prova availability; middleware não prova security; código de métrica não prova emissão operacional. Sem evidência, use `UNVERIFIED_NFR` ou `NOT_VERIFIED`.

## Planos e decisões

Task marcada `Completed` exige código, requirements, testes e completion criteria comprovados. ADR `Accepted` relevante deve ser conferido contra a implementação; ADR `Proposed` não cria obrigação confirmada e seu uso pelo código é finding potencial.

## Comandos e falhas

Execute somente comandos definidos pelo projeto. Registre comando, resultado e limitação. Quando necessário, compare baseline para separar `PREEXISTING_FAILURE` de `REGRESSION`.
