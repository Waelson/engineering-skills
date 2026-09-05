# Implementação em Brownfield

Priorize pequenos deltas, comportamento confirmado, compatibilidade, regression safety, contratos e integrações impactadas. Inspecione testes antes de alterar comportamento.

Characterization tests podem proteger refactor quando o plano os exigir ou quando forem necessários para entender risco. Rotule-os como comportamento observado: eles não criam requirement nem tornam correto um legado conflitante.

Quando houver `API.md`, compare `Current Contract → Required Change → Target Contract` com API real, consumers, contract tests, handlers, schemas e compatibility requirements. Não assuma que o contrato atual está errado; confirme intenção, permissão de breaking change e plano de versioning/migration.

Não introduza breaking change sem `COMPAT-*`, requirement ou decisão explícita. Verifique APIs, schemas, events, persistence, consumers e config relevantes. Não edite generated files diretamente; encontre fonte e comando gerador. Se código e `API.md` divergirem, registre conflito; nunca edite `API.md` apenas para refletir a implementação.

Evite cleanup e modernização não relacionados. Uma descoberta pode ser reportada sem ampliar o patch.

Considere reviews especializados para detectar regressão de controles, bypass, novos failure modes, alterações de retry/timeout, expansão de trust boundary e mudança de capacity profile. Não aplique recommendation como decisão nem bloqueie uma task por finding não relacionado.
