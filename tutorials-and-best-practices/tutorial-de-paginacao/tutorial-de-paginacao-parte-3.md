# Tutorial de paginação - parte 3

O caminho EXTRACTING\_DATA é onde os dados são recuperados de sua fonte e enviados em blocos para serem processados.

Nesse caminho, o fluxo envia cada registro para um _pipeline_ de processamento de dados, cria um resumo da execução e atualiza os parâmetros da paginação a depender de em qual parte da migração o processo se encontra.

Se você quiser aprender mais sobre _pipelines_ de processamento de dados, leia nossa [documentação sobre arquitetura orientada a eventos](../arquitetura-orientada-a-eventos.md).

<figure><img src="https://lh6.googleusercontent.com/e7vRQAEnlrbLNasl9iGQVIIAWisyrtcZgDsEGqIOhaCPL0juco35bvEd6WT3IPMFCCLK9GZy9LYl3QMbOviSnL5NK3pJUSYSvX9j7mrlt2l8Y4qZIYfA6eY1he0Au85OGrNIZVx80MjD-HgqzWm_PuOzaySEdNHgUe232vUO46hq0mrSyukBTuwRdCtNGA" alt=""><figcaption><p><strong>O caminho EXTRACTING_DATA</strong></p></figcaption></figure>

Para construir o caminho EXTRACTING\_DATA, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `$.control[?(@.step == 'EXTRACTING_DATA')]`.

Aplicando essa condição, o fluxo de integração segue esse caminho se o parâmetro _step_ assumir valor `EXTRACTING_DATA`.

&#x20; 3\. Adicione um componente que realiza iterações através da sua fonte de dados, como um componente For Each ou Stream DB V3

No nosso exemplo, utilizamos o Stream DB V3. Configure a conta, URL do banco de dados e nome da coluna de acordo com a fonte de dados e use o seguinte comando SQL:

```sql
select * from enb_person limit {{ message.control.start }}, {{ message.control.limit }}
```

Esse comando recupera um número de registros igual ao parâmetro _limit_, começando pelo registro cujo índice é igual ao parâmetro _start_.

No subpipeline onProcess desse componente, adicione um componente Event Publisher, configure o nome do evento para o evento ao qual o seu _pipeline_ de processamento de dados é inscrito e configure a propriedade _Body_ para `{{ message.$ }}` para enviar todo o _payload_.

Depois, gere uma mensagem de sucesso usando um componente JSON Generator. Configure o parâmetro JSON desse componente para:

```json
{
    "success": true
}
```

<figure><img src="https://lh5.googleusercontent.com/ZoH6FjJWAOLcvbwJ0rYRnCNdS_UfRnArFkov1jaHiwiaIVWSJGdefhbpPK19W9Mx__uow4OE8rVQrrmAWQd6ZhYAMukTDT732RN-u4B86CMU8vSnLVrNnG4racnR5Q9YNmfBuuYDM2qZpjyvq3HzhluBEvj0n3rPfwuj6MzBDHsGjBowiKM1TUBBQjAq9Q" alt=""><figcaption><p><em>Subpipeline</em> onProcess do Stream DB V3</p></figcaption></figure>

No _subpipeline_ onException desse componente, adicione um componente Log seguido de um Event Publisher. Este componente publica eventos de erro aos quais o seu _pipeline_ de tratamento de erros está inscrito. Se você quiser aprender mais sobre pipelines de tratamento de erro, leia [nossa documentação sobre arquitetura orientada a eventos](../arquitetura-orientada-a-eventos.md).

Finalmente, adicione um componente Throw Error.

<figure><img src="https://lh6.googleusercontent.com/HtevcL2LhOrSKa5EdxeYtQbW88ymnL68UJ4-YWglSA9u0WJbq4JJ85XTqMVKtSNbgbZwtJtzzvBrFOIY7Ix9vLQpZe-YlLc3FVw6zE28gvk8j0ZhKhFAMyxbcTf0JS2TgwbfgN-w_BIjsANsmU3VaKRlpcEqWu-G5TJwjIyRdTCB2rE_2g9XOT3qSQeSbA" alt=""><figcaption><p><em>Subpipeline</em> onException do Stream DB V3</p></figcaption></figure>

De volta ao caminho EXTRACTING\_DATA,

&#x20; 4\. Crie um resumo da execução usando um JSON Generator.

O componente Stream DB ou For Each usado no passo 3 envia como _output_ um resumo da execução. Salve este resumo em uma propriedade JSON chamada _summary_ configurando o parâmetro JSON desse componente como:

```json
{
    "summary": {{ message.$ }}
}
```

&#x20; 5\. Salve a propriedade `summary` usando um componente Session Management

&#x20; 6\. Recupere a propriedade `control` usando um componente Session Management

&#x20; 7\. Verifique se o processo de migração acabou usando um componente Choice

Quando o processo de migração acaba, os parâmetros de paginação são atualizados e um _output_ informando o fim do processo é enviado no formato JSON. Para construir esse fluxo, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `$.[?(@.summary.total < @.control.limit)]`.

Usando essa condição, o fluxo segue esse caminho se o número de registros recuperados for menor que o parâmetro _limit_. Isso é uma indicação de que não há mais registros a serem recuperados neste momento.

&#x20; 3\. Atualize os parâmetros de paginação utilizando um componente Object Store

Use o mesmo nome e ID dos Object Stores usados anteriormente, ative as opções _Unique Index_ e _Upsert_ e configure o parâmetro _Document_ como:

```json
{
    $set:{
        "start": 0,
        "end": null,
        "step": "FINISHED",
        "nextExecutionTimestamp": {{ FORMATDATE(FORMATDATE(SUMDATE( NOW() , "DAY", 1), "timestamp", "dd/MM/yyyy 01:00:00"), "dd/MM/yyyy HH:mm:ss", "timestamp") }}
    }
}
```

Este código atribui valor `FINISHED` para o parâmetro _step_. Isso significa que na próxima execução desse _pipeline_, o código seguirá o caminho FINISHED.

Note que o parâmetro `start` é configurado para o valor `0` porque essa é uma migração total do banco de dados. Para que a migração continuasse de onde parou no dia anterior, deveríamos alterar o valor de _start_ para ser igual ao valor de `end` nessa iteração.

&#x20; 4\. Recupere a propriedade `control` usando um componente Session Management.

&#x20; 5\. Gere um _output_ usando um componente JSON Generator.

Configure o parâmetro JSON como:

```json
{
    "message": {{ CONCAT("A migração começará em ",  FORMATDATE( message.control.nextExecutionTimestamp, "timestamp", "dd/MM/yyyy HH:mm:ss")) }}
}
```

Agora, retorne ao componente Choice que verifica se o processo de migração acabou ou não. Se o processo não acabou, o fluxo atualiza os parâmetros de paginação e envia uma mensagem informando que o processo continuará.

Para construir esse fluxo, siga esses passos:

&#x20; 1\. Adicione um componente Log

&#x20; 2\. Configure a condição Choice desse caminho como `otherwise`

&#x20; 3\. Atualize os parâmetros de paginação usando um componente Object Store

Use o mesmo nome e ID dos Object Stores usados anteriormente, ative as opções _Unique Index_ e _Upsert_ e configure o parâmetro _Document_ como:

```json
{
    $set:{
        "start": {{ message.control.end }},
        "end": {{ TOINT(SUM(message.control.end, message.control.limit)) }},
        "step": "EXTRACTING_DATA"
    }
}
```

&#x20; 4\. Recupere os parâmetros de paginação usando um componente Object Store.

Use o mesmo nome e ID dos Object Stores usados anteriormente e defina a operação como _Find by Object Store ID_.

&#x20; 5\. Crie um output usando um componente JSON Generator

Configure o parâmetro JSON desse componente como:

```json
{
    "mensagem": "Os dados estão sendo migrados",
    "next_execution": {{ message.data[0] }}
}
```
