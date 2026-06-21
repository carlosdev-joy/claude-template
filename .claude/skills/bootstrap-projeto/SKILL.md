---
description: >
  Inicializa a estrutura de agentes de um projeto novo a partir do claude-template.
  Use logo após copiar o template para um repositório, ou quando o usuário disser
  "bootstrap", "configurar projeto", "inicializar agentes", "preparar skills". Detecta a
  stack, conduz uma entrevista (contexto, forma de trabalho, infra, automação) e gera
  CLAUDE.md, skills e subagents sob medida.
---

# Bootstrap de projeto

Transforme este template genérico na configuração específica do projeto. Princípio:
**detecte o que der; só pergunte o que não dá para inferir.** Pergunte em blocos curtos
(use `AskUserQuestion`) e confirme o que detectou em vez de perguntar do zero.

## Passo 1 — Detecção automática
Inspecione o repo e anote o que encontrar (não pergunte isto):
- **Stack**: `package.json`, `requirements.txt`/`pyproject.toml`, `go.mod`, `pom.xml`,
  `Gemfile`, `Cargo.toml`, `composer.json`.
- **Frontend**: `vite`, `next`, `react`, `vue`, `angular`, `tailwind.config.*`.
- **Backend/framework**: fastapi, django, flask, express, nestjs, spring, rails…
- **Banco/migrations**: `sql/migrations`, `prisma/`, `alembic/`, `db/migrate`, `supabase/`.
- **Infra**: `Dockerfile`, `docker-compose*.y*ml`, `.github/workflows`, `k8s/`,
  `terraform/`, `serverless.yml`, `vercel.json`, `fly.toml`.
- **Testes/build**: scripts de `package.json`, `pytest.ini`, `Makefile`, `tox.ini`.

## Passo 2 — Entrevista (só o que faltar)
Cubra estes blocos. Adapte as opções ao que detectou.

**A. Contexto & negócio** — nome do projeto, domínio/negócio, objetivo principal,
idioma da documentação.

**B. Stack & estrutura** — confirme backend/frontend/banco detectados; onde ficam
código, testes, migrations e artefatos de build.

**C. Forma de trabalho** — estratégia de branch; **política de PR** (o agente pode abrir
sozinho ou só quando pedido?); convenção de commit; quem/como revisa.

**D. Qualidade** — comandos reais de teste/lint/build; padrões obrigatórios (ex.: tema
claro/escuro, acessibilidade, lint, cobertura mínima); o que **nunca** fazer.

**E. Dados & migrations** — como migrations são criadas/versionadas/aplicadas;
idempotência; ambientes; ferramenta (alembic/prisma/sql puro…).

**F. Infra & deploy** — como sobe (script/pipeline/CI-CD); ambientes (dev/staging/prod);
provedor/infra (Docker, k8s, serverless, Supabase/AWS/GCP/on-prem); riscos conhecidos;
gestão de segredos (nunca commitar segredo).

**G. Automação & agentes** —
- Quais **skills** automatizar? (deploy, nova-migration, release, backlog, revisão-pr…)
- Quais **subagents de negócio** criar? Para cada um: área/domínio, e as **regras e
  situações específicas** que ele deve conhecer para garantir qualidade.
- Vai usar **backlog em banco**? Qual conexão/tabela?

## Passo 3 — Gerar a configuração
1. **CLAUDE.md**: preencha `reference/CLAUDE.template.md` (substitua todos os `{{…}}`)
   e escreva na raiz como `CLAUDE.md`. Mantenha < ~150 linhas; aponte docs longos com `@`.
2. **Skills**: para cada automação escolhida, crie `.claude/skills/<nome>/SKILL.md` a
   partir de `reference/skill.template.md`, com os **comandos reais** do projeto. Adapte
   as skills genéricas já presentes (`nova-migration`, `deploy`, `revisao-pr`) ou remova
   as que não se aplicam.
3. **Subagents**: para cada área, crie `.claude/agents/<nome>.md` a partir de
   `reference/agent.template.md`, preenchendo regras e situações específicas. Prefixe com
   o nome do projeto (ex.: `meuapp-backend`) para evitar colisão entre projetos.
4. **Guards**: confirme que `.gitignore` versiona `.claude/skills`,`/agents`,`/commands`
   (e ignora `*.local.json`) e que `.dockerignore` exclui `.claude/` e `CLAUDE.md`
   (este template já vem com ambos — só ajuste se o projeto tiver convenção própria).
5. **Backlog (opcional)**: se escolhido, crie a tabela/migration no padrão do projeto e a
   skill `/backlog` (registrar item + gerar script). Use a conexão informada.
6. **Infra (opcional)**: se o usuário pediu automação de infra, registre como skill os
   passos reais (provisionar, migrar, subir) e os riscos no agente de deploy.

## Passo 4 — Resumo & validação
- Liste os arquivos criados e as decisões tomadas.
- Rode os comandos de teste/build informados para validar.
- Remova exemplos genéricos do template que não se aplicam.
- Lembre: **nunca abra PR sem o usuário pedir**; **nunca** commite segredo.

Ao final, o projeto fica auto-explicável: qualquer sessão nova herda o `CLAUDE.md`, as
skills e os subagents — sem reexplicação.
