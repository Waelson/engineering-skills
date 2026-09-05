# Processo de Bootstrap

## Repository Discovery

Inspecione primeiro as fontes de maior sinal:

- `AGENTS.md`, `README.md` e estrutura de `docs/`;
- `Makefile`, `Taskfile`, `package.json`, `go.mod`, `pom.xml`, `build.gradle`, `pyproject.toml` e `Cargo.toml` quando existirem;
- scripts de build, test e lint e configuração de CI relevante;
- diretórios de código apenas o suficiente para entender o tipo e a organização do projeto.

Não execute comandos apenas para provar que estão declarados; valide a origem textual antes de registrá-los. Não transforme presença de uma ferramenta em comando presumido: `go.mod` confirma Go, mas não confirma por si só que `go test ./...` seja a convenção oficial do projeto.

## Classificação do contexto

- `GREENFIELD`: pouca ou nenhuma estrutura de projeto ou documentação estabelecida.
- `BROWNFIELD`: há código, documentação ou convenções operacionais relevantes.
- `PARTIALLY_BOOTSTRAPPED`: já existe `AGENTS.md`, algum diretório SDD ou parte do workflow, mas faltam elementos mínimos.

Use `PARTIALLY_BOOTSTRAPPED` quando a característica dominante for completar preparação existente, mesmo que o projeto também seja brownfield.

## SDD Convention Alignment

Compare o estado encontrado com a convenção SDD. Preserve convenções compatíveis e complete apenas lacunas. Se `design/adr/`, `documentation/` ou outro path já cumprir papel equivalente, não duplique nem mova silenciosamente. Apresente o conflito e peça uma decisão entre:

- preservar a convenção atual e documentar o mapeamento;
- adotar a convenção SDD, com mudança explicitamente autorizada;
- manter ambas com responsabilidades não sobrepostas.

## Readiness

- `BOOTSTRAP_DISCOVERY_REQUIRED`: existe conflito ou informação indispensável ainda sem decisão. Não aplique a parte afetada do bootstrap.
- `READY_FOR_BOOTSTRAP`: há informação suficiente para criar ou ajustar as instruções e diretórios mínimos.
- `SDD_READY`: convenção adotada está documentada, estrutura mínima está preparada e não há conflito bloqueante para iniciar `$spec-author`.

Não exija language, build ou validation commands para `SDD_READY` quando o projeto ainda não os definiu. Exija apenas que o `AGENTS.md` não os invente.

## Comportamento por contexto

### Greenfield

Crie `AGENTS.md`, prepare os diretórios mínimos e registre somente fatos já conhecidos. Não adicione conteúdo de negócio nem escolha stack.

### Brownfield

Reconstrua convenções de fontes reais, preserve documentação existente, atualize instruções incrementalmente e inclua apenas regras de segurança sustentadas pelo projeto. Ausência de `docs/spec/SPEC.md` ou `docs/architecture/ARCHITECTURE.md` não bloqueia.

### Partially bootstrapped

Identifique exatamente o que falta e complete somente isso. Não recrie arquivos nem substitua instruções existentes por um template integral.

## Checkpoint

Quando uma decisão for necessária, consolide:

```text
Entendimento atual do repositório

Contexto: GREENFIELD | BROWNFIELD | PARTIALLY_BOOTSTRAPPED
Já existe:
- ...
Não existe:
- ...
Convenções detectadas e fontes:
- ...
Conflitos:
- ...
Decisão pendente:
- ...
```
