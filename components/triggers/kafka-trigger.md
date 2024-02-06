---
description: >-
  Descubra mais sobre o Kafka Trigger e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Kafka Trigger

{% hint style="warning" %}
Para utilizar este _trigger_ é necessário entrar em contato com nossa Equipe de Suporte para obter a liberação.
{% endhint %}

O **Kafka Trigger** é responsável pelo consumo das mensagens de um _broker_ Kafka.

## Paramêtros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="258">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Nome da conta que será utilizada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Truststore</strong></td><td>Caso seja necessário informar uma <em>truststore</em> para realizar o SSL Handshake usando certificados privados, crie uma conta do tipo <em>CERTIFICATE-CHAIN</em> e informe os certificados concatenados. No campo "password" é opcional inserir a senha a ser cadastrada na criação da <em>truststore</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Keystore</strong></td><td>Caso seja necessário informar uma <em>keystore</em> para realizar a autenticação SSL mútua, crie uma conta do tipo <em>CERTIFICATE-CHAIN</em>, informe a cadeia completa com os certificados concatenados e a chave privada a ser utilizada para a autenticação SSL mútua. Caso exista uma chave privada, é necessário informá-la no campo "password".</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Brokers</strong></td><td><em>Brokers</em> do servidor (HOST: PORT) usados para o envio de registros. Para informar múltiplos HOSTS, você pode separá-los por vírgula. Exemplo: HOST1:PORT1,HOST2:PORT2,...,HOSTn:PORTn.</td><td>kafka-test.godigibee.io:9092</td><td><em>String</em></td></tr><tr><td><strong>Topic</strong></td><td>Nome do tópico que recupera os registros.</td><td>topic-digibee</td><td><em>String</em></td></tr><tr><td><strong>Protocol</strong></td><td>Protocolo utilizado para se comunicar com os <em>brokers</em>.</td><td>SASL SSL</td><td><em>String</em></td></tr><tr><td><strong>Consumer Group Name</strong></td><td>Um <em>string</em> único que identifica o grupo de consumidor ao qual esse consumidor pertence.</td><td>digibee-new</td><td><em>String</em></td></tr><tr><td><strong>Auto Commit</strong></td><td>Se "true", a mensagem passará automaticamente por <em>commit</em> assim que for recebida pelo <em>trigger</em>; do contrário, o <em>trigger</em> vai efetuar o <em>commit</em> manualmente após a confirmação de processamento do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Send Batch</strong></td><td>Só pode ser utilizado com <em>autoCommit</em> - se "true", um <em>poll</em> de mais de 1 mensagem será enviado como <em>array</em>; do contrário, será enviada 1 mensagem por vez.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Key As Avro</strong></td><td>Se "true", as keys dos registros recebidos serão interpretadas no formato Avro, do contrário, serão interpretadas como String.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Payload As Avro</strong></td><td>Se "true", os payloads (values) dos registros recebidos serão interpretados no formato Avro, do contrário, serão interpretados como String.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Schema Registry URL</strong></td><td>Caso ao menos uma das opções Key As Avro e Payload As Avro for ativada, o campo será exibido para que seja informada a URL do Schema Registry.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Schema Registry Account</strong></td><td>Account para autenticação com o Schema Registry (account Basic ou Oauth-Bearer).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Schema Registry Truststore</strong></td><td>Caso seja necessário informar uma truststore para realizar o SSL Handshake utilizando certificados privados, deve-se criar uma conta do tipo CERTIFICATE-CHAIN e informar os certificados concatenados. No campo "password" é opcional inserir a senha a ser cadastrada na criação da truststore.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Schema Registry Keystore</strong></td><td>Caso seja necessário informar uma keystore para realizar a autenticação SSL mútua, deve-se criar uma conta do tipo CERTIFICATE-CHAIN, informar a cadeia completa com os certificados concatenados e a chave privada a ser utilizada para a autenticação SSL mútua. Caso exista uma chave privada, é necessário informá-la no campo "password".</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Max Poll Records</strong></td><td>Número máximo de registros recuperados por um <em>long poll</em>.</td><td>100</td><td>Inteiro</td></tr><tr><td><strong>Include Headers</strong></td><td>Se a opção estiver ativada, os cabeçalhos da mensagem serão incluídos no <em>payload</em> de entrada do <em>pipeline</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Binary Headers</strong></td><td>Se a opção estiver ativada, os valores dos cabeçalhos de entrada serão considerados como binários e apresentados como uma representação base64. Essa opção será apresentada apenas quando <em>Include Headers</em> estiver ativado também.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Headers Charset</strong></td><td>Nome do código de caracteres para a codificação dos valores dos cabeçalhos (padrão UTF-8). Essa opção será apresentada apenas quando <em>Include Headers</em> estiver ativada também.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Por quanto tempo um <em>pipeline</em> pode ser executado (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Kerberos Service Name</strong></td><td>Valor definido na propriedade <em>sasl.kerberos.service.name</em> configurado no lado <em>server</em> do <em>broker</em> Kafka.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Partition Numbers</strong></td><td>Especifica os números das partições em que o <strong>Kafka Trigger</strong> consumirá mensagens. Pode-se configurar mais de uma partição e, caso essa propriedade não seja configurada, o <strong>Kafka Trigger</strong> irá consumir de todas as partições do tópico.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se a opção estiver habilitada, permite que a mensagem seja reenviada caso o haja falha no <em>Pipeline Engine</em>. Aprenda mais na <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine">documentação sobre <em>Pipeline Engine</em>.</a></td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="warning" %}
* O suporte ao formato Avro está atualmente em [fase Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta). Como não faz parte do padrão usar o Kafka para transmitir mensagens grandes, não aceitamos mais de 5 MB de envio de mensagens por _poll._ Recomendamos que você use a propriedade (message.max.bytes) no _broker_ para no máximo 1 MB. A capacidade de tráfego de dados no formato Avro também está incluída nesta limitação de tamanho.
* O Kafka Trigger Key e as configurações de carga útil devem corresponder às configurações dos tópicos a serem consumidos pelo Trigger: Se **Key As Avro** estiver habilitado, todas as chaves dos registros a serem consumidos deverão estar no formato Avro. Se **Payload As Avro** estiver habilitado, todas as cargas úteis (valores) de registros a serem consumidos deverão estar no formato Avro.
{% endhint %}

## Estratégias de _offsets commit_&#x20;

Esse _trigger_ possui 2 estratégias de _offsets commit_ configuráveis:

### **1.** **Commit sem garantia de entrega**

Todas as mensagens recebidas pelo _trigger_ são enviadas ao _pipeline_ de forma mais rápida, porém sem garantia de entrega (ou seja, não será esperado o retorno do _pipeline_ para que o processamento da mensagem seja confirmado).&#x20;

Com o _auto commit_ ativado, utilizaremos o _commit default_ implementado pelo Kafka. O envio de mensagem pode ser configurado por:

#### **Envio batch**

Todas as mensagens recebidas pelo _polling_ do consumidor serão enviadas juntas em um _array_. Por exemplo, se durante esse _poll_ forem retornadas 10 mensagens, então o _trigger_ enviará um _array_ com essas 10 mensagens.

#### **Envio de mensagem uma a uma**

Será feito um envio ao _pipeline_ ao invés do _array_ total (apenas 1 mensagem por vez). Por exemplo, se durante esse _poll_ forem retornadas 10 mensagens, então o _trigger_ enviará somente 1 mensagem por vez. No total, serão feitos 10 envios de mensagens ao _pipeline_.

### **2. Commit com garantia de entrega**

O _trigger_ ficará responsável por realizar o _offsets commit_, que será feito após o recebimento de uma resposta de sucesso do _pipeline_. Somente o envio _batch_ das mensagens é possível, através do qual todas as mensagens recebidas pelo polling do consumidor serão enviadas juntas em um _array_.

Por exemplo: se durante esse _poll_ forem retornadas 10 mensagens, então o _trigger_ enviará um _array_ com essas 10 mensagens.

{% hint style="info" %}
Poderá ocorrer um rebalanceamento dos consumidores e/ou das partições do Kafka. Caso isso ocorra entre o retorno da resposta do _pipeline_ ao _trigger_, os _offsets_ vão receber o _commit_. Isso pode acarretar em perdas ou mensagens duplicadas.
{% endhint %}

#### **Autocommit "false" e Batch Mode "true"**

Nessa opção, o _poll_ realizado pode trazer um _array_ de mensagens e o seu tamanho máximo é estipulado pelo _Max Poll Records_. As mensagens passam por _commit_ somente depois que o _pipeline_ retornar a transação com sucesso. Se ocorrer _timeout_ durante o processamento do _pipeline_, as mensagens não vão passar por _commit_.

#### **Autocommit "false" e Batch Mode "false"**

Nessa opção, o _poll_ vai enviar apenas 1 mensagem e não um _array_ de mensagens. Assim, o _throughput_ de envio/recebimento de mensagens é diminuído, mas a garantia do processamento bem sucedido é maior - ou seja, não há perda de mensagens.

{% hint style="info" %}
Se houver rebalanceamento do Tópico no Broker do Kafka durante o processamento das mensagens e os consumidores tiverem que assumir outras partições, as mensagens vão passar por _commit_ caso ocorra erro no término da execução do _pipeline_. Dessa maneira, as mensagens não vão ser processadas no _poll_ seguinte.&#x20;

Para contornar esse problema, recorra às configurações _**Autocommit "false"**_ e _**Batch Mode "false**_".
{% endhint %}

## _Consumers_

A configuração de consumidores impacta diretamente no _throughput_ de recebimento e saída de mensagens quando o Kafka Trigger é ativado. O cenário ideal de utilização é ter a mesma quantidade de _consumers_ configurados e partições em determinado tópico.

Caso haja mais _consumers_ do que partições, os _consumers_ excedentes ficarão _idle_ até ocorra um aumento de partições. E, se esse aumento ocorrer, Kafka vai iniciar o processo de rebalanceamento de _consumers_.

### Consumer Group <a href="#consumer-group" id="consumer-group"></a>

É o grupo de consumidores ao qual o seu _pipeline_ vai fazer a subscrição no tópico do Kafka. Um tópico pode ter “n” _Consumer Groups_ e cada um deles vai ter “n” consumidores que consomem os registros do tópico.

* **Cenário 1**

Digamos que exista um tópico chamado _kafka-topic_, um _pipeline_ que utilize um _trigger_ configurado com o _consumer group_ (groupId) nomeado _digibee_ e um segundo _pipeline_ que utilize um _trigger_ configurado com o mesmo tópico, mas com um _consumer group_ (groupId) nomeado digibee-2. Nesse caso, ambos os _pipelines_ receberão as mesmas mensagens.\


* **Cenário 2**

Digamos que exista um tópico chamado _kafka-topic_, um _pipeline_ que utilize um _trigger_ configurado com o _consumer group_ (groupId) nomeado _digibee_ e um segundo _pipeline_ que utilize um _trigger_ configurado com o mesmo tópico e _consumer group_ (digibee). Ambos os _pipelines_ vão receber as mensagens passadas por esse tópico. No entanto, o Kafka fica encarregado de fazer o balanceamento das partições entre os _consumers_ cadastrados nos dois _triggers_. Nesse caso, ambos os _pipelines_ vão receber mensagens de forma intercalada, de acordo com a distribuição das partições.

## Tecnologia <a href="#tecnologia" id="tecnologia"></a>

### **Autenticação usando Kerberos** <a href="#autenticao-usando-kerberos" id="autenticao-usando-kerberos"></a>

Para utilizar a autenticação via Kerberos no _**Kafka Trigger**_ é necessário ter cadastrado o arquivo de configuração “krb5.conf” no parâmetro de _Realm_. Caso não tenha feito isso, acione o nosso suporte via _chat_. Após concluir esse passo, basta configurar corretamente uma conta do tipo Kerberos e utilizá-la no componente.

### Formato de mensagem na entrada do pipeline <a href="#h_7510e36b4b" id="h_7510e36b4b"></a>

_Pipelines_ associados ao Kafka Trigger recebem a seguinte mensagem como entrada:

```
{
  "data": [
    {
      "data": <STRING conteúdo da mensagem>,
      "topic": <STRING O tópico do qual o registro é recebido>,
      "offset": <LONG A posição do registro na partição Kafka correspondente>,
      "partition": <INT A partição da qual o registro é recebido>,
      "success": <BOOLEAN Indica se a mensagem individual foi consumida com sucesso ou não>,
      "headers": {
          "header1": "value1", … (quando incluídos)
      }
    }
  ],
  "success": <BOOLEAN Indica se todas as mensagens foram consumidas com sucesso ou não>
}
```

\
