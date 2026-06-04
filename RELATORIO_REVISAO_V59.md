# RELATÓRIO TÉCNICO V59 — Filtros por competência em lançamentos, a receber e a pagar

## Escopo do ajuste
- Adicionado filtro por **Competência** em Lançamentos.
- Mantido e revisado filtro por **Competência** em Contas a receber.
- Adicionado filtro por **Competência** em Contas a pagar.
- Adicionado botão **Limpar filtros** em Lançamentos.
- As tabelas de Lançamentos, Contas a receber e Contas a pagar agora exibem a coluna **Competência**.

## Testes executados
- OK: JavaScript sem erro de sintaxe
- OK: ID existe: entryCompetenceFilter
- OK: ID existe: receivableCompetenceFilter
- OK: ID existe: payableCompetenceFilter
- OK: ID existe: entryClearFiltersBtn
- OK: ID existe: receivableClearFiltersBtn
- OK: ID existe: payableClearFiltersBtn
- OK: ID existe: entryRows
- OK: ID existe: receberRows
- OK: ID existe: pagarRows
- OK: Nenhum getElementById sem elemento HTML
- OK: Função ligada: updateEntryCompetenceOptions(base)
- OK: Função ligada: updatePayableCompetenceOptions(list)
- OK: Função ligada: updateReceivableCompetenceOptions(list)
- OK: Função ligada: entryMatchesCompetenceSelect(entry, competenceId)
- OK: Função ligada: entryMatchesListCompetenceFilter(entry)
- OK: Limpar filtros conectado: entryClearFiltersBtn
- OK: Limpar filtros conectado: receivableClearFiltersBtn
- OK: Limpar filtros conectado: payableClearFiltersBtn
- OK: Lançamentos mostra Competência
- OK: A receber mostra Competência
- OK: A pagar mostra Competência
- OK: Lógica: a receber 05/2026 aberto
- OK: Lógica: a receber 06/2026 aberto
- OK: Lógica: a pagar 07/2026 aberto
- OK: Lógica: lançamentos 06/2026 todos

## Observação honesta
Os testes foram feitos por validação estática e lógica local do arquivo `index.html`. Não houve acesso ao seu Firestore real neste ambiente. Após publicar, deve ser feito teste operacional com o usuário administrador no navegador.