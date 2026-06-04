# Relatório técnico V64 - Baixa manual com data e importação CSV de boletos pagos

## Arquivo CSV testado

Foi testado o arquivo enviado pelo usuário com as seguintes colunas:

- Número da Cobrança
- Valor (R$)
- Status
- Data de Emissão
- Forma de cobrança
- Nome
- E-mail
- Telefone
- Documento
- Data de Vencimento
- Valor Pago (R$)
- Pago Em

## Resultado do reconhecimento do modelo

- Modelo reconhecido como CSV de boletos/cobranças mensais: **SIM**
- Separador reconhecido: **ponto e vírgula `;`**
- Encoding: **UTF-8 com acentuação normal**
- Linhas de dados: **12**
- Linhas pagas ou marcadas como pagas: **12**
- Linhas em aberto no arquivo testado: **0**
- Valor original total: **R$ 4.205,00**
- Valor pago total: **R$ 4.244,55**
- Pagamentos com data “Pago Em” em 05/2026: **12**
- Competências por vencimento: **11 em 05/2026 e 1 em 06/2026**

## Regra implementada

A importação baixa automaticamente somente quando encontra uma parcela já existente no sistema por:

1. Número da cobrança, quando já existir no lançamento;
2. Documento/CNPJ/CPF;
3. Nome aproximado do cliente;
4. Competência pelo vencimento;
5. Valor original da cobrança, com tolerância para diferença de juros/multa no valor pago.

Se o boleto vier pago, mas não existir parcela compatível, o sistema **não cria cliente automaticamente**. Ele lança como **Recebimentos não identificados** para vinculação manual.

## Data do recebimento

A coluna `Pago Em` passa a ser gravada como `paidAt`. Portanto:

- A competência do título continua sendo definida pelo vencimento/competência da parcela;
- O card **Recebido no mês** considera a data real do recebimento (`Pago Em`);
- Exemplo testado: um boleto com vencimento em 06/2026 e pagamento em 31/05/2026 entra no recebido de 05/2026, preservando a competência 06/2026 da cobrança.

## Baixa manual

Também foi adicionada data de recebimento nos controles manuais de baixa:

- Aba Clientes > Baixar honorário;
- Aba Contas a receber > botão ✓;
- Aba Lançamentos > botão ✓ em receitas/despesas abertas.

Agora a baixa não usa obrigatoriamente o dia atual. O usuário informa/seleciona a data do recebimento antes de confirmar.

## Testes executados

- Sintaxe JavaScript validada com `node --check`: **OK**
- Reconhecimento das colunas do CSV enviado: **OK**
- Conversão de valores brasileiros, incluindo `262,99`: **OK**
- Conversão de datas brasileiras, incluindo `27/05/2026`: **OK**
- Status `Pago`: **OK**
- Status `Marcado como pago`: **OK**
- Simulação com parcelas abertas correspondentes: **12 de 12 baixadas**
- Valor pago total simulado: **R$ 4.244,55**
- Preservação da regra de não criar cliente automático: **OK**
