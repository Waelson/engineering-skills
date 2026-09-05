# Engineering Skills

Engineering Skills é um marketplace de plugins do OpenAI Codex voltados a práticas de engenharia de software. Ele distribui workflows reutilizáveis como plugins instaláveis, sem vincular o repositório a uma única metodologia de engenharia.

## Plugins

### sdd

Um toolkit de Spec-Driven Development para preparar trabalhos de software antes da implementação.

Skills disponíveis:

- `spec-author` — transforma problemas, necessidades, funcionalidades e mudanças de software em especificações prontas para implementação.
- `spec-reviewer` — revisa especificações em busca de ambiguidades, lacunas, inconsistências e riscos de implementação.
- `architecture-designer` — transforma specifications maduras em propostas de arquitetura técnica rastreáveis e justificadas.
- `adr-author` — conduz discovery de decisões arquiteturais e registra ADRs rastreáveis com o status apropriado.

## Instalação

Adicione este repositório como um marketplace do Codex:

```bash
codex plugin marketplace add Waelson/engineering-skills --ref main
```

Instale o plugin `sdd` a partir do marketplace `engineering-skills`:

```bash
codex plugin add sdd@engineering-skills
```

Verifique o marketplace configurado e o plugin:

```bash
codex plugin marketplace list
codex plugin list --marketplace engineering-skills
```

Os comandos acima seguem a sintaxe disponibilizada pela versão atual da CLI do Codex. Após a instalação, inicie uma nova tarefa no Codex para que as novas skills sejam carregadas.

## Uso

Invoque a skill explicitamente em um prompt do Codex:

```text
Use $spec-author para criar uma especificação para um MCP Registry distribuído.
```

A skill cria ou atualiza uma especificação, como `SPEC.md`; ela não implementa o software.

## Licença

Este projeto é licenciado sob a Licença MIT. Consulte o arquivo [LICENSE](LICENSE).
