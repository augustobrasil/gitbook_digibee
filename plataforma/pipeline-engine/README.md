---
description: Conheça o motor de execução dos pipelines.
---

# Pipeline Engine

A Digibee Integration Platform utiliza um motor que não somente interpreta os pipelines construídos através da interface, mas também os executa. Esse motor é chamado de _Pipeline Engine_.

\
Dê uma olhada nos conceitos e na arquitetura de operação do _Pipeline Engine_.

### Conceitos <a href="#conceitos" id="conceitos"></a>

Tenha a visão em alto nível do Pipeline Engine em relação aos nossos demais componentes da Plataforma:

* **Pipeline Engine:** componente responsável pela execução dos fluxos construídos na nossa Plataforma
* **Trigger:** componente que recebe invocações que vêm de diferentes tecnologias e as encaminha para o Pipeline Engine
* **Mecanismo de filas:** mecanismo central de gestão de filas da nossa Plataforma

### Arquitetura de Operação <a href="#arquitetura-de-operao" id="arquitetura-de-operao"></a>

Cada fluxo (_pipeline_) criado é convertido em um container Docker, executado com a tecnologia Kubernetes - base da Digibee Integration Platform. Veja as principais garantias desse modelo de operação:

* **isolamento:** cada container é executado na infraestrutura de maneira exclusiva (os espaços de memória e o consumo de CPU são completamente exclusivos para cada _pipeline_)
* **segurança:** _pipelines_ NÃO conversam entre si, a não ser que seja através das interfaces providas pela nossa Plataforma
* **escalabilidade específica:** é possível aumentar o número de "réplicas" de _pipelines_ de maneira específica, isto é, aumentar ou diminuir o que demanda maior ou menor desempenho

### **Tamanhos de Pipeline**

Utilizamos o conceito _serverless_, ou seja, você não precisa se preocupar com detalhes de infraestrutura para a execução dos seus _pipelines_. Dessa forma, cada _pipeline_ deve ter o seu tamanho definido durante a implantação. A Plataforma permite que os pipelines sejam utilizados em 3 tamanhos distintos:

* SMALL, 10 _consumers_ (consumidores), 20% de 1 CPU, 64 MB de memória
* MEDIUM, 20 _consumers_ (consumidores), 40% de 1 CPU, 128 MB de memória
* LARGE, 40 _consumers_ (consumidores), 80% de 1 CPU, 256 MB de memória

### _**Consumers**_

Além do tamanho de cada _pipeline_, você define o número máximo de execuções simultâneas (ou consumidores) que o _pipeline_ permite. Dependendo do tamanho, um número máximo de consumidores pode ser configurado para a execução.&#x20;

Assim, um _pipeline_ com 10 consumidores pode processar 10 mensagens em paralelo, enquanto um _pipeline_ com 1 consumidor pode processar somente 1 mensagem.

### **Recursos (CPU e Memória)**

Além do mais, o tamanho do _pipeline_ também define o desempenho e a quantidade de memória que ele tem acesso. O desempenho é dado pela quantidade de ciclos de uma CPU a qual o _pipeline_ tem acesso.&#x20;

Por outro lado, a memória é dada pelo espaço endereçável para tratamento de mensagens e consumo de informações.

### **Réplicas**

As mensagens são enviadas ao mecanismo de filas da Plataforma através de _triggers_, que são a porta de entrada para a execução dos _pipelines_. Existem _triggers_ para diferentes tipos de tecnologia, assim como REST, HTTP, Scheduler, Email, etc. Assim que as mensagens chegam ao mecanismo de filas, elas ficam disponíveis para serem consumidas pelos _pipelines_.&#x20;

Durante a implantação do _pipeline_, você deve definir seu o número de réplicas. Um _pipeline_ SMALL com 2 réplicas tem o dobro do desempenho de processamento e escalabilidade, e assim por diante. Além de prover mais poder de processamento e escalabilidade, as réplicas garantem maior disponibilidade - se uma das réplicas falha, há outras para atender.

De maneira geral, as réplicas entregam escalabilidade horizontal, enquanto o tamanho do _pipeline_ entrega escalabilidade vertical. Por isso, mesmo que 1 _pipeline_ de tamanho LARGE seja equivalente a 4 _pipelines_ de tamanho SMALL pela lógica da infraestrutura, não significa que eles sejam equivalentes para todos os tipos de cargas de trabalho. Em muitas situações, principalmente naquelas que envolvam o processamento de mensagens grandes, somente a utilização de _pipelines_ "verticalmente" maiores traz o resultado esperado.

### _**Timeouts**_ e **Expiration**

Os _triggers_ podem ser configurados com os seguintes tipos principais de controle de tempo para o processamento de mensagens:

* _**timeout**_**:** indica o tempo máximo que o _trigger_ espera pelo retorno do _pipeline_
* _**expiration**_**:** indica o tempo máximo que uma mensagem pode ficar na fila até ser capturada por um _Pipeline Engine_

\
A configuração de _timeout_ é possível para todos os _triggers_, mas apenas alguns permitem a configuração de _expiration_. Isso ocorre porque a característica do _trigger_ pode ser síncrona ou assíncrona.

O _trigger_ de eventos realiza execuções de forma assíncrona e pode manter mensagens em fila por um bom tempo até que sejam consumidas. Por essa razão, faz sentido definir o tempo de expiração das mensagens produzidas por esse tipo de _trigger_.

Contudo, REST Trigger depende da resposta do _pipeline_ para dar um retorno. Nesse caso, a configuração de _expiration_ não faz sentido. Mesmo assim, internamente, os _triggers_ síncronos estimam o tempo de expiração, não configurável, para as mensagens. Isso garante que as mensagens não se percam no processo de enfileiramento.

### **Controle de Execução**

O processamento de mensagens é feito de forma sequencial para cada consumidor. Logo, se um pipeline é implantado com 1 consumidor, as mensagens serão processadas 1 a 1 sequencialmente. Enquanto a mensagem é processada, ela recebe uma marca e nenhuma outra réplica de _pipeline_ vai poder recebê-la para processamento.&#x20;

Se um pipeline enfrentar qualquer problema na execução e precisar de um _restart_ (ex.: OOM, crash, etc.), então as mensagens em execução serão devolvidas para o mecanismo de fila.

### **Mensagens devolvidas para a fila de processamento**

Mensagens devolvidas para a fila de processamento ficam disponíveis para o consumo de outras réplicas de _pipeline_ ou até mesmo pela mesma réplica que teve algum problema e precisou ser reiniciada.

Nesse caso, é possível configurar o _pipeline_ para definir a abordagem em casos de reprocessamento de mensagens. Todos os _triggers_ da Plataforma possuem uma configuração denominada "_Allow Redeliveries_".&#x20;

Quando essa opção estiver ativada, o _pipeline_ aceita que a mensagem seja reprocessada. Quando desativada, o _pipeline_ recebe a mensagem, detecta que se trata de um reprocessamento e a recusa por meio de um erro.

O tempo de retentativas da mensagem será o tempo do _Maximum Timeout_ definido no _trigger_ do _pipeline_, no caso de um _pipeline_ com _Event Trigger_ será o tempo determinado no _Expiration_.

Também é possível detectar se a mensagem em execução é reprocessada ou não. Para fazer isso, basta utilizar a linguagem _Double Braces_ acessando o escopo de metadados. Exemplo:

```
{{ metadata.execution.redelivery }} 
```
