# {{PROJETO}}

> ⚠️ Projeto recém-criado a partir do **claude-template**.
> Rode **`/bootstrap-projeto`** para preencher este arquivo (contexto, stack, convenções,
> deploy) e gerar as skills/subagents sob medida. Apague este aviso depois.

## Visão geral
{{DESCRICAO_CURTA}}

## Estrutura do repositório
{{ESTRUTURA}}

## Convenções inegociáveis
- {{CONVENCAO_1}}
- **Git**: desenvolva em branch de feature; nunca push direto na branch principal;
  **nunca abra PR sem o usuário pedir**.
- **Antes de commitar**: rode {{COMANDO_TESTE}} e {{COMANDO_BUILD}}.

## Testes / build
{{COMANDOS}}

## Deploy / infra
{{DEPLOY}}

## Skills e subagents
- Skills em `.claude/skills/`. Subagents em `.claude/agents/`.
