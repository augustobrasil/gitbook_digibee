---
description: >-
  Aprenda sobre a arquitetura orientada a eventos, um modelo que a Digibee
  Integration Platform usa para dividir o fluxo de integração de um usuário em
  vários pipelines.
---

# Arquitetura orientada a eventos

Usar um único _pipeline_ para realizar todas as tarefas do seu fluxo de integração pode parecer uma solução simples e eficiente, mas esse método pode trazer problemas a longo prazo.&#x20;

Aqui vamos falar sobre arquitetura orientada a eventos, um modelo mais eficiente que divide seu fluxo de integração em vários _pipelines_.

## O padrão publisher-subscriber

Suponha que você fez uma compra com seu cartão de crédito. Após você fazer a transação, você recebe uma notificação do seu aplicativo do banco confirmando a compra e um e-mail da loja contendo a nota fiscal.

Vamos usar esse exemplo para ilustrar a arquitetura orientada a eventos, conceito importante na arquitetura de _pipelines._ Alguns conceitos importantes desse modelo são:

* **Evento**: uma ação de interesse de um sistema. No nosso exemplo, sua compra é um evento.&#x20;
* **Publisher (publicadores)**: a parte do sistema que informa quais eventos ocorreram. No nosso exemplo, a empresa de cartão de crédito é um _publisher_. Na Digibee Integration Platform, você pode publicar eventos com o componente [Event Publisher](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/event-publisher).&#x20;
* **Subscriber ou consumer (inscrito ou consumidor)**: a parte do sistema que recebe informações acerca de certos eventos. No nosso exemplo, o aplicativo do banco e o e-mail da loja são _subscribers_. Na Digibee Integration Platform, você pode criar um _subscriber_ com um [Event Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/event-trigger).&#x20;

No padrão **publisher-subscriber**, registros de eventos não são comunicados a _subscribers_ específicos. Eles são enviados a um log administrado por um _event broker_, como o Apache Kafka ou o RabbitMQ. _Consumers_ inscritos nesses eventos são informados quando eles ocorrem.

Note que um único evento pode ser comunicado a vários _subscribers_. No nosso exemplo, o evento da compra foi comunicado tanto ao aplicativo do banco quanto ao e-mail da loja.

Note também que _publishers_ e _subscribers_ não estão cientes uns dos outros e existem independentemente. Suponha que a loja não tenha e-mail e que o aplicativo do banco esteja fora do ar. Mesmo não havendo _subscribers_ para o evento da compra, a empresa de cartão de crédito o publicaria de qualquer maneira.

Na Digibee Integration Platform, você pode usar a arquitetura orientada a eventos para dividir seu fluxo de integração em mais de um _pipeline_ e usar cada _pipeline_ para um propósito específico. Esse modelo oferece várias vantagens, como:

* **Evitar retrabalho**: suponha que você está construindo dez _pipelines_. Em cada _pipeline_, você quer fazer uma chamada a uma REST API de uma ferramenta ITSM sempre que um erro ocorre. Em vez de configurar o request em cada um dos dez _pipelines_, você pode criar um _pipeline_ que faz essa chamada e usar [Event Publishers](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/event-publisher) nos outros _pipelines_ para ativá-lo.
* **Facilitar manutenção**: suponha que você queira fazer um ajuste a essa parte do fluxo de integração responsável por enviar uma mensagem de erro a uma ferramenta ITSM. Em vez de ajustar dez _pipelines_, você pode ajustar somente a que faz a chamada API.
* **Evitar erros**: usando um _pipeline_ para cada tarefa, você reduz a chance de erros Out of Memory ou Timeout, causados por sobrecarga no _pipeline._&#x20;
* **Escalar de acordo com sua necessidade**: usando a arquitetura orientada a eventos, você pode aumentar o tamanho de implementação somente dos _pipelines_ do seu fluxo de integração que requerem mais memória, em vez de aumentar o de todos eles.&#x20;

## Modelo síncrono

{% hint style="success" %}
Use o modelo síncrono para integrações que exigem confirmação imediata
{% endhint %}

{% hint style="danger" %}
Não use o modelo síncrono para integrações que:&#x20;

* Manipulem grandes quantidades de dados&#x20;
* Insiram, modifiquem ou deletem dados em um banco de dados&#x20;
* Façam chamadas POST para serviços que não suportam grandes listas de dados
* Demorem pra processar
{% endhint %}

Um dos modelos que usam arquitetura orientada a eventos na Digibee Integration Platform é o modelo síncrono. Nesse modelo, dividimos nosso fluxo de integração em dois tipos de _pipelines_: os _**pipelines**_** de regra de negócio** e os _**pipelines**_** de tratamento de erros**.

Os _**pipelines**_** de regra de negócio** realizam todos os passos necessários para fazer sua integração de dados. Quando um erro ocorre nesses processos, um componente Log os registra e um componente [Event Publisher](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/event-publisher) publica o evento de erro.

O _**pipeline**_** de tratamento de erro** é um único pipeline que possui um _trigger_ de evento. Ele “escuta” os eventos de erro que são publicados pelos _pipelines_ de regra de negócio. Esse pipeline pode enviar alertas de erro ou reprocessar dados.

Note que o mesmo evento de erro pode ser publicado por vários _pipelines_ e enviado para o mesmo _pipeline_ de tratamento de erro.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p><strong>Modelo síncrono</strong></p></figcaption></figure>

## O modelo assíncrono

{% hint style="success" %}
Use o modelo assíncrono para integrações que:&#x20;

* Insiram dados em um banco de dados&#x20;
* Manipulem grandes quantidades de dados
* Façam chamadas POST a serviços que não suportem grandes listas de dados
* Demorem para processar
{% endhint %}

{% hint style="danger" %}
Não use o modelo assíncrono para integrações que exigem confirmação imediata
{% endhint %}

Outro modelo que usa a arquitetura orientada a eventos é o modelo assíncrono. Para construir um fluxo de integração usando um modelo assíncrono, você deve construir quatro _pipelines:_&#x20;

**O primeiro pipeline** busca dados de um banco de dados ou de uma API e publica um evento para cada registro de dados. Se um erro ocorrer nesse processo, esse _pipeline_ publica um evento de erro.

**O segundo pipeline** é inscrito nos eventos publicados pelo primeiro _pipeline_. Ele recebe os registros de dados que foram buscados do banco de dados e os processa de acordo com a regra de negócio. Se um erro ocorrer durante esse processo, esse _pipeline_ registra o erro, assim como o payload de input em um Object Store.

**O terceiro pipeline** periodicamente acessa o Object Store mencionado anteriormente e busca registros de erros. Depois, ele checa quantas tentativas de reprocessamento já foram feitas para um determinado registro. Se o número de tentativas ainda não alcançou um limite definido anteriormente, o _pipeline_ publica um evento de reprocessamento que será recebido pelo segundo _pipeline_. Se o número de tentativas de reprocessamento atingir o limite ou se um erro acontecer durante a execução desse _pipeline_, ele publica um evento de erro.

**O quarto pipeline** é inscrito nos eventos de erro que foram enviados pelos três _pipelines_ anteriores. Depois de receber esses eventos de erro, ele os armazena em um banco de dados e envia esses registros a uma ferramenta de ITSM ou por email.

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p><strong>Modelo assíncrono</strong></p></figcaption></figure>
