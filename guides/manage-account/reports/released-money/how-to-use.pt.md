# Como usar o relatório?

Quando o relatório estiver pronto e baixado, você terá um arquivo pronto para consultar as planilhas de cálculo e importá-las para o programa que você usa.

Para consultar o relatório, recomendamos baixá-lo em formato .csv para poder abri-lo no programa que possa visualizá-lo. O arquivo deve estar configurado em formato UTF-8 para evitar problemas de leitura.

## O que contém no relatório?

O relatório é composto por:


| Composição do relatório | Descrição |
| --- | --- |
| Initial Available Balance |<br/> Saldo inicial.<br/><br/>|
| Release |<br/>O detalhe das liberações de dinheiro que inclui o saldo inicial.<br/><br/> |
| Block | <br/>Os bloqueios de dinheiro por disputas.<br/><br/> |
| Unblock |<br/> Os desbloqueios após a resolução das disputas.<br/><br/>|
| Subtotal | <br/>É a soma das transações que compõem cada seção.<br/><br/>|
| Total| <br/> É o resultado final composto pela soma de todos os subtotais. <br/><br/>Ou seja:<br/> subtotal `Release` + subtotal `Block` + subtotal `Unblock` = resultado total<br/><br/> |


Além disso, o relatório reflete os conceitos de *débito* (dinheiro a pagar) e *crédito* (dinheiro a receber) em duas colunas, uma para conceito: 


> Seu a ver estará na coluna `NET_CREDIT`
>
> Seu deve estará na coluna `NET_DEBIT`

Você verá o saldo disponível das transações liberadas nas colunas `NET_CREDIT` (creditado) e `NET_DEBIT` (debitado), dependendo se o valor é positivo ou negativo. Você também verá aí o valor bruto e os gastos de financiamento, impostos e custos de envio que descontamos para chegar ao valor líquido.

**O que acontece se uma transferência não se concretizar? **

Caso isso aconteça, o relatório continuará válido. O dinheiro voltará à sua conta e a transação aparecerá no relatório em uma nova linha na coluna `NET_CREDIT`.


> NOTE
>
> Nota
>
> Tenha em mãos o [Glossário do relatório](https://www.mercadopago.com.br/developers/es/guides/manage-account/reports/released-money/glossary/) de liberaçoes para consultá-lo quando precisar ou queira conferir algum termo técnico.

## Exemplo de um relatório

Observe como está composto o relatório de dinheiro liberado neste exemplo para identificar as seções e analisar seus próprios relatórios:

![Relatório de liberaçoes Exemplos Mercado Pago](/images/manage-account/reports/examples-es.png)

A versão padrão mostrará uma visualização estendida das colunas. O relatório final terá a maior quantidade de detalhes possível. 


> WARNING
>
> Importante: diferenças entre retirada parcial e retirada total.
>
> Quando você retirar todo o seu saldo disponível, o total do relatório corresponderá a esse valor. Por outro lado, quando você faz uma retirada parcial, que não inclui todo o seu dinheiro liberado na conta, o saldo total disponível e o total do relatório não coincidem.
>
>Por exemplo, imagine que você tenha R$ 3.000 disponíveis para retirar para uma conta bancária, mas retira apenas R$ 2.000. A retirada é parcial, mas o valor total do relatório continuará a mostrar o valor do saldo inicial que estava no momento da retirada, ou seja, os R$ 3.000 disponíveis. Por outro lado, se você retirar os R$ 3.000, o valor total do relatório corresponderá ao valor dessa retirada.


<hr/>

### Próximos passos

> LEFT_BUTTON_REQUIRED_ES
>
> Gere seus relatórios                   
>
> Saiba as formas de gerar um relatório e siga as etapas para configurar suas preferências.
>
> [Gere seus relatórios](https://www.mercadopago.com.br/developers/es/guides/manage-account/reports/released-money/generate/)

> RIGHT_BUTTON_RECOMMENDED_ES
>
> Glossário
>
> Saiba o que significa cada termo e os detalhes das colunas que compõem o relatório.
>
> [Glossário](https://www.mercadopago.com.br/developers/es/guides/manage-account/reports/released-money/glossary/)