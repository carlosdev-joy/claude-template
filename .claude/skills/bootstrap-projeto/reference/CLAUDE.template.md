# {{PROJETO}}

{{DESCRICAO_CURTA}}  ·  Stack: {{STACK}}.

## Estrutura do repositório
- {{DIR_BACKEND}} — {{BACKEND_DESC}}
- {{DIR_FRONTEND}} — {{FRONTEND_DESC}}
- {{DIR_MIGRATIONS}} — migrations ({{MIGRATION_TOOL}})
- {{DIR_TESTES}} — testes
- `docs/` — base de conhecimento; `scripts/` — automações

## Convenções inegociáveis
- **Migrations**: {{REGRA_MIGRATION}} (idempotentes; aplicadas via {{COMO_APLICA_MIGRATION}}).
- {{CONVENCAO_CODIGO}} (ex.: padrão de import, registro de módulo, estilo de UI).
- **Git**: branch de feature; nunca push direto na `{{BRANCH_PRINCIPAL}}`;
  **{{POLITICA_PR}}**. Commits {{ESTILO_COMMIT}}.
- **Antes de commitar**: `{{COMANDO_TESTE}}` e `{{COMANDO_BUILD}}`.

## Padrões por área
- Backend: {{PADRAO_BACKEND}}
- Frontend: {{PADRAO_FRONTEND}}
- Qualidade obrigatória: {{PADROES_QUALIDADE}}

## Deploy / infra
- Como sobe: {{COMO_DEPLOY}} (ambientes: {{AMBIENTES}}).
- Infra: {{INFRA}}. Riscos: {{RISCOS}}. Segredos: {{GESTAO_SEGREDOS}}.

## Testes
- `{{COMANDO_TESTE}}` ({{NOTA_TESTES}}).

## Skills e subagents
- Skills: {{LISTA_SKILLS}}.
- Subagents: {{LISTA_AGENTS}}.

## Mais contexto (sob demanda)
{{IMPORTS_DOCS}}
