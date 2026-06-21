# claude-template

Template de **estrutura de agentes (Claude Code)** para iniciar qualquer projeto com
padrões, qualidade e automação — sem ter que reexplicar o projeto a cada sessão.

Fornece: `CLAUDE.md` (memória), `.claude/skills/` (procedimentos), `.claude/agents/`
(subagents de negócio) e os _guards_ de `.gitignore`/`.dockerignore` (a estrutura fica
só no repo, fora do deploy).

## Como usar num projeto novo

1. **Copie** o conteúdo deste template para a raiz do repositório novo:
   ```bash
   # dentro do repo novo, vazio ou existente
   rsync -a --exclude .git /caminho/do/claude-template/ ./
   #   (traz CLAUDE.md, .claude/, .gitignore, .dockerignore)
   ```
   Ou clone e remova o `.git`:
   ```bash
   git clone <url-do-claude-template> tmp && rm -rf tmp/.git && rsync -a tmp/ ./ && rm -rf tmp
   ```

2. **Abra uma sessão do Claude Code dentro do repo novo** e rode:
   ```
   /bootstrap-projeto
   ```
   Ele **detecta a stack**, faz uma **entrevista** (contexto, forma de trabalho, infra,
   automação) e **gera** o `CLAUDE.md`, as skills e os subagents sob medida — preenchendo
   todos os `{{placeholders}}`.

3. **Revise e commite.** A estrutura passa a valer para toda sessão nova naquele repo,
   isolada de qualquer outro projeto.

## O que vem no template
- `CLAUDE.md` — stub que aponta para o `/bootstrap-projeto`.
- `.claude/skills/bootstrap-projeto/` — a entrevista + geração (com modelos em `reference/`).
- `.claude/skills/{nova-migration,deploy,revisao-pr}/` — skills genéricas, adaptadas no bootstrap.
- `.claude/agents/{backend,reviewer}.md` — subagents genéricos (especializados no bootstrap).
- `.gitignore` / `.dockerignore` — já com os _guards_ corretos.

> Isolamento: cada projeto tem o **seu** `.claude/` no **seu** repo. Nada é compartilhado
> entre projetos a não ser que você publique algo em `~/.claude/` (global da máquina).
