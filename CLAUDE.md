# CLAUDE.md

Guia para qualquer sessão Claude Code trabalhando neste repositório.
Documenta *decisões já tomadas*, não intenções — mantenha em sincronia
com a realidade.

## O que é este repositório

`dev-toolkit` guarda skills e templates **reutilizáveis entre projetos**.
O critério de entrada é esse: o que serve a um projeto só continua no
repositório daquele projeto.

## O symlink, e o que ele implica

`skills/` é symlinkado para `~/.claude/skills`:

```bash
ln -s ~/dev/dev-toolkit/skills ~/.claude/skills
```

Três consequências que mudam como se trabalha aqui:

- **Toda skill daqui fica ativa em todos os projetos.** Não existe
  rascunho local — o que entra aqui passa a competir por gatilho em
  qualquer sessão, em qualquer repositório.
- **Mudança só vale a partir da próxima sessão.** A lista de skills é
  montada quando a sessão começa; editar um `SKILL.md` não afeta a
  sessão em andamento. Não conclua que a edição falhou por não ver
  efeito imediato.
- **Nome de skill é espaço global.** Antes de criar uma, confira que o
  nome não colide com skill de plugin (`anthropic-skills:...`) nem com
  skill de projeto em `.claude/skills/`.

## Criar ou editar uma skill

- **Use a skill `skill-architect`** (`skills/skill-architect/`). Ela
  obriga a passar por Discovery e Architecture antes de escrever
  qualquer `SKILL.md`. Não escreva um na mão.
- **Valide antes de commitar**:

  ```bash
  python3 skills/skill-architect/scripts/validate_skill.py skills/<nome>
  ```

- **Frontmatter**: `name`, `description`, `license: CC-BY-4.0`, e
  `metadata` com `author` e `version`. A regra de quando incrementar a
  versão está em `~/.claude/CLAUDE.md`, porque vale também para as
  skills que moram dentro de projetos.
- **A `description` decide tudo.** É o único campo que o modelo lê para
  escolher a skill. Precisa de frases-gatilho reais — em português, que
  é como elas são invocadas — e de um `Do NOT use for...`. Sem escopo
  negativo, as skills começam a pisar umas nas outras conforme o número
  cresce.

## Skills de terceiros

`skill-architect` veio de `tech-leads-club/agent-skills` e carrega um
`.skill-meta.json` com hash de conteúdo e data de download. Editar uma
skill importada cria um fork local: a partir daí, atualizar upstream
deixa de ser um download limpo e vira merge manual. Prefira abrir issue
no upstream a divergir em silêncio.
