---
description: >
  Cria uma nova migration no padrão do projeto. Use ao adicionar/alterar tabela ou schema,
  ou quando o usuário disser "nova migration", "criar tabela", "alterar schema".
argument-hint: "[nome_curto]"
---

# Nova migration — {{PROJETO}}

> Adapte no /bootstrap-projeto à ferramenta real ({{MIGRATION_TOOL}}: sql puro, alembic, prisma…).

1. **Número/nome**: siga a convenção de `{{DIR_MIGRATIONS}}` (sequência ou timestamp).
2. **Idempotência**: a migration deve ser segura para rodar mais de uma vez
   (ex.: `IF NOT EXISTS` / `CREATE TABLE IF NOT EXISTS` / guardas equivalentes).
3. **Degradação graciosa**: leitura no código degrada se a tabela ainda não existir.
4. **Aplicação**: lembre que roda via {{COMO_APLICA_MIGRATION}} (não automático).
5. **Validação**: `{{COMANDO_TESTE}}`.
