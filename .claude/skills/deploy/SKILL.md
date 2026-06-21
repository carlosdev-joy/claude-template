---
description: >
  Roteiro de deploy do projeto. Use quando o usuário pedir "deploy", "subir para produção",
  "roteiro de deploy", "aplicar migrations".
---

# Deploy — {{PROJETO}}

> Adapte no /bootstrap-projeto ao deploy real ({{COMO_DEPLOY}}).

## Antes
- Estado saudável dos serviços; backup antes de migrations; janela segura.

## Aplicar
1. **Migrations primeiro** (se houver): {{COMO_APLICA_MIGRATION}}.
2. **App**: {{COMANDO_DEPLOY}} (ambientes: {{AMBIENTES}}).

## Riscos
- {{RISCOS}}. Nunca exponha segredos.

## Validar pós-deploy
- {{HEALTHCHECK}}; fumaça nas telas/endpoints alterados.
