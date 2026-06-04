# Revisão V60 - Conferência clientes x contas a receber

## Problema analisado
O sistema pode exibir 77 clientes cadastrados e 70 contas a receber porque os números medem coisas diferentes:

- Clientes cadastrados: quantidade de registros no cadastro mestre de clientes.
- Contas a receber: quantidade de títulos/parcelas/lançamentos financeiros em aberto ou conforme filtro aplicado.

A diferença pode ser normal quando há clientes inativos, sem honorário mensal, com cobrança já paga/bonificada, sem início de cobrança para a competência selecionada, ou com mensalidade ainda não gerada.

## Correção funcional criada
Foi adicionada uma conferência na aba Contas a receber:

- Competência analisada.
- Clientes ativos com honorário esperado.
- Títulos em aberto encontrados.
- Clientes pagos/bonificados.
- Clientes sem título gerado.

## Novos botões
- Conferir clientes sem cobrança.
- Gerar cobranças faltantes.

## Função de diagnóstico no console
alfaConferirClientesReceber()

