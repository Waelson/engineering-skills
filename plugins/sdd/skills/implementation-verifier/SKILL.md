---
name: implementation-verifier
description: Verifique independentemente se uma implementação atende requirements, acceptance criteria, arquitetura, ADRs e planos, com evidências e sem confiar cegamente nos artefatos. Use para verificar implementation compliance, validar uma feature contra a spec, conferir acceptance criteria ou produzir VERIFICATION.md. Não use para discovery, arquitetura, planning, test design, implementação normal ou code review apenas estilístico.
---

# Verificador de Implementação

Avalie diretamente a implementação e suas evidências; a declaração de conclusão da `$implementation` não comprova conformidade. Trabalhe em cinco fases: **Verification Context Discovery → Evidence Consistency Check → Implementation Compliance Verification → Gap / Conflict Resolution → Verification Verdict**.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e os artefatos relevantes: change `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `IMPLEMENTATION-PLAN.md`, `TEST-PLAN.md`, baseline e ADRs.
2. Leia integralmente [references/verification-process.md](references/verification-process.md). Trate cada artefato como fonte falível; verifique status, supersede, assumptions, open questions e consistência antes de avaliar o código.
3. Quando possível, comece pelo diff. Inspecione código, testes, contratos, schemas, migrations, configuração, flags, observabilidade, CI e generated code afetados. Relacione alterações a `TASK-*`, requirements e acceptance criteria.
4. Classifique a readiness como `VERIFICATION_CONTEXT_UNRESOLVED`, `READY_FOR_VERIFICATION` ou `VERIFICATION_COMPLETE`. Se uma dúvida alterar o verdict, faça 1 a 4 perguntas objetivas somente após consultar as fontes.
5. Leia [references/compliance-model.md](references/compliance-model.md) e [references/evidence-guidance.md](references/evidence-guidance.md). Verifique cada requirement e acceptance criterion relevante com evidência direta; teste passando é evidência, não prova absoluta.
6. Registre findings rastreáveis com ID `IV-*`, severidade, categoria, requirement, evidência, impacto, ação e status. Não infle severidade.
7. Em brownfield, leia [references/brownfield-verification.md](references/brownfield-verification.md). Em migration, leia [references/migration-verification.md](references/migration-verification.md).
8. **Hard gate:** nunca emita `COMPLIANT` com pergunta `BLOCKING`, conflito material, requirement crítico sem evidência suficiente ou `HIGH` aberto que invalide comportamento crítico.
9. Quando útil, crie ou atualize `docs/changes/<change-id>/VERIFICATION.md`, preservando IDs. Não sobrescreva `REVIEW.md` nem crie `VERIFICATION-v2.md` sem necessidade.
10. Por padrão, verifique sem corrigir. Se o usuário pedir verificação e correção, conclua e registre findings primeiro; separe remediation e encaminhe à skill adequada antes de editar.

## Limites

- Não aceite SPEC, REVIEW, ARCHITECTURE, ADR, PLAN, TEST-PLAN, testes ou relato da implementação como verdade absoluta. Compare intenção, evidência e realidade.
- Não invente requirements, comportamento esperado, métricas, constraints, limites ou resultado de teste. Use `VERIFICATION_OPEN_QUESTION` quando faltar definição.
- Não escolha silenciosamente entre fontes conflitantes. Registre `VERIFICATION_CONTEXT_CONFLICT`; ADR `Proposed` não é decisão confirmada sem evidência formal.
- Diferencie `OBSERVED IMPLEMENTATION BEHAVIOR` de `CONFIRMED EXPECTED BEHAVIOR`, `PREEXISTING_FAILURE` de `REGRESSION` e detalhe local de desvio material.
- Não declare `PASS` apenas porque código existe ou teste passa. Confirme cobertura, assertions, mocks, completion criteria e ausência de enfraquecimento relevante.
- Não altere código, testes ou documentos silenciosamente durante verification.
- Escreva no idioma do usuário, salvo convenção aplicável. Preserve IDs e cite paths, comandos e resultados reais.

Consulte [references/verification-scenarios.md](references/verification-scenarios.md) para os cenários normativos.
