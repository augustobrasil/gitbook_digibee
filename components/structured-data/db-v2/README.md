---
description: >-
  Descubra mais sobre o componente DB V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# DB V2

O **DB V2** efetua operações de _Select_, _Insert_, _Delete_ e _Update_ e também faz chamadas em _Procedures_, retornando os valores para uma estrutura JSON. Para consultar quais os bancos de dados suportados por esse componente, leia a [documentação Bancos de dados suportados](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados).

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="151">Parâmetro</th><th width="359">Descrição</th><th width="140.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operação a ser realizada (<em>Query</em> ou <em>Procedure</em>).</td><td><em>Query</em></td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente para se conectar. Contas suportadas: <em>Basic</em> e Kerberos.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Database URL</strong></td><td>Define um <em>Database</em> URL.</td><td>jdbc:mysql://35.223.175.97/db-training</td><td><em>String</em></td></tr><tr><td><strong>SQL Statement</strong> <code>(DB)</code></td><td>Aceita qualquer SQL <em>statement</em> suportado pelo banco de dados subjacente. Expressões com <em>Double Braces</em> são permitidas. Ex.: {{ message.id }}.</td><td>SELECT DATE_FORMAT(SYSDATE(), '%Y-%m-%d') as DATA</td><td><em>String</em></td></tr><tr><td><strong>Batch</strong></td><td>Se a opção estiver habilitada, é realizado o processamento em lote.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Rollback On Error</strong></td><td>Se esta opção estiver habilitada, os <em>commits</em> das operações são executados apenas se todas forem bem sucedidas. Caso contrário, será executada uma reversão de todas as operações em lote.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Batch Items</strong></td><td>Se <strong>Batch</strong> estiver ativado, especifique os itens do <em>batch</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, e o resultado mostrará o valor false para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Blob As File</strong></td><td>Se a opção estiver habilitada, todos os parâmetros <em>Blob</em> para operações <em>Query</em> ou <em>Procedure</em> deverão receber o caminho do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Clob As File</strong></td><td>Se a opção estiver habilitada, todos os parâmetros <em>Clob</em> para operações <em>Query</em> ou <em>Procedure</em> deverão receber o caminho do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Charset</strong></td><td>Nome do código dos caracteres para a leitura do arquivo.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Propriedades específicas de conexão e banco de dados definidas pelo usuário.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Type Properties</strong></td><td>Clique no botão <strong>Add</strong> para ativar os seguintes parâmetros adicionais: <strong>Key</strong>, <strong>Type</strong>, <strong>Out Parameter Name</strong> e <strong>Parameter Type</strong>.</td><td>N/A</td><td>Opções de <em>Type Properties</em></td></tr><tr><td><strong>Key</strong></td><td>Faz referência a uma propriedade declarada atráves de expressão <em>Double Braces</em> no <em>SQL Statement</em> no caso de <em>Procedures</em> e <em>INSERT Queries</em> que tratam dos tipos de dados CLOB/BLOB. Veja mais sobre esse parâmetro na seção abaixo.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Type</strong></td><td>O tipo de dado da propriedade que é declarado no <em>SQL Statement</em>.</td><td>VARCHAR</td><td><em>String</em></td></tr><tr><td><strong>Out Parameter Name</strong></td><td>Define o nome do parâmetro <em>Out</em> no caso de um <strong>Parameter Type</strong> tipo OUT ou INOUT.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Parameter Type</strong></td><td><p>Define o tipo de uso da propriedade declarada no <em>SQL Statement</em>.<br></p><p>As opções são IN, OUT ou INOUT.</p></td><td>IN</td><td><em>String</em></td></tr><tr><td><strong>Keep Connection</strong></td><td>Se a opção estiver habilitada, as conexões com o banco de dados serão mantidas por no máximo 30 minutos; caso contrário, serão mantidas por 5 minutos.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Permite definir uma <em>Query</em> a ser executada antes da definida no <em>SQL Statement</em> para garantir que a conexão com o banco de dados seja estabelecida e erros sejam evitados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Pool Size By Actual Consumers</strong></td><td>Se a opção estiver habilitada, o número de conexões agrupadas é igual ao número de consumidores configurados na implantação do <em>pipeline</em>. Se a opção estiver desativada, o tamanho do pool será determinado pelo tamanho da implantação do <em>pipeline</em>, independentemente do número de consumidores.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Exclusive DB Pool</strong></td><td>Se a opção estiver habilitada, um novo <em>pool</em> não compartilhado sempre é criado para uso exclusivo desse componente. Se a opção estiver desativada, um pool poderá ser compartilhado entre os componentes se a URL for a mesma.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Output Column From Label</strong></td><td>Para alguns bancos de dados, se seu <em>Select</em> usar um alias, você deve habilitar este sinalizador para que o nome da coluna seja exibido exatamente como o alias.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Connection Test Query</strong></td><td><em>SQL statement</em> a ser usado antes de cada conexão ser estabelecida. Este é um parâmetro opcional e deve ser usado com bancos de dados que não fornecem informações confiáveis sobre o status da conexão.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Raw SQL Statement</strong> <code>(DB)</code></td><td>Se a opção estiver ativada, o parâmetro <strong>SQL Statement</strong> permite o uso de <em>queries</em> dinâmicas através de declarações <em>Double Braces</em>. Ao utilizar essa funcionalidade, você deve garantir que o pipeline possua mecanismos de segurança contra instruções SQL indesejadas (<em>SQL Injection</em>). Veja mais sobre esse parâmetro na <a href="./#db-v2-em-ao">seção</a> abaixo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>Quando a opção estiver ativada, o componente irá usar a conta dinamicamente. Quando estiver desativada, a conta será usada estaticamente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Account Name</strong></td><td>Nome da conta a ser definida. O nome da conta deve ser gerado dinamicamente através do componente <strong>Store Account</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Scoped</strong></td><td>Quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada. Para saber mais sobre a funcionalidade <strong>Scoped</strong>, leia a <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito">documentação de Suporte a credenciais dinâmicas</a>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Informações importantes:**&#x20;

* Ao ativar o uso de credenciais, um _pool_ de conexão é criado cada vez que o _pipeline_ é executado e fechado quando a execução estiver completa. Os _pools_ de conexão continuarão a ser comunicados entre os conectores do banco se a mesma configuração for aplicada entre eles.
* Atualmente, os parâmetros **Use Dynamic Account**, **Account Name** e **Scoped** podem ser usados apenas no Pipeline Engine v2 e estão disponíveis em fase Beta Restrito. Para saber mais, [leia o artigo Progama Beta.](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta)&#x20;
* Em casos onde um banco de dados Apache Hive é usado, os dados de _Updatecount_ podem estar indisponíveis devido a uma característica do sistema. Essa informação estará disponível apenas se o controle do _updated row count_ estiver habilitado no servidor Apache Hive. [Para mais informações sobre suporte Apache Hive para a Digibee Integration Platform, leia o artigo Banco de dados suportados.](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados#apache-hive)
{% endhint %}

## Informações adicionais de parâmetros <a href="#db-v2-em-ao" id="db-v2-em-ao"></a>

### Key

O parâmetro **Key** faz referência a uma propriedade declarada através de uma expressão _Double Braces_ no _SQL Statement_ em caso de _Procedures_ e INSERT _Queries_ que tratam dos tipos de dados CLOB/BLOB. Toda declaração _Double Braces_ tem um _index_ que deve ser usado para configurar esse parâmetro.

Exemplo:

`INSERT INTO TABLE (MY_CLOB, MY_BLOB, MY_STRING) VALUES ({{ message.clob }}, {{ message.blob }}, {{ message.string }})`

Nesse caso, temos _index_ 0 para `{{ message.clob }}`, 1 para `{{ message.blob }}` e 2 para `{{ message.string }}` .

### Raw SQL Statement <a href="#db-v2-em-ao" id="db-v2-em-ao"></a>

Para trazer mais flexibilidade ao utilizar o **DB V2**, podemos ativar a opção **Raw SQL Statement**, configurar previamente uma _query_ e referenciá-la via _Double Braces_ no parâmetro **SQL Statement** da seguinte maneira:

#### **Query definida previamente via Template Transformer**

<figure><img src="../../../.gitbook/assets/DB V2 - Raw SQL 01 - apr 23.png" alt=""><figcaption></figcaption></figure>

#### **Ativação do Raw SQL Statement**

<figure><img src="../../../.gitbook/assets/DB v2 - Raw SQL 02 - apr 23.png" alt=""><figcaption></figcaption></figure>

#### **Query referenciada no parâmetro SQL Statement**

<figure><img src="../../../.gitbook/assets/DB V2 - Raw SQL 03 - apr 23.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Importante:** como boa prática, recomendamos fortemente que ao ativar a opção **Raw SQL Statement**, as _queries_ sejam definidas previamente através do componente [**Template Transformer**](https://docs.digibee.com/documentation/components/tools/template-transformer). O uso do **Template Transformer** permite validar parâmetros através da tecnologia FreeMarker e também a declaração de parâmetros via _Double Braces_. Estes parâmetros não são resolvidos pelo **Template Transformer** e sim pelo componente **DB V2**, que por padrão configura e valida os parâmetros da instrução SQL previamente (_PreparedStatement_). Ao aplicar essas medidas de segurança, você diminui os riscos de ataques do tipo _SQL Injection_.
{% endhint %}

Na imagem abaixo, temos à esquerda um exemplo do uso recomendado do componente (com o _Double Braces_ na cláusula _WHERE_, no destaque verde); e à direita um exemplo do uso não recomendado (com o FreeMarker na cláusula _WHERE_, no destaque vermelho) que pode trazer riscos à segurança do _pipeline_:

<figure><img src="../../../.gitbook/assets/DB V2 - Raw SQL 04 exp - apr 23.png" alt=""><figcaption></figcaption></figure>

## DB V2 em Ação <a href="#db-v2-em-ao" id="db-v2-em-ao"></a>

### Batch mode <a href="#batch-mode" id="batch-mode"></a>

Quando for necessário realizar um processamento em lote de algumas instruções, você pode realizar chamadas em modo _batch_ nas _queries_.

\
**Exemplo**

Digamos que você precise informar no componente um _array_ de objetos, que serão utilizados nessa execução em _batch_:

**Itens**

```
[   { 
    "name": "Mathews", "type":"A"
    }, { 
    "name": "Jules", "type":"A"
    }, { 
    "name": "Raphael", "type":"B"
    } 
]
```

E na instrução SQL, você deverá informá-lo da seguinte maneira:

**SQL**

`INSERT INTO TABLE VALUES ( {{ item.name }}, {{ item.type }} )`

Quando você utiliza expressões em _Double Braces_ \{{ item.name \}}, uma iteração é feita dentro do _array_ (informado em itens) e uma propriedade correspondente é buscada dentro do objeto. Nesse caso, a propriedade é "name".

Após a execução, 3 registros são inseridos. O retorno esperado é:

```
{ 
    "totalSucceeded":3, 
    "totalFailed":0 
}
```

Caso uma das execuções falhe, será retornado um objeto com a propriedade "error":

```
{ 
    "totalSucceeded":1, 
    "totalFailed":1 
}
```

Caso uma das execuções falhe, será retornado um objeto com a propriedade "errors":

```
{ 
    "totalSucceeded":1, 
    "totalFailed":1,
    "errors": ["erro1", "error2"]
}
```

{% hint style="info" %}
**Importante:** os erros retornados na propriedade “errors” variam conforme o _driver_ do banco. Alguns _drivers_ não retornam todos os erros ocorridos durante a execução em modo _batch_.
{% endhint %}

### Rollback On Error <a href="#rollback-on-error" id="rollback-on-error"></a>

Se essa opção estiver ativada, os _commits_ das operações serão realizados apenas se todas elas forem bem sucedidas. Do contrário, será feito o _rollback_ de todas as operações _batch_.

Se a opção estiver inativa, então o _commit_ e as alterações bem sucedidas por _commit_ serão feitas mesmo que ocorra alguma falha entre as execuções.

{% hint style="info" %}
**Importante:** para alguns bancos de dados, principalmente para o Oracle, não é possível retornar o número consolidado execuções bem ou mal sucedidas.&#x20;
{% endhint %}

Caso algum erro ocorra, um objeto contendo todos os erros será retornado (dentro da propriedade "errors") e consolidado com o valor -1 também será retornado:

```
{ 
    "totalSucceeded":-1, 
    "totalFailed":-1,
    "errors": ["erro1", "error2"], 
    "success": false
}
```

Para outros bancos, como o Firebird, a ocorrência de erros não é informada. Portanto, um objeto sem nenhum erro pode ser retornado mesmo que tenha ocorrido uma falha:

```
{ 
    "totalSucceeded":0, 
    "totalFailed":3,
    "errors": ["erro1", "error2"], 
    "success": false
}
```

Para esses casos de erro no _Batch Mode_, não deixe de analisar a propriedade "success". Se ela retornar "false", significa que pelo menos um erro ocorreu durante a execução.

## Pool de conexão <a href="#h_f90a8ac5f6" id="h_f90a8ac5f6"></a>

Por padrão, utilizamos um _pool_ de tamanho baseado nas configurações do _pipeline_ implantado. Por exemplo, caso seja um _pipeline_ SMALL, então o tamanho do _pool_ será de 10. Para o MEDIUM o tamanho seria de 20 e para o LARGE seria de 40.

É possível gerenciar o tamanho do _pool_ na hora da implantação também. Para isso, é necessário habilitar a propriedade **Pool Size By Actual Consumers** no componente. Com isso, é utilizado o que for configurado manualmente na tela de implantação.

Veja na figura abaixo a configuração de um _pipeline_ SMALL com 5 _consumers_. Se você quiser que o _pool_ dos componentes de banco de dados (**DB V2** e **Stream DB V3**) utilize esse tamanho, será preciso habilitar a propriedade “Pool Size By Actual Consumers” em todos os componentes existentes:

![](../../../.gitbook/assets/dbv2-2.png)

{% hint style="info" %}
**Importante:** atenção ao configurar o tamanho do _pool_ manualmente para que não ocorra nenhum _deadlock_ em chamadas concorrentes ao mesmo banco.
{% endhint %}

O nosso _pool_ é compartilhado entre os componentes de banco de dados que acessam o mesmo banco de dados dentro do _pipeline_. Caso seja necessário um _pool_ exclusivo para determinado componente, habilite a propriedade “Exclusive Pool”.

## Tecnologia

### Autenticação via Kerberos

É possível realizar autenticação via Kerberos em componentes de banco de dados. Para isso, basta você:

* informar uma conta do tipo KERBEROS
* configurar um Kerberos principal
* configurar uma _keytab_ (que deve ser a base64 do próprio arquivo _keytab_ gerado)

## Mais cenários de uso com DB V2&#x20;

Veja na documentação a seguir como usar o DB V2 em diferentes cenários:

{% content-ref url="db-v2-cenarios-de-uso.md" %}
[db-v2-cenarios-de-uso.md](db-v2-cenarios-de-uso.md)
{% endcontent-ref %}

### &#x20;<a href="#h_f90a8ac5f6" id="h_f90a8ac5f6"></a>
