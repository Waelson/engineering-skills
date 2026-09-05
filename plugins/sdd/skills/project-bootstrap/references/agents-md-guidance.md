# Orientação para AGENTS.md

## Finalidade

`AGENTS.md` registra instruções estáveis e acionáveis para agentes que trabalham no repositório. Por padrão, use o arquivo na raiz. Leia e preserve um arquivo existente; faça alterações incrementais e evite duplicar regras semanticamente equivalentes.

## Estrutura adaptativa

Inclua somente seções com conteúdo real:

```markdown
# Project Agent Instructions

## SDD Workflow

project-bootstrap
→ spec-author
→ spec-reviewer
→ architecture-designer
→ adr-author
→ implementation-planner
→ test-designer
→ implementação
→ implementation-verifier

## Documentation Structure

- `docs/spec/SPEC.md`: baseline vigente do sistema.
- `docs/changes/<change-id>/SPEC.md`: specification de uma mudança.
- `docs/changes/<change-id>/REVIEW.md`: review da mudança.
- `docs/changes/<change-id>/ARCHITECTURE.md`: arquitetura proposta da mudança.
- `docs/architecture/ARCHITECTURE.md`: arquitetura baseline vigente.
- `docs/architecture/adr/`: ADRs.

## General Agent Rules

## Project Conventions

## Validation Commands

## Change Safety Rules
```

Adapte títulos e idioma à convenção do projeto. Não cite como disponíveis skills ainda não instaladas ou não adotadas pelo projeto; quando o workflow futuro for declarado pelo usuário, ele pode ser documentado como sequência pretendida.

## Regras gerais estáveis

Registre, quando compatíveis com o projeto:

- não inventar requirements nem transformar assumptions em fatos;
- fazer discovery diante de ambiguidade material;
- consultar contexto existente antes de perguntar;
- preservar IDs de requirements quando possível;
- respeitar ADRs vigentes;
- não atualizar baseline automaticamente a partir de change ativa;
- respeitar convenções específicas do projeto.

## Project conventions e validação

Registre linguagem, módulo, layout, build, test e lint somente com evidência. Cite os comandos exatos declarados pelo projeto, sem acrescentar alternativas genéricas. Se não houver comando confiável, omita a seção ou declare concisamente que ainda não foi definido; pergunte somente se o dado for necessário ao trabalho imediato.

## Change safety

Em brownfield, inclua regras como preservar compatibilidade, inspecionar testes, respeitar contratos públicos, não editar arquivos gerados ou não alterar migrations aplicadas somente quando a documentação, configuração ou estrutura do projeto realmente as sustentar.

## Conteúdo proibido

Não inclua feature requirements, backlog, decisões temporárias, open questions de uma change, architecture design detalhado, implementation plan ou informação especulativa. Detalhes extensos pertencem aos documentos específicos.
