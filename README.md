# Alfa Financeiro - Publicação no GitHub Pages

Sistema interno de controle financeiro da Alfa Contabilidade.

## Publicação

Publique os arquivos desta pasta no repositório do GitHub Pages:

`alfacontabilidadefinanceiro/alfa-financeiro-seguro`

Link esperado do site:

`https://alfacontabilidadefinanceiro.github.io/alfa-financeiro-seguro/`

## Arquivos principais

- `index.html`: sistema financeiro.
- `alfa-logo.png`: logomarca usada no sistema.
- `clientes.json`, `financeiro.json`, `reference-entries.json`: arquivos vazios de referência, sem dados reais.
- `official-data.js` e `official-expenses.js`: arquivos vazios de referência, sem dados reais.
- `LEIA-ANTES-DE-PUBLICAR.txt`: orientação rápida de publicação.
- `CHECKLIST-PUBLICACAO-FINAL.txt`: conferência antes de publicar.

## Atenção de segurança

Não publique dados reais de clientes no GitHub, mesmo que o site tenha login.

Não envie para o repositório:

- planilhas reais;
- backups do sistema;
- extratos bancários;
- CPF/CNPJ de clientes;
- boletos;
- arquivos CSV com cobranças reais;
- chaves PIX privadas;
- senhas;
- arquivos `.env` ou chaves de API privadas.

Os dados lançados dentro do sistema ficam salvos no navegador/localStorage do computador usado. Para dados reais e uso por vários usuários, o ideal é evoluir para banco seguro, regras de acesso e backup controlado.


## V7 - Mês do relatório

Inclui seletor de mês visível no topo e dentro da tela Relatórios, com botões de mês anterior, próximo mês, mês atual e mês com dados.


## V8 - Extrato mensal completo
Incluído relatório de extrato mensal com todas as transações do mês, separando entradas, saídas e valor líquido. Linhas de Saldo Diário do banco são ignoradas para não distorcer os totais.


## V11 - Reclassificação e duplicidades

Esta versão adiciona reclassificação rápida de despesas e bloqueio de lançamentos duplicados na mesma competência, incluindo importações de CSV, extrato e contas a pagar.


## V12 Segurança de publicação

Esta versão inclui marcação `noindex`, política básica de permissões no navegador, checklist de segurança e orientação LGPD. O pacote permanece sem dados reais.

Arquivos adicionados:

- `SEGURANCA-LGPD-ANTES-DE-PUBLICAR.md`
- `CHECKLIST-SEGURANCA-PUBLICACAO.txt`

Atenção: o uso com dados reais deve considerar banco seguro, regras de acesso e backup controlado.

## V18 - Sincronização em nuvem

Esta versão usa Firebase Authentication e Cloud Firestore para salvar os dados na nuvem.
Após login autorizado, clientes, cobranças, pagamentos, despesas, extratos e configurações passam a ser carregados do Firestore.

Para segurança, os dados reais devem ser importados somente dentro do sistema, nunca enviados para o GitHub.
As regras recomendadas estão no arquivo `FIRESTORE-RULES-ALFA-FINANCEIRO.txt`.
