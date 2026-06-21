---
description: >
  Checklist de qualidade antes de commitar/abrir PR. Use quando o usuário pedir "revisar",
  "checklist", "antes do PR", "validar mudanças".
---

# Revisão de qualidade — {{PROJETO}}

Rode e reporte cada item. **Não abra PR sem o usuário pedir.**

- [ ] Testes passam: `{{COMANDO_TESTE}}` (sem novas falhas).
- [ ] Build passa: `{{COMANDO_BUILD}}`.
- [ ] Lint/format: `{{COMANDO_LINT}}`.
- [ ] Migrations idempotentes e leitura degrada se a tabela não existir.
- [ ] Padrões obrigatórios atendidos: {{PADROES_QUALIDADE}}.
- [ ] Branch de feature (não a principal); commit no estilo do projeto.
- [ ] Sem segredos no diff.

Conclua: pronto para commit, ou lista de pendências.
