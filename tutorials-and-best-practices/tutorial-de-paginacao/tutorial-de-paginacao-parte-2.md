# Tutorial de paginação - parte 2

O fluxo de integração segue o caminho FINISHED se o processo de migração de dados diário já terminou ou se ainda não chegou a hora de iniciá-lo.

Primeiramente, verificamos se o parâmetro _next execution timestamp_ é nulo, isto é, não existe. Isso acontece durante a primeira execução do _pipeline_. Se for nulo, atribuímos um valor a ele.

Se o parâmetro _next execution timestamp_ existe, o _pipeline_ verifica se é hora de iniciar o processo de migração de dados ou se ele deve continuar esperando. Se for a hora de iniciar o processo, atribuímos o valor `EXTRACTING_DATA` à propriedade step, o que faz com que o fluxo siga o caminho EXTRACTING\_DATA na próxima execução.

Para construir o caminho FINISHED, siga esses passos:

<figure><img src="https://lh5.googleusercontent.com/oPRr4nSfXl9iZMQfgsEHj23O66MpeJuZ4CPE1dmSECu6aII9tG4kgWuPjOEh-NBtgUyJzB3t-pCUJUGgfhv8-evNt2eK2ZnrJcKCulFMR9Y-mL96XRVELICzfVVTsi3rAQ_j5kfpuBogQPF1iPNi6Yjp5UiHfDIjMne5oOLuZveRiYgxywgBjHZ1mWJ4fA" alt=""><figcaption><p><strong>O caminho FINISHED</strong></p></figcaption></figure>

&#x20; 1\. Adicione um componente Log.

Sempre adicione um componente Log após um componente Choice. Isso é considerado uma boa prática.

Como em todos os componentes Log, adicione uma mensagem descritiva no campo mensagem. Você pode aprender mais sobre esse componente [aqui](../../components/tools/log.md).

&#x20; 2\. Configure a condição Choice desse caminho como `$.control[?(@.step == 'FINISHED')]`**.**

Aplicando essa condição, o fluxo de integração seguirá esse caminho se o parâmetro _step_ assumir valor `FINISHED`.

&#x20; 3\. Adicione um componente Choice.

Esse componente verifica se o parâmetro _next execution timestamp_ existe.

Para construir o caminho que o fluxo segue caso esse parâmetro exista, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `$.[?(@.control.nextExecutionTimestamp != null)]`.

&#x20; 3\. Adicione outro componente Choice.

Esse componente verifica se está ou não na hora de começar o processo de migração.

Para construir o caminho que o fluxo segue quando é hora de iniciar a migração, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `$.control.[?(@.startTimestamp>= @.nextExecutionTimestamp)]`.

&#x20; 3\. Atualize os parâmetros de paginação utilizando um componente Object Store

Selecione a operação _Update by Object ID_, ative a opção _Upsert_, use o mesmo nome e ID do Object Store utilizado nos passos iniciais e configure o parâmetro _Document_ dessa maneira:

```json
{
    $set:{
        "step": "EXTRACTING_DATA"
    }
}
```

Esse código atribui o valor `EXTRACTING_DATA` à propriedade _step_. Isso faz com que o _pipeline_ siga o caminho EXTRACTING\_DATA na próxima execução.

&#x20; 4\. Configure uma mensagem de _output_ usando um componente JSON Generator

Configure o parâmetro JSON deste componente desta maneira:

```json
{
    "message": "Migration will start at the next execution."
}
```

Para construir o caminho que o fluxo segue quando ainda não é hora de iniciar a paginação, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `otherwise`.

&#x20; 3\. Configure uma mensagem de _output_ usando um componente JSON Generator.

Configure o parâmetro JSON desse componente como:

```json
{
    "message": {{ CONCAT("A migração começará em ",  FORMATDATE( message.control.nextExecutionTimestamp, "timestamp", "dd/MM/yyyy HH:mm:ss")) }}
}
```

Agora, retorne ao componente Choice que verifica se o parâmetro next execution timestamp é nulo ou não.

Para construir o caminho que o fluxo segue quando esse parâmetro é nulo, siga esses passos:

&#x20; 1\. Adicione um componente Log.

&#x20; 2\. Configure a condição Choice desse caminho como `otherwise`.

&#x20; 3\. Configure o _timestamp_ da próxima execução utilizando um componente Object Store.

Selecione a operação _Update by Object ID_, ative a opção _Upsert_, use o mesmo nome e ID do Object Store que usamos nos passos iniciais e configure o parâmetro _Document_ como:

```json
{
    $set:{
        "nextExecutionTimestamp": {{ FORMATDATE(FORMATDATE(SUMDATE( NOW() , "DAY", 1), "timestamp", "dd/MM/yyyy 01:00:00"), "dd/MM/yyyy HH:mm:ss", "timestamp") }}
    }
}
```

Esse código faz com que o timestamp da próxima execução seja configurado para o próximo dia, às 1 da manhã.
