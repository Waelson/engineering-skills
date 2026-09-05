---
name: project-bootstrap
description: Prepare repositórios greenfield, brownfield ou parcialmente configurados para o workflow SDD, criando ou ajustando instruções estáveis em AGENTS.md e a estrutura documental mínima. Use para bootstrap SDD, preparar AGENTS.md, inicializar diretórios de documentação ou alinhar um projeto existente às convenções SDD. Não use para criar specifications, reviews, arquitetura, ADRs, planos, testes ou código.
---

# Bootstrap de Projeto SDD

Prepare o repositório para iniciar o workflow SDD sem produzir artefatos das etapas posteriores. Trabalhe em três fases: **Repository Discovery → SDD Convention Alignment → Bootstrap**. O resultado deve permitir que `$spec-author` trabalhe em seguida.

## Fluxo de trabalho

1. Leia todos os `AGENTS.md` aplicáveis e inspecione proporcionalmente a raiz, `README.md`, documentação, manifests, arquivos de build, scripts e CI relevantes. Não varra o repositório inteiro sem necessidade.
2. Leia integralmente [references/bootstrap-process.md](references/bootstrap-process.md). Classifique o contexto como `GREENFIELD`, `BROWNFIELD` ou `PARTIALLY_BOOTSTRAPPED` e a readiness como `BOOTSTRAP_DISCOVERY_REQUIRED`, `READY_FOR_BOOTSTRAP` ou `SDD_READY`.
3. Descubra convenções reais: estrutura documental, linguagem, módulos, comandos de build, teste e lint, contratos, arquivos gerados e regras de segurança para mudanças. Cite a fonte; ausência de evidência não autoriza inferência.
4. Leia [references/sdd-directory-convention.md](references/sdd-directory-convention.md). Compare a estrutura existente com a convenção SDD. Se houver conflito material, explique-o e pergunte se deve preservar, adotar ou mapear as convenções; não mova arquivos automaticamente.
5. Faça normalmente 2 a 5 perguntas de alto impacto por rodada somente quando conflitos ou informações necessárias não puderem ser resolvidos pelas fontes. Não pergunte stack ou comandos se eles não forem necessários para um bootstrap responsável.
6. Ao atingir `READY_FOR_BOOTSTRAP`, leia [references/agents-md-guidance.md](references/agents-md-guidance.md). Crie `AGENTS.md` na raiz ou atualize-o incrementalmente, preservando conteúdo e regras existentes compatíveis.
7. Crie somente os diretórios SDD que faltarem. Como Git não versiona diretórios vazios, adicione um `.gitkeep` em cada diretório novo apenas quando a preparação precisar persistir no repositório; não trate esse marcador como artefato SDD.
8. Verifique que nenhuma specification, review, arquitetura, ADR, plano ou código foi criado; valide que instruções e comandos registrados possuem evidência e que convenções existentes não foram sobrescritas silenciosamente.
9. Classifique como `SDD_READY` quando `AGENTS.md` documentar as convenções mínimas adotadas e a estrutura necessária estiver preparada. Recomende `$spec-author` como próxima etapa, sem executar seu papel.

## Limites

- Não crie `SPEC.md`, `REVIEW.md`, `ARCHITECTURE.md`, `ADR-*.md`, `IMPLEMENTATION-PLAN.md` ou `TEST-PLAN.md`.
- Não crie nem altere código de aplicação, serviços, handlers, dependências, migrations, contratos ou arquitetura.
- Não invente linguagem, framework, módulo, comandos, paths especiais, branch strategy, deployment model, owners, requirements ou convenções.
- Registre somente comandos confirmados por manifests, arquivos de build, scripts, CI ou confirmação do usuário. Se necessários e desconhecidos, pergunte; caso contrário, indique que não estão definidos.
- Um `AGENTS.md` contém apenas regras estáveis para agentes. Não inclua requisitos da change atual, backlog, decisões temporárias, open questions de feature, design detalhado ou plano de implementação.
- Em brownfield, não sobrescreva `AGENTS.md`, não mova documentação e não normalize convenções existentes sem confirmação. Faça merge mínimo e compatível.
- A ausência de baseline ou arquitetura baseline não bloqueia o bootstrap e não autoriza criar arquivos vazios dessas etapas.
- Escreva no idioma do usuário, salvo solicitação explícita ou convenção documental aplicável.

Consulte [references/bootstrap-scenarios.md](references/bootstrap-scenarios.md) para os cenários normativos.
