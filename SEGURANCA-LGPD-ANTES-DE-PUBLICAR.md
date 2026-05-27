# Segurança e LGPD - Alfa Financeiro

## Publicação no GitHub Pages

Este pacote foi preparado para publicação sem dados reais de clientes. Antes de publicar, confira:

1. Publique somente os arquivos extraídos deste pacote.
2. Não envie ZIP, RAR, PDF, planilhas, extratos, boletos, XML, guias, backups ou arquivos de clientes para o repositório.
3. Os arquivos `clientes.json`, `financeiro.json`, `reference-entries.json`, `dados.csv` e `cobrancas.csv` devem permanecer vazios ou apenas como modelo.
4. O repositório público permite que qualquer pessoa veja os arquivos do projeto. Portanto, nenhum dado sensível deve ficar no código.
5. Teste o acesso em aba anônima: sem login, o sistema não deve liberar o painel.

## Limitação importante

A versão atual salva os lançamentos no navegador/localStorage do computador usado. Isso ajuda nos testes, mas não substitui banco de dados seguro, backup controlado e regras de permissão.

Para uso definitivo com dados reais, recomenda-se evoluir para:

- Firebase/Firestore com regras de segurança;
- liberação somente para e-mails autorizados;
- bloqueio de cadastro público;
- backup automático;
- histórico de alterações;
- perfis de usuário;
- política de retenção de dados;
- rotina de exportação mensal.

## Rotina segura de uso

1. Usar dados fictícios para teste.
2. Validar relatórios, duplicidades e reclassificações.
3. Importar base real somente no ambiente definitivo.
4. Fazer backup mensal.
5. Remover arquivos baixados de computadores compartilhados.
6. Usar senha forte e autenticação em dois fatores nas contas do Google/GitHub.
