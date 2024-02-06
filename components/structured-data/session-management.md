---
description: >-
  Descubra mais sobre o componente Session Management e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Session Management

O **Session Management** implementa o gerenciamento de sessão tradicional e a sua função principal para construção de _pipelines_ é bastante utilizada no armazenamento de dados semelhantes às variáveis em desenvolvimento tradicional.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="172">Parâmetro</th><th width="214">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser executada (<em>Get Data, Put Data, Delete Data</em>).</td><td><em>Get Data</em></td><td><em>String</em></td></tr><tr><td><strong>Session Type</strong></td><td>Sessão para inserir o objeto especificado em <em>Fields</em> (Local ou Global).</td><td>Local</td><td><em>String</em></td></tr><tr><td><strong>Fields</strong></td><td>Objeto a ser especificado - ex. <em>body, data, id.</em></td><td>body, data, id</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong></td><td>Quando esta opção está habilitada, a sessão é isolada de outro subprocesso. Nesse caso, os subprocessos veem sua própria versão dos dados da sessão.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## **Operation**

Esse componente pode ser configurado nas seguintes operações:

* **Get Data:** busca na sessão os objetos especificados no parâmetro **Fields**, que serão inseridos em seguida no corpo da solicitação.&#x20;
* **Put Data:** insere na sessão (Local ou Global) os objetos especificados no parâmetro **Fields**_._
* **Delete Data:** apaga da sessão os objetos especificados no parâmetro **Fields**.

## **Session Type**

### Local <a href="#local" id="local"></a>

Lida com uma sessão onde os valores armazenados estão disponíveis apenas no _pipeline_ em execução corrente.               &#x20;

**Exemplo:** As _tags "body_" e _"data"_ da etapa **Fields** são armazenadas na sessão **Local**.

### Global <a href="#global" id="global"></a>

Lida com uma sessão baseada no _token_ JWT do usuário autenticado, permitindo que _pipelines_ e execuções distintas tenham acesso seguro aos dados armazenados na sessão global do usuário.

Somente será permitido armazenar e acessar dados em sessão **Global** quando o _pipeline_ possuir o [**REST Trigger**](../triggers/rest-trigger.md) ou o [**HTTP Trigger**](../triggers/http-trigger.md) e tiver o _token_ JWT como critério de segurança.

Para executar um _pipeline_ com esse critério de segurança, é necessário que você crie um _pipeline_ de _login_ e utilize o componente [**JWT**](../security-components/jwt-v2.md) para obter um _token_ JWT_._

&#x20;        \
**Exemplo**

* **Step Name:** Session-Management
* **Operation:** Get Data
* **Session Type:** Global
* **Fields:** object

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada e pode fazer uso dela declarando os valores do JSON no campo **Fields**.

### Saída <a href="#sada" id="sada"></a>

O componente não altera nenhuma informação da mensagem de entrada. Portanto, ela é retornada para o componente seguinte ou é utilizada como resposta final se este componente for o último passo do _pipeline_.&#x20;

Ao manter a operação _Get Data_ selecionada, os itens especificados no campo **Fields** serão adicionados à mensagem de saída (caso existam na sessão).
