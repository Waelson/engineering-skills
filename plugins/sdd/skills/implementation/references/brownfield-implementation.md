# Implementação em Brownfield

Priorize pequenos deltas, comportamento confirmado, compatibilidade, regression safety, contratos e integrações impactadas. Inspecione testes antes de alterar comportamento.

Characterization tests podem proteger refactor quando o plano os exigir ou quando forem necessários para entender risco. Rotule-os como comportamento observado: eles não criam requirement nem tornam correto um legado conflitante.

Não introduza breaking change sem `COMPAT-*`, requirement ou decisão explícita. Verifique APIs, schemas, events, persistence, consumers e config relevantes. Não edite generated files diretamente; encontre fonte e comando gerador.

Evite cleanup e modernização não relacionados. Uma descoberta pode ser reportada sem ampliar o patch.
