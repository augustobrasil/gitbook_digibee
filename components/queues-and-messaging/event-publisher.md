---
description: >-
  Descubra mais sobre o componente Event Publisher e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Event Publisher

Um evento é uma mensagem que notifica outros componentes sobre uma mudança de estado, uma ação ou um fato ocorrido. O **Event Publisher** publica um evento para que outros _pipelines_ configurados para escutá-lo possam reagir quando a publicação ocorrer.

Para mais informações, [leia a documentação sobre Arquitetura orientada a eventos](../../tutorials-and-best-practices/arquitetura-orientada-a-eventos.md).

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="291">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Event</strong> <code>(DB)</code></td><td>Nome do evento criado que será publicado para consumo por outros <em>pipelines</em>.</td><td>{{ DEFAULT(message.eventName, "new-event") }}</td><td><em>String</em></td></tr><tr><td><strong>Body</strong> <code>(DB)</code></td><td><em>Payload</em> a ser enviado com o evento.</td><td>{{ message.$ }}</td><td>JSON</td></tr><tr><td><strong>Log Each Event Sent</strong></td><td>Quando ativada, a opção irá gerar uma entrada de <em>log</em> para cada evento enviado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do pipeline com erro será interrompida; do contrário, a execução do pipeline continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Como o Event Publisher é utilizado? <a href="#como-o-event-publisher--utilizado" id="como-o-event-publisher--utilizado"></a>

Para implementar uma Arquitetura Orientada a Eventos é necessário definir:

* o _pipeline_ que publicará o evento (Publicador);
* um ou mais _pipelines_ que irão consumir o evento (Assinantes).

Para configurar o _pipeline_ que publicará o evento:

* arraste o **Event Publisher** para o _canvas_ do _pipeline_ Publicador;
* configure o nome do evento no parâmetro **Event** do **Event Publisher**;
* caso deseje passar um _payload_ junto com o evento, defina o conteúdo do parâmetro **Body**.

Para configurar o _pipeline_ que consumirá o evento:

* altere o tipo do _trigger_ para [**Event Trigger**](../triggers/event-trigger.md) no _pipeline_ Assinante;
* abra as configurações do _trigger_ e informe o nome do evento a ser consumido no parâmetro **Event Name**. Esse valor deve ser idêntico ao informado no **Event Publisher** do _pipeline_ Publicador.

## **Cenários de erro**

### **java.util.NoSuchElementException: Timeout waiting for idle object**

Quando utilizar o **Event Publisher**, o seguinte erro pode ocorrer: `java.util.NoSuchElementException: Timeout waiting for idle object`

Isso significa que o componente está com dificuldades para lidar com a grande quantidade de eventos que estão sendo enviados ao mesmo tempo. Para resolver essa situação, você tem duas opções:

* **Aumentar o número de réplicas do **_**pipeline**_: isso ajuda a distribuir a carga de eventos de forma mais eficiente e reduzir a pressão sobre o componente para que ele processe os eventos de maneira mais fluida.
* **Implementar um tratamento de erros com o Retry:** essa abordagem envolve o uso do componente **Retry** para para fazer novas tentativas de envio dos eventos que causaram o erro. Isso pode ser útil para lidar com picos de carga temporários ou eventos que ocasionalmente falham.

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Entrada** <a href="#entrada" id="entrada"></a>

O componente espera uma mensagem válida em formato JSON. Não é esperado nenhum atributo específico. A mensagem de entrada poderá ser referenciada através de _Double Braces_ tanto para a configuração do parâmetro **Event** quanto do parâmetro **Body**. Por exemplo, digamos que a mensagem abaixo fosse passada para o **Event Publisher**:

```
{
"eventName": "example",
"body": {
"id": "1",
"description": "Description of the case"
}
}
```

Você poderia definir uma expressão _Double Braces_ no parâmetro **Event** para obter o valor do atributo `eventName`:

```
{{ message.eventName }}
```

O atributo `body` também poderia ser configurado da mesma forma:

```
{{ message.body }}
```

### **Saída** <a href="#sada" id="sada"></a>

O componente repassa a mensagem recebida do componente anterior sem nenhuma alteração. No caso do exemplo acima, a mensagem repassada seria:

```
{
"eventName": "example",
"body": {
"id": "1",
"description": "Description of the case"
}
}
```
