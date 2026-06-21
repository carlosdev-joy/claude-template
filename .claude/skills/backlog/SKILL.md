---
description: >
  Registra itens de backlog do projeto e gera o script de criação automaticamente.
  Use para "anotar no backlog", "registrar ideia", "criar tarefa", "gerar script de backlog".
argument-hint: "registrar|listar|gerar-script <texto>"
---

# Backlog — {{PROJETO}}

Mantém o backlog em {{BACKLOG_DESTINO}} (ex.: tabela no banco do projeto, ou arquivo
versionado). Defina o destino e a conexão no `/bootstrap-projeto`.

- **registrar**: extrai título/tipo/área/prioridade do pedido e grava o item
  (INSERT idempotente / endpoint / arquivo). Confirma o id criado.
- **listar**: mostra o backlog por status/prioridade.
- **gerar-script**: a partir de um item "refinado", cria o esqueleto da entrega
  (migration + módulo + teste) já preenchido com título/descrição, no padrão do projeto.

Regras: nunca inventa schema; segue a numeração e o padrão idempotente do projeto.
Campos sugeridos: id, titulo, descricao, tipo (feature|bug|debt|spike), area,
prioridade (P0..P3), status (ideia|refinado|em_andamento|concluido|descartado),
origem, ref_pr, criado_em.
