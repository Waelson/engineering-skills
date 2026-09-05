# Security Context Discovery

Descubra somente com evidência: usuários e serviços, atores potencialmente maliciosos, recursos protegidos, dados, integrações externas, operações privilegiadas, superfície e trust boundaries. Identifique o que um ator poderia obter, qual boundary atravessaria, qual controle deveria impedir e possíveis bypasses.

Classifique informação como:

- `CONFIRMED SECURITY REQUIREMENT`: comportamento de segurança requerido por fonte confirmada.
- `OBSERVED SECURITY BEHAVIOR`: comportamento constatado em código, teste ou execução; não prova intenção.
- `SECURITY ASSUMPTION`: hipótese com fonte, justificativa e impacto se incorreta.
- `OPEN SECURITY QUESTION`: lacuna objetiva com classificação e impacto.
- `PROPOSED SECURITY CONTROL`: controle sugerido, ainda não aprovado ou comprovado.
- `CONFIRMED SECURITY CONTROL`: controle confirmado e com evidência de aplicação relevante.

Antes de findings conclusivos em contexto complexo, resuma atores, recursos, boundaries, controles confirmados, assumptions, questões e riscos prioritários. Em `GREENFIELD`, priorize modelo de privilégio, dados, boundaries, abuso e auditabilidade. Em `EVOLUTION`, priorize regressões, novos bypasses, exposição e expansão de privilégio. Em `MIGRATION`, examine coexistência, legacy bypass, identidades ou enforcement divergentes, backfill e rollback de segurança.
