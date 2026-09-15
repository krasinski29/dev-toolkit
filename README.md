# dev-toolkit

Skills e templates reutilizáveis de workflow — gestão de projetos, integrações (ex: Linear) e outras práticas usadas entre projetos diferentes.

## Estrutura

- `skills/` — skills globais do Claude Code (ex: interação com Linear, gestão de projetos). Pensadas para uso via symlink em `~/.claude/skills`.
- `templates/` — modelos genéricos reutilizáveis entre projetos (ex: estrutura inicial de um projeto novo, checklists de setup). Documentação específica de um projeto continua no próprio repo daquele projeto.

## Uso

```bash
ln -s ~/Dev/dev-toolkit/skills ~/.claude/skills
```
