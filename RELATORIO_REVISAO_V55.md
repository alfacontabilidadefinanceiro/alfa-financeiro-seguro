# ALFA Financeiro V55 - Correção definitiva da edição de clientes

## Ajustes aplicados

1. Refeito o fluxo do botão **Editar cadastro** na aba Clientes.
2. O editor agora localiza o cliente por índice visível, ID, chave, CPF/CNPJ ou nome.
3. O botão de edição não depende mais do bloqueio visual de `data-permission`; a permissão é validada dentro da função de edição, com aviso claro.
4. O modal de cliente é aberto diretamente e recebe reforço de `display:flex`, `z-index` e rolagem.
5. O salvamento de edição agora identifica o cadastro existente por ID, chave original ou CPF/CNPJ, evitando duplicidade e permitindo atualização correta.
6. O valor mensal passou a aceitar formatos como `422`, `422,00` e `R$ 422,00`.

## Teste obrigatório

1. Publicar o novo `index.html`.
2. Limpar cache com Ctrl+F5 ou abrir aba anônima.
3. Acessar Clientes.
4. Clicar em **Editar cadastro**.
5. Alterar telefone ou observações.
6. Salvar.
7. Conferir se o cliente foi atualizado na lista sem duplicar.
