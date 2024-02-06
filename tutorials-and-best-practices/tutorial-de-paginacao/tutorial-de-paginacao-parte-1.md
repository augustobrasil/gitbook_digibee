# Tutorial de paginação - parte 1

Nos passos iniciais do pipeline de paginação, nós configuramos o trigger do pipeline e usamos uma sequência de componentes para configurar e salvar os parâmetros de paginação, como descrito abaixo:

<figure><img src="https://lh3.googleusercontent.com/1IaUxYbJ1cqy0KS7WK4ZSPuyIhom1AslFqgN5IhNn3XPoUmvruECdLsxViXDrp6lXAISUh0WdO7YZnUDXVIXQuV7iQqDI9enXaHh-O81RUb2USuCmUgN8rkrz8L8-ZywswEcKgzd4QYttOtjuC2894s_r4axdkw2wy2qU4tABuQnecP6O0knqncZ6rzkjw" alt=""><figcaption><p>Passos iniciais de um pipeline de paginação</p></figcaption></figure>

&#x20; 1\. Configure o _trigger_ do pipeline para um _scheduler trigger_ de cinco minutos.

Esse pipeline migra um banco de dados diariamente às 1 da manhã. O _pipeline_ é ativado em intervalos regulares para verificar se está na hora de começar a paginação. Aqui, configuramos o _trigger_ para ativar o _pipeline_ a cada cinco minutos.

&#x20; 2\. Consulte os parâmetros da paginação usando um componente Object Store (OS).

Esse componente consulta um banco de dados OS para encontrar parâmetros de paginação. Esses parâmetros são:

* _Start timestamp_: a data e hora nos quais o pipeline foi ativado.&#x20;
* _Limit_: o número máximo de resultados a serem retornados.
* _Start_: o índice do primeiro registro a ser processado nesse passo do processo de paginação.&#x20;
* _End_: o índice do último registro a ser processado nesse passo do processo de paginação.&#x20;
* _Step_: esse parâmetro assume o valor `EXTRACTING_DATA` quando o processo de paginação está ocorrendo ou `FINISHED` quando ele termina ou quando o _pipeline_ é executado pela primeira vez.&#x20;
* _Next execution timestamp_: a data e hora do próximo processo de migração.

Para consultar os parâmetros, selecionamos a operação “Find by Object ID” e definimos o Object ID como:

```
{{ CONCAT(metadata.pipeline.name, "_v" , metadata.pipeline.versionMajor) }}
```

Aqui, usamos a função CONCAT para nomear o ID do Object Store como o nome desse pipeline seguido de sua versão.

Atribua valor `0` para os parâmetros _limit_ e _skip_ desse componente e ative a opção _Unique Index_.

Durante a primeira execução do _pipeline_, os parâmetros da paginação não existirão, então precisamos definir valores padrão para eles. Faremos isso no passo 3.

&#x20; 3\. Defina valores padrão para os parâmetros da paginação utilizando um componente JSON Generator.

Utilizamos a função Double Braces DEFAULT para atribuir valores padrão aos parâmetros da paginação recuperados pelo Object Store se eles não existirem. Isso acontece durante a primeira execução do _pipeline_.

O parâmetro JSON desse componente deve ser configurado desta maneira:

```json
{
    "control":{
        "startTimestamp": {{ metadata.execution.startTimestamp }},
        "limit": {{ DEFAULT( message.data[0].limit, 500 ) }},
        "start": {{ DEFAULT( message.data[0].start, 0 ) }},
        "end": {{ DEFAULT( message.data[0].end, 500 ) }},
        "step": {{ DEFAULT( message.data[0].step, "FINISHED" ) }},
        "nextExecutionTimestamp": {{ message.data[0].nextExecutionTimestamp }}
    }
}
```

Nesse exemplo, nós atribuímos o valor `500` para a propriedade _limit_. Ao aplicar a paginação, você deve mudar esse valor de acordo com sua necessidade de processamento de dados. Um valor de _limit_ muito alto pode sobrecarregar o _pipeline_, fazendo com que a paginação perca seu propósito; um valor muito pequeno pode deixar o processo lento.

&#x20; 4\. Salve a propriedade `contol` usando um componente Session Management.

&#x20; 5\. Divida o fluxo de integração usando um componente Choice.

Esse componente divide o fluxo de integração nos três caminhos mencionados anteriormente: o caminho FINISHED, o caminho EXTRACTING\_DATA e o caminho de erro. Vamos descrever como cada caminho deve ser construído nos próximos artigos.

<figure><img src="https://lh5.googleusercontent.com/dvsvwrEPUD--lFHDGedOKGlmwIcZYX1RrQxWzxWe1uxNKI8LU_yvypHvzPzFURAzb0mAgrx9LTOXzHaeg1l9GC096bbaeYlBDO7R440W4YZu5o4XyN1qFsov2wu04EV79OFwhUi6VzvS4SUXxWESjfB30FtQvHHlMSocjHziwbk1zsnza3tzpyGI3BBJKw" alt=""><figcaption><p>Camihos do <em>pipeline</em> de paginação</p></figcaption></figure>
