# Revisão V61 - Conferência real de clientes x contas a receber

## Problema informado
Na tela Contas a receber, ao usar os filtros, apareceram apenas 2 clientes/títulos, gerando dúvida porque existem 77 clientes cadastrados e 70 contas a receber.

## Diagnóstico técnico
1. O total de clientes cadastrados não precisa ser igual ao total de contas a receber.
   - Clientes podem estar inativos, sem honorário, com cobrança paga/bonificada, fora da competência selecionada ou sem título gerado.
2. Havia um problema técnico importante: as telas Contas a receber e Contas a pagar ainda usavam `filteredEntries("receita")` e `filteredEntries("despesa")` como base.
   - Essa função lê filtros da aba Lançamentos (`searchInput`, `typeFilter`, `statusFilter`).
   - Na prática, um filtro antigo/escondido da aba Lançamentos poderia reduzir indevidamente a lista de A receber/A pagar.
3. O painel de conferência de clientes x contas a receber estava disponível no código, mas não aparecia corretamente dentro da aba Contas a receber.

## Correções aplicadas
1. Criada a função `accountEntriesByType(type)` para que Contas a receber e Contas a pagar usem base própria, independente da aba Lançamentos.
2. Contas a receber agora usa `accountEntriesByType("receita")`.
3. Contas a pagar agora usa `accountEntriesByType("despesa")`.
4. Adicionado painel visível na aba Contas a receber: `Conferência da competência selecionada`.
5. Adicionado resumo por competência, exibindo por mês:
   - clientes esperados;
   - títulos existentes;
   - títulos em aberto;
   - pagos/bonificados;
   - clientes sem título.
6. Os botões `Conferir clientes` e `Gerar cobranças faltantes` foram ligados na aba Contas a receber.
7. O filtro de competência passou a mostrar contagem no próprio select, por exemplo: `06/2026 - 70 registro(s)`.

## Como validar
1. Abrir Contas a receber.
2. Clicar em Limpar filtros.
3. Conferir o select Competência.
4. Escolher 05/2026, 06/2026, 07/2026.
5. Verificar o quadro de resumo por competência.
6. Clicar em Conferir clientes.
7. Gerar cobranças faltantes apenas se a conferência indicar clientes ativos sem título.
