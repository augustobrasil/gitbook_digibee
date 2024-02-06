---
description: >-
  Descubra mais sobre o componente Stream DB V3 e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Stream DB V3



O **Stream DB V3** permite estabelecer uma conexão com um serviço que suporta o protocolo JDBC (_Java Database Connectivity_) e executar instruções SQL (_Structured Query Language_). Para consultar quais os bancos de dados suportados por esse componente, leia a [documentação Bancos de dados suportados](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados).

Diferentemente do componente [**DB V1**](db-v1.md), o **Stream DB** foi desenvolvido para realizar execução em lotes, ou seja, cada retorno (linha resultante ou _row_) da instrução SQL executada é tratada individualmente através de um _subpipeline_, podendo conter seu próprio fluxo de processamento. [Leia o artigo Subpipelines para saber mais.](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/subpipelines)

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="206">Parâmetro</th><th width="285">Descrição</th><th width="159.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Para o componente fazer a autenticação a um serviço JDBC, é necessário usar uma <em>account</em> do tipo <em>Basic</em> ou Kerberos (veja o tópico <a href="stream-db-v3.md#autenticao-via-kerberos">Autenticação via Kerberos</a>).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Database URL</strong> <code>(DB)</code></td><td>URL (<em>Uniform Resource Locator</em>) para estabelecer conexão ao servidor de banco de dados com suporte ao protocolo JDBC. Este parâmetro aceita <em>Double Braces</em>.</td><td>jdbc:mysql://35.223.175.97/db-training</td><td><em>String</em></td></tr><tr><td><strong>SQL Statement</strong></td><td>Instrução SQL a ser executada.</td><td>select * from clientes LIMIT 2</td><td><em>String</em></td></tr><tr><td><strong>Column Name</strong></td><td>Caso haja um erro no processamento do <em>subpipeline onProcess</em>, o valor associado à coluna definida neste campo será adicionado à mensagem de erro, em um novo campo chamado "<em>processedId</em>" e que poderá ser manipulado pelo <em>subpipeline onException</em>.</td><td>codigo</td><td><em>String</em></td></tr><tr><td><strong>Parallel Execution Of Each Iteration</strong></td><td>Quando ativada, essa opção faz com que cada uma das passagens pelo <em>subpipeline</em> seja feita em paralelo, reduzindo o tempo de execução total. No entanto, não há qualquer garantia de que os itens sejam executados na ordem retornada pelo banco de dados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Blob As File</strong></td><td>Se ativada, a opção faz com que os campos do tipo blob sejam armazenados no contexto do <em>pipeline</em> como arquivo; do contrário, os campos são armazenados como textos normais (<em>strings</em>) e codificados em base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Clob As File</strong></td><td>A opção faz com que os campos do tipo clob sejam armazenados no contexto do <em>pipeline</em> como arquivo; do contrário, os campos são armazenados como textos normais (<em>strings</em>).</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Charset</strong></td><td>Essa opção é exibida apenas quando a opção <em><strong>Clob As File</strong></em> for ativada. Esse parâmetro permite configurar o <em>encoding</em> de arquivos clob.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>A habilitação desse parâmetro suspende a execução do <em>pipeline</em> apenas quando há uma ocorrência grave na estrutura da iteração, impedindo a sua conclusão por completo. A ativação do parâmetro <em><strong>Fail On Error</strong></em> não tem ligação com erros ocorridos nos componentes utilizados para a construção dos <em>subpipelines (onProcess</em> e <em>onException).</em></td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Propriedades de conexão específicas definidas pelo usuário.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Keep Connections</strong></td><td>Se ativada, a opção vai manter as conexões com a base de dados por no máximo 30 minutos; do contrário, será por apenas 5 minutos.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Se ativada, as seguintes configurações estarão disponíveis:</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Pool Size By Actual Consumers</strong></td><td>Se a opção estiver ativada, o número de <em>pooled connections</em> será equivalente ao número de consumers configurados durante a implantação do <em>pipeline</em>. Do contrário, o tamanho do <em>pool</em> é dado pelo tamanho de implantação do <em>pipeline</em>, independentemente do número de <em>consumers</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Exclusive DB Pool</strong></td><td>Se a opção estiver ativada, um novo <em>pool</em> não-compartilhado sempre será criado para uso exclusivo deste componente. Do contrário, um <em>pool</em> poderá ser compartilhado entre componentes se a URL for a mesma.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Output Column From Label</strong></td><td>Para alguns bancos de dados, é importante manter esta opção ativada caso o seu <em>SELECT</em> esteja utilizando algum alias, pois dessa maneira garante-se que o nome da coluna será exibido da mesma forma que o alias configurado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Connection Test Query</strong></td><td>Instrução SQL a ser executada antes que cada conexão seja estabelecida (i.e. <em><code>select 1 from dual</code></em>). Esse parâmetro é opcional e deve ser aplicado apenas a bancos de dados que não possuem informações confiáveis sobre o status da conexão.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Raw SQL Statement</strong> <code>(DB)</code></td><td>Se a opção estiver ativada, o parâmetro <strong>SQL Statement</strong> permite o uso de queries dinâmicas através de declarações <em>Double Braces</em>. Ao utilizar essa funcionalidade, você deve garantir que o pipeline possua mecanismos de segurança contra instruções SQL indesejadas (<em>SQL Injection</em>). Veja mais sobre esse parâmetro na <a href="stream-db-v3.md#raw-sql-statement">seção</a> abaixo.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
Em casos onde um banco de dados Apache Hive é usado, os dados de _Updatecount_ podem estar indisponíveis devido a uma característica do sistema. Essa informação estará disponível apenas se o controle do _updated row count_ estiver habilitado no servidor Apache Hive. [Para mais informações sobre suporte Apache Hive para a Digibee Integration Platform, leia o artigo Banco de dados suportados.](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados#apache-hive)
{% endhint %}

## Informações adicionais sobre parâmetros

### Column Name

Veja o seguinte exemplo sobre a mensagem de erro em **Column Name**:

```
{
  "timestamp": 1600797662733,
  "error": "Error message",
  "code": 500,
  "processedId": "2"
}
```

### Blob As File

Se **Blob As File** estiver ativado, os campos do tipo blob são armazenados como no exemplo a seguir:&#x20;

```
// "Blob As File" true
{
  "id": 12,
  "blob": "d3X8YK.file",
}
```

Do contrário, os campos do tipo blob são armazenados como mostrado abaixo:

{% code overflow="wrap" %}
```
// "Blob As File" false
{
  "id": 12,
  "blob": "iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAIAAACQkWg2AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAeSURBVDhPY1Da6EMSYiBJNVDxqAZiQmw0lAZHKAEAaskfEED3lr0AAAAASUVORK5CYII="
}
```
{% endcode %}

### Clob As File

Se **Clob As File** estiver ativado, os campos do tipo clob são armazenados como no exemplo a seguir:&#x20;

```
// "Clob As File" true
{
  "id": 15,
  "clob": "f7X9AS.file",
}
```

Do contrário, os campos do tipo clob são armazenados como mostrado abaixo:

```
// "Clob As File" false
{
  "id": 15,
  "clob": "AAAAABBBBBCCCC”
}
```

## Raw SQL Statement

Para trazer mais flexibilidade ao utilizar o **Stream DB V3**, podemos ativar a opção **Raw SQL Statement**, configurar previamente uma _query_ e referenciá-la via _Double Braces_ no parâmetro **SQL Statement** da seguinte maneira:

### **Query definida previamente via Template Transformer**

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 01 - apr 23.png" alt=""><figcaption></figcaption></figure>

### **Ativação do **_**Raw SQL Statement**_

<figure><img src="../../.gitbook/assets/DB v2 - Raw SQL 02 - apr 23.png" alt=""><figcaption></figcaption></figure>

### **Query referenciada no parâmetro SQL Statement**

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 03 - apr 23.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Importante:** como boa prática, recomendamos fortemente que ao ativar a opção **Raw SQL Statement**, as _queries_ sejam definidas previamente através do componente [**Template Transformer**](https://docs.digibee.com/documentation/components/tools/template-transformer)_._ O uso do **Template Transformer** permite validar parâmetros através da tecnologia _FreeMarker_ e também a declaração de parâmetros via _Double Braces_. Estes parâmetros não são resolvidos pelo **Template Transformer** e sim pelo componente **Stream DB V3**, que por padrão configura e valida os parâmetros da instrução SQL previamente (_PreparedStatement_). Ao aplicar essas medidas de segurança, você diminui os riscos de ataques do tipo _SQL Injection_.
{% endhint %}

Na imagem abaixo, temos à esquerda um exemplo do uso recomendado do componente (com o _Double Braces_ na cláusula _WHERE_, no destaque verde); e à direita um exemplo do uso não recomendado (com o FreeMarker na cláusula _WHERE_, no destaque vermelho) que pode trazer riscos à segurança do _pipeline_:

<figure><img src="../../.gitbook/assets/DB V2 - Raw SQL 04 exp - apr 23.png" alt=""><figcaption></figcaption></figure>

## Tecnologia <a href="#tecnologia" id="tecnologia"></a>

### **Autenticação via Kerberos** <a href="#autenticao-via-kerberos" id="autenticao-via-kerberos"></a>

Para realizar autenticação a um banco de dados via Kerberos é necessário:

* informar uma conta (_account_) do tipo KERBEROS;
* configurar um Kerberos principal;
* configurar uma _keytab_ (que deve ser a base64 do próprio arquivo _keytab_ gerado).

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Estrutura de mensagem disponível no subpipeline onProcess** <a href="#estrutura-de-mensagem-disponvel-no-subpipeline-onprocess" id="estrutura-de-mensagem-disponvel-no-subpipeline-onprocess"></a>

Uma vez que a instrução SQL é executada, o _subpipeline_ será disparado recebendo o resultado da execução por meio de uma mensagem na seguinte estrutura:

```
{  
    "coluna1": "dado1",   
    "coluna2": "dado2",  
    "coluna3": "dado3"
}
```

### Saída com erro <a href="#erro" id="erro"></a>

```
{   
    "code": error_code,   
    "error": mensagem de erro,   
    "processId": the_id_column_value
}
```

### Saída <a href="#sada" id="sada"></a>

Após a execução do componente, é retornada uma mensagem na seguinte estrutura:

```
{   
    "total": 0,   
    "success": 0,   
    "failed": 0
}
```

* **total:** número total de linhas processadas.
* **success:** número total de linhas processadas com sucesso.
* **failed:** número total de linhas cujo processamento falhou.

{% hint style="info" %}
**Importante:** para detectar se uma linha foi processada corretamente, cada _subpipeline_ _onProcess_ deve responder com { _"success": true_ } a cada elemento processado.
{% endhint %}

O **Stream DB V3** realiza processamento em lote. [Consulte o artigo Processamento em lote para saber mais sobre este conceito.](https://docs.digibee.com/documentation/v/pt-br/tutorials-and-best-practices/processamento-em-lote)

## Pool de conexão <a href="#h_cf06a705b9" id="h_cf06a705b9"></a>

Por padrão, utilizamos um _pool_ com tamanho baseado nas configurações do _pipeline_ implantado. Caso seja um _pipeline Small_, então o tamanho do _pool_ será de 10; para o _Medium_, será de 20; e para o _Large_, de 40.

É possível gerenciar o tamanho do _pool_ também na hora da implantação. Para isso, será necessário habilitar o parâmetro **Pool Size By Actual Consumers** no componente. Com isso, será utilizado o que for configurado manualmente na tela de implantação.

No exemplo da figura abaixo, foi configurado um _pipeline_ _Small_ com 5 _consumers_. Se você quiser que o _pool_ dos componentes de banco de dados ([DB V2](db-v2/) e Stream DB V3) utilize esse tamanho, é necessário habilitar o parâmetro **Pool Size By Actual Consumers** em todos os componentes existentes.

![](<../../.gitbook/assets/streamdb v3.png>)

Tenha atenção redobrada ao configurar o tamanho do _pool_ manualmente para que não ocorra nenhum _deadlock_ em chamadas concorrentes ao mesmo banco.

O nosso _pool_ é compartilhado entre os componentes de banco de dados que acessam o mesmo banco de dados dentro do _pipeline_. Caso seja necessário um _pool_ exclusivo para um determinado componente, habilite o parâmetro **Exclusive DB Pool**.
