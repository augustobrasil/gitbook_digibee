---
description: >-
  Descubra mais sobre o componente Event Trigger e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Event Trigger

Um evento é uma mensagem que notifica outros componentes sobre uma mudança de estado, uma ação ou um fato ocorrido. O **Event Trigger** responde a um evento específico gerado por outro _pipeline_ por meio do **Event Publisher**. [Para saber mais sobre esse componente, leia a documentação](../queues-and-messaging/event-publisher.md).&#x20;

[Você também pode aprender mais sobre Arquitetura orientada a eventos em nossa documentação](https://docs.digibee.com/documentation/v/pt-br/tutorials-and-best-practices/arquitetura-orientada-a-eventos).

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Event Name</strong></td><td>Nome do evento ao qual o <em>trigger</em> responde.</td><td>event-trigger</td><td><em>String</em></td></tr><tr><td><strong>Expiration</strong></td><td>Tempo de permanência do evento em fila (em milissegundos). Se o <em>expiration</em> for = 0 ou um valor maior que 6h, então o <em>expiration</em> será 1/4 do valor <strong>Maximum timeout</strong> especificado.</td><td>600000</td><td>Inteiro</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Padrão: 300000. Limite: 900000.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery of Messages</strong></td><td>Se ativada, a opção permite que mensagens sejam entregues novamente caso o <em>Pipeline Engine</em> falhe.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Entrada** <a href="#entrada" id="entrada"></a>

O _trigger_ espera uma mensagem válida em formato JSON. A mensagem recebida é exatamente aquela que foi definida no atributo "_body_" do componente **Event Publisher**.

```
{    
    "id": "1",    
    "description": "Description of the case"
}
```

### **Saída** <a href="#sada" id="sada"></a>

O componente repassa a mensagem recebida do componente anterior sem nenhuma alteração. No caso do exemplo acima, a mensagem repassada seria:

```
{    
    "id": "1",    
    "description": "Description of the case"
}
```

## Event Trigger em ação <a href="#event-trigger-em-ao" id="event-trigger-em-ao"></a>

#### Para implementar uma Arquitetura orientada a eventos é necessário definir:

* o _pipeline_ que publicará o evento (Publicador);
* um ou mais _pipelines_ que irão consumir o evento (Assinantes).

#### Para configurar o _pipeline_ que publicará o evento:

* arraste o _Event Publisher_ para o canvas do _pipeline_ Publicador;
* configure o nome do evento na propriedade “Evento” do **Event Publisher**;
* caso deseje passar um _payload_ junto com o evento, defina o conteúdo da propriedade “Body”.

#### Para configurar o _pipeline_ que consumirá o evento:

* altere o tipo do _trigger_ para _**Event**_ no _pipeline_ Assinante;
* abra as configurações do _trigger_ e informe o nome do evento a ser consumido na propriedade “Nome do Evento”. Esse valor deve ser idêntico ao informado no **Event Publisher** do _pipeline_ Publicador.

\
