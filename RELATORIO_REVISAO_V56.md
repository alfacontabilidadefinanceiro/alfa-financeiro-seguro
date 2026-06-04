# Alfa Financeiro V56 - Correção do salvamento de cliente

## Correção principal

Foi corrigido o erro que podia impedir o botão **Salvar cliente** de concluir a edição. O problema técnico era uma chamada a `formatCurrency(...)`, função inexistente no arquivo. Quando o sistema detectava possível duplicidade de cliente, o JavaScript travava antes de salvar.

Correção aplicada:

- `formatCurrency(client.monthlyFee)` substituído por `formatMoney(client.monthlyFee)`.
- `saveClientForm` passou a ter tratamento de erro com alerta técnico.
- Botão `Salvar cliente` recebeu `id="saveClientBtn"` e chamada direta de salvamento.
- Campo de honorário mensal passou de `type="number"` para `type="text" inputmode="decimal"`, aceitando `422`, `422,00` e `R$ 422,00`.
- Após salvar localmente, o sistema tenta sincronizar imediatamente com o Firestore.

## Como testar

1. Publicar o `index.html` desta versão.
2. Abrir o navegador e pressionar `Ctrl + F5`.
3. Entrar como administrador.
4. Abrir **Clientes**.
5. Clicar em **Editar cadastro**.
6. Alterar telefone/observação/honorário.
7. Clicar em **Salvar cliente**.
8. Conferir se o modal fecha, aparece mensagem de sucesso e a lista atualiza.

## Diagnóstico no navegador

No console, pode executar:

```js
alfaDiagnosticoSalvarCliente()
```

Ele mostra se o usuário tem permissão, se o modal está aberto, dados carregados e se a nuvem está pronta para escrita.
