# Catálogo — skills e subagents do template

Menu do que o `/bootstrap-projeto` pode ativar/gerar. Marque o que se aplica ao projeto
e remova o resto.

## Skills (em `.claude/skills/`)
| Skill | O que faz | Quando ativar |
|---|---|---|
| `bootstrap-projeto` | Entrevista + geração inicial | sempre (1ª execução) |
| `nova-migration` | Cria migration no padrão | projeto com banco/migrations |
| `deploy` | Roteiro de deploy + migrations | projeto com deploy próprio |
| `revisao-pr` | Checklist de qualidade pré-PR | sempre recomendado |
| `backlog` | Registra item + gera script | se for usar backlog |

### Opcionais que o bootstrap pode criar sob demanda
- `release-notes` — changelog/notas de versão a partir dos commits.
- `nova-feature` — scaffold de endpoint/módulo + teste no padrão.
- `seed-dados` — popular dados de exemplo/ambiente.

## Subagents (em `.claude/agents/`)
| Agent | Papel | Tools típicas |
|---|---|---|
| `backend` | implementa backend/API/migrations | Read, Grep, Glob, Edit, Bash |
| `frontend` | telas/componentes/tema | Read, Grep, Glob, Edit, Bash |
| `deploy` | planeja/valida deploy e infra | Read, Grep, Glob, Bash |
| `reviewer` | gate de qualidade (read-only) | Read, Grep, Glob, Bash |

### De negócio (criar conforme o domínio)
Um por área crítica do produto (ex.: integração X, processamento Y), com as **regras e
situações específicas** que garantem qualidade. Base: `skills/bootstrap-projeto/reference/agent.template.md`.

## Built-ins do Claude (sem precisar criar)
`/code-review` · `/security-review` · `/verify` — já disponíveis.

## Config & automação
- `.claude/settings.json` — allowlist de permissões + `env` (afine com `/update-config`).
- `scripts/setup.sh` — setup p/ sessões na web (ligue via `/session-start-hook`).
- `.claude/rules/*.md` — regras escopadas por path (carregam só onde importam).

## Convenções inegociáveis (herdadas)
- Cores de paleta sempre com par claro/escuro (se houver UI).
- Migrations idempotentes; leitura degrada se a tabela não existir.
- **Nunca abrir PR sem o usuário pedir**; **nunca** commitar segredo.
- `.claude/` e `CLAUDE.md` ficam só no repo (guards de `.gitignore`/`.dockerignore`).
