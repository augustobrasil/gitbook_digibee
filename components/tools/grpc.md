---
description: >-
  Descubra mais sobre o componente gRPC e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# gRPC

O **gRPC** permite a realização de chamadas a serviços gRPC do tipo unário e _client stream_ via _payload_ ou via arquivo.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="261">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Authenticate with client certificates</strong></td><td>Quando ativado, pode selecionar autenticação de cliente com certificados de cliente (mTLS). Use o tipo de conta <em>Certificate Chain</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Authenticate with Google Key</strong></td><td>Quando ativado, pode selecionar a autenticação do cliente com <em>Google Key</em>. Use o tipo de conta <em>Google Key</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Method Type</strong></td><td>Tipo de método que será utilizado na invocação do serviço. Os tipos de métodos suportados são <em><strong>Unary</strong></em>, <em><strong>Client Stream - via Payload</strong></em> e <em><strong>Client Stream - via File</strong></em>.</td><td><em>Unary</em></td><td><em>String</em></td></tr><tr><td><strong>URL</strong></td><td>Endereço de chamada do serviço gRPC. Ex: localhost:50051.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Configura todos os tipos de headers necessários para chamada (ex.: Authorization: Bearer Co4ECg1FeGFtcGxlLnByb3RvIjwKDEh).</td><td>N/A</td><td>Par de chave-valor</td></tr><tr><td><strong>Custom Accounts</strong></td><td>Defina a conta a ser usada em expressões com <em>Double Braces</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Service name</strong></td><td>Nome do serviço que está descrito dentro do arquivo de configuração .proto do servidor gRPC. Aprenda mais em <a href="grpc.md#service-name">Informações adicionais sobre parâmetros</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Method Name</strong></td><td>Nome do método que está descrito dentro do arquivo de configuração .proto do servidor gRPC. Aprenda mais em <a href="grpc.md#method-name">Informações adicionais sobre parâmetros</a>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Proto Descriptor File</strong></td><td>Base64 do arquivo “descriptor” do arquivo .proto. Aprenda mais em <a href="grpc.md#proto-descriptor-file">Informações adicionais sobre parâmetros</a>.</td><td>N/A</td><td><em>String</em> (Base64)</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>O <em>payload</em> de requisição que será enviado ao servidor gRPC. Para o tipo de método <em><strong>Unary</strong></em>, deverá ser utlizado um objeto simples que contenha os campos definidos no arquivo .proto. Para o tipo de método <em><strong>Client Stream - via Payload</strong></em> deverá ser utilizado um <em>array</em> de objetos, onde cada item do <em>array</em> é uma mensagem a ser enviada ao servidor gRPC.</td><td>N/A</td><td>Objeto JSON ou <em>Array</em></td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo que será usado para enviar o <em>payload</em> no modo <em><strong>Client Stream - via File</strong></em>. Esse arquivo deverá ser um arquivo JSON que contenha um <em>array</em> e, dentro desse <em>array</em>, deve haver as mensagens a serem enviadas ao gRPC <em>server</em> de forma assíncrona (<em>stream</em>).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JSON Path</strong></td><td>Expressão JSON Path que irá determinar como será feita a leitura em <em>stream</em> do arquivo JSON. Somente para o tipo de método <em><strong>Client Stream - via File</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Connect Timeout</strong></td><td>Tempo de expiração da conexão com o servidor (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Request Timeout</strong></td><td>Tempo de expiração da chamada de requisição do componente com o servidor gRPC (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

### Informações adicionais sobre parâmetros

#### Service Name

Veja um exemplo de **Service Name** como “Greeter”:

```protobuf
service Greeter {
   rpc helloMethod(Hellorequest) returns (HelloResponse);
​
}
```

#### Method Name

Veja um exemplo de **Method Name** como “helloMethod”:

```protobuf
service Greeter {
   rpc helloMethod(Hellorequest) returns (HelloResponse);
​
}
```

#### Proto Descriptor File

Para usar esse parâmetro, o “descriptor” deve ser gerado primeiro a partir de um arquivo .proto. Para fazer isso, siga os passos abaixo:

1. Gere o arquivo "descriptor" executando o seguinte comando no diretório corrente que estiver localizado o arquivo .proto:

* **Arquivo .proto do diretório:** Example.proto
* **Nome do arquivo descriptor a ser gerado:** proto.desc

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

Faça o download do compilador protoc em [Protocol Buffer Compiler Installation](https://grpc.io/docs/protoc-installation/).

2. Realize o _encode_ deste arquivo para base64:

```
tLmRpZ2liZWUuZ3JwY0IMRGlnaWJlZVByb3RvUAGiAgNITFdiBnByb3RvMw==
```

3. Informe o base64 na propriedade **Proto Descriptor File**.

## Fluxo de mensagens

### Entrada

Espera-se um _payload_ de entrada que será utilizado dentro do parâmetro **Payload** do componente.

### Saída

Ao executar um componente SFTP utilizando as operações _download_, _upload_ ou _move_, a seguinte estrutura de JSON será gerada:

```
{
   "response": {},
   "success": "true"
}
```

* **response:** JSON de resposta recebido do serviço gRPC.
* **success:** "true" se houver uma conexão e o _script_ for executado mesmo se retornar erros no _stderr_.

### Saída com erro

```
{ 
   "success": false, 
   "message": "Something went wrong while trying to call the gRPC server", 
   "error": "java.net.SocketTimeoutException: connect timed out"
}
```

* **success:** “false” quando a operação falha.
* **message:** mensagem sobre o erro.
* **exception:** informação sobre o tipo de erro ocorrido.

Para entender melhor o fluxo das mensagens na Plataforma, leia a [documentação sobre Processamento de mensagens](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/processamento-de-mensagens).

## Componente gRPC em ação

### Unary

Dado o seguinte arquivo .proto:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
 rpc unary (HelloRequest) returns (HelloReply) {}
 rpc clientStream (stream HelloRequest) returns (HelloReply) {}
 rpc serverStream (HelloRequest) returns (stream HelloReply) {}
 rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
 string name = 1;
 string address = 2;
}
​
message HelloReply {
 string message = 1;
 int32 status = 2;
}
```

Primeiramente, é preciso gerar o arquivo “descriptor”:

1. Dentro do diretório do arquivo, execute o comando:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. Com o “descriptor” em mão, gere o base64 do arquivo proto.desc e adicione-o no campo **Proto Descriptor File**.

Configurações do componente:

**Method Type:** Unary

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** unary

**Proto Descriptor File:** \<BASE64 DO ARQUIVO DESCRIPTOR GERADO ACIMA>

**Payload:**

```
{
   "name": "Charles",
   "address": "390 Fifth Avenue"
}
```

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** desabilitado

**Resposta**

```
{
   "message": "Hi Charles",
   "status": 200
}
```

### Client Stream - via Payload

Dado o arquivo .proto:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
 rpc unary (HelloRequest) returns (HelloReply) {}
 rpc clientStream (stream HelloRequest) returns (HelloReply) {}
 rpc serverStream (HelloRequest) returns (stream HelloReply) {}
 rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
 string name = 1;
 string address = 2;
}
​
message HelloReply {
 string message = 1;
 int32 status = 2;
}
```

Primeiramente, é preciso gerar o arquivo “descriptor”:

1. Dentro do diretório do arquivo, execute o comando:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. Com o “descriptor” em mão, gere o base64 do arquivo proto.desc e adicione-o no campo **Proto Descriptor File**.

Configurações do componente:

**Method Type:** Client Stream - via Payload

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** clientStream

**Proto Descriptor File:** \<BASE64 DO ARQUIVO DESCRIPTOR GERADO ACIMA>

**Payload:**

```
[
   {
       "name": "Charles",
       "address": "390 Fifth Avenue"
   },
   {
       "name": "Paul",
       "address": "32 Seventh Avenue"
   },
   {
       "name": "Yan",
       "address": "12 Fourth Avenue"
   }
]
```

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** desabilitado

**Resposta**

```
{
   "message": "Hi Charles, Paul and Yan",
   "status": 200
}
```

### Client Stream - via File

Dado o seguinte arquivo .proto:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
 rpc unary (HelloRequest) returns (HelloReply) {}
 rpc clientStream (stream HelloRequest) returns (HelloReply) {}
 rpc serverStream (HelloRequest) returns (stream HelloReply) {}
 rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
 string name = 1;
 string address = 2;
}
​
message HelloReply {
 string message = 1;
 int32 status = 2;
}
```

Primeiramente, é preciso gerar o arquivo “descriptor”:

1. Dentro do diretório do arquivo, execute o comando:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. Com o “descriptor” em mão, gere o base64 do arquivo proto.desc e adicione-o no campo **Proto Descriptor File**.

Configurações do componente:

**Method Type:** Client Stream - via Payload

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** clientStream

**Proto Descriptor File:** \<BASE64 DO ARQUIVO DESCRIPTOR GERADO ACIMA>

**File Name:** file.json

**File Name**: file.json

{% code title="file.json" %}
```
{ 
    "infos": [
        {
            "name": "Charles",
            "address": "390 Fifth Avenue"
        },
        {
            "name": "Paul",
            "address": "32 Seventh Avenue"
        },
        {
            "name": "Yan",
            "address": "12 Fourth Avenue"
        }
    ]
}
```
{% endcode %}

**JSON Path:** $.infos\[\*]

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** desabilitado

**Resposta**

```
{
   "message": "Hi Charles, Paul and Yan",
   "status": 200
}
```
