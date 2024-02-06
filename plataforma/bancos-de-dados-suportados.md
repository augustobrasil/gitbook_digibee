---
description: >-
  Descubra os tipos e versões de bancos de dados suportados pela Digibee
  Integration Platform e como eles podem simplificar a criação de pipelines de
  integração para todos os usuários.
---

# Bancos de dados suportados

Você pode acessar bancos de dados usando componentes específicos, tais como:

* [DB V2](../components/structured-data/db-v2/)
* [Stream DB V3](../components/structured-data/stream-db-v3.md)
* [Stored Procedure](../components/structured-data/stored-procedure.md)

O suporte aos bancos de dados mencionados aqui não se aplicam a versões descontinuadas de componentes. Recomendamos que você não use componentes descontinuados. Alguns exemplos de componentes descontinuados são:

* [Stream DB V1](../components/structured-data/stream-db-v1.md)
* [DB V1](../components/structured-data/db-v1.md)

Atualmente a Digibee Integration Platform suporta os seguintes bancos de dados:

## DB2

A Digibee Integration Platform oferece suporte ao _driver_ JDBC IBM DB2 e cobre as seguintes versões:

* Versão do DB2 level: 11.5
* Versão do _driver_: 4.26.14

**String de conexão**&#x20;

```
jdbc:db2://127.0.0.1:1724/dbtest
```

{% hint style="info" %}
As funcionalidades disponibilizadas são baseadas na [documentação oficial do DB2](https://www.ibm.com/support/pages/db2-jdbc-driver-versions-and-downloads). O _driver_ licenciado pela sua empresa junto a IBM deve ser ativado para se conectar às versões suportadas dos bancos de dados. \
\
Este processo é tratado pelo time de suporte da Digibee, mas você deve fornecer o _driver_ JDBC IBM DB2 para ativação. Este processo é exclusivo ao _realm_ do cliente solicitante.
{% endhint %}

## Apache Hive

A Plataforma Digibee oferece suporte para o Apache Hive somente via JDBC Connector 2.6.17 for Cloudera Enterprise e cobre as seguintes versões:

* Apache Hive versões 1.0.0 a 3.1

**String de conexão**

```
 jdbc:hive2://localhost:10002

```

{% hint style="info" %}
As funcionalidades disponibilizadas são baseadas na [documentação oficial do _driver_ JDBC Cloudera](https://docs.cloudera.com/documentation/other/connectors/hive-jdbc/2-6-17.html). O _driver_ licenciado pela sua empresa junto a Cloudera deve ser ativado para se conectar às versões suportadas dos bancos de dados. \
\
Este processo é tratado pelo time de suporte da Digibee, mas você deve fornecer o _driver_ JDBC Cloudera para ativação. Este processo é exclusivo ao _realm_ do cliente solicitante.
{% endhint %}

## Teradata Database

A Digibee Integration Platform oferece suporte às seguintes versões:

* Teradata Database 16.10, 16.20, 17.00, 17.10, e 17.20.

**String de conexão**

```
jdbc:teradata://192.168.64.2/DATABASE=DBC,DBS_PORT=1025
```

{% hint style="info" %}
O _driver_ licenciado pela sua empresa junto à Teradata deve ser ativado para se conectar às versões suportadas dos bancos de dados. \
\
Este processo é tratado pelo time de suporte da Digibee, mas você deve fornecer o _driver_ JDBC Teradata para ativação. Este processo é exclusivo ao _realm_ do cliente solicitante.
{% endhint %}

## SQL Server <a href="#sql-server" id="sql-server"></a>

A Digibee Integration Platform oferece suporte às seguintes versões:

* Microsoft SQL Server 2019
* Microsoft SQL Server 2017
* Microsoft SQL Server 2016
* Microsoft SQL Server 2014
* Microsoft SQL Server 2012
* Microsoft SQL Server 2008 R2
* Azure SQL Database
* Azure SQL Data Warehouse or Parallel Data Warehouse
* Azure SQL Managed Instance (Extended Private Preview)

{% hint style="info" %}
Embora a conexão através da versão 2019 do Microsoft SQL Server seja suportada, nem todas as funcionalidades desta versão poderão estar disponíveis.
{% endhint %}

**String de Conexão**

```
jdbc:sqlserver://[serverName[\instanceName][:portNumber]]
```

## Oracle <a href="#oracle" id="oracle"></a>

A Digibee Integration Platform oferece suporte às seguintes versões:

* 19.x
* 18.3
* 12.2 ou 12cR2
* 12.1 ou 12cR1
* 11.2 ou 11gR2

**Strings de Conexão**

* Sintaxe Oracle Net

```
jdbc:oracle:thin:@(DESCRIPTION=
(LOAD_BALANCE=on)
(ADDRESS_LIST=
(ADDRESS=(PROTOCOL=TCP)(HOST=host1) (PORT=5221))
(ADDRESS=(PROTOCOL=TCP)(HOST=host2)(PORT=5221)))
(CONNECT_DATA=(SERVICE_NAME=orcl)))
```

{% hint style="info" %}
No banco de dados da Oracle, a _string_ de conexão pode conter múltiplos _endpoints_. Se sua _string_ de conexão contém mais de um _endpoint_, o _driver_ da Oracle realizará tentativas de conexão com cada um dos _endpoints_, continuando até que a tentativa seja bem sucedida ou não haja mais _endpoints_ disponíveis.

Portanto, se sua _string_ de conexão contiver múltiplos _endpoints_ e você configurar o parâmetro `"oracle.net.connect_timeout"` em **Custom Connection Properties** dos componentes [DB V2](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2), [Stream DB V3](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stream-db-v3) e [Stored Procedure](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stored-procedure), é importante saber que o _timeout_ se aplica a cada _endpoint_ especificado individualmente, e não de maneira global a todos os _endpoints_ ao mesmo tempo.
{% endhint %}

* Sintaxe com Nome de Serviço

```
jdbc:oracle:thin:@//localhost:5221/orcl
```

{% hint style="info" %}
Apenas conexões do tipo _thin_ são suportadas. Ao acessar as bases de dados especificadas nessa _string_ de conexão, você concorda que possui as licenças Oracle necessárias.
{% endhint %}

## MySQL <a href="#mysql" id="mysql"></a>

A Digibee Integration Platform oferece suporte às seguintes versões:

* 5.6
* 5.7
* 8.0

**String de Conexão**

```
jdbc:mysql://<host>:<port>/<database>
```

{% hint style="info" %}
A Digibee Integration Platform desabilita a interpretação de _strings_ Maria DB pelo _driver_ MySQL. No entanto, é possível utilizar o _driver_ Maria DB para se conectar a versões mais antigas do MySQL.
{% endhint %}

## Maria DB <a href="#maria-db" id="maria-db"></a>

A Digibee Integration Platform oferece suporte à seguinte versão:

* 5.5.3+

**String de Conexão**

```
jdbc:mariadb://<host>:<port>/<database>
```

{% hint style="info" %}
A Digibee Integration Platform desabilita a interpretação de _strings_ Maria DB pelo _driver_ MySQL.
{% endhint %}

## Progress <a href="#progress" id="progress"></a>

A Digibee Integration Platform oferece suporte à seguinte versão:

* OpenEdge 10.1.x+

**String de Conexão**

```
jdbc:datadirect:openedge://hostname:port
```

## Sybase <a href="#sybase" id="sybase"></a>

A Digibee Integration Platform oferece suporte à seguinte versão:

* SAP/Sybase ASE

**String de Conexão**

```
jdbc:sybase:Tds:host:port
```

## PostgreSQL <a href="#postgresql" id="postgresql"></a>

A Digibee Integration Platform oferece suporte a todas as versões.

**String de Conexão**

```
jdbc:postgresql://host:port/database
```

## OLAP DataSource via MDX <a href="#olap-datasource-via-mdx" id="olap-datasource-via-mdx"></a>

A Digibee Integration Platform oferece suporte às seguintes versões:

* Hyperion Essbase 7
* Microsoft Analysis Services 2005
* Mondrian (sem informação de versão)
* SAP BW 3.0a+

**Strings de Conexão**

* MS SQL Server

```
jdbc:jdbc4olap:http://<server>:<port>/OLAP/msmdpump.dll
```

* Mondrian

```
jdbc:jdbc4olap:http://<server>:<port>/mondrian/xmla
```

* SAP BW

```
jdbc:jdbc4olap:http://<server>:<port>/sap/bw/soap/xmla?sap-client=number
```

{% hint style="info" %}
Esse tipo de conexão utiliza o padrão XMLA (XML for Analysis), que deve estar habilitado no servidor OLAP a ser acessado.
{% endhint %}

## JTOpen for AS/400 <a href="#jtopen-for-as400" id="jtopen-for-as400"></a>

Sem informação de compatibilidade

**String de Conexão**

```
jdbc:as400://<server>[:port];prompt=false
```

{% hint style="info" %}
A porta de _Database Access_ (padrão 8471) deve ser mapeada conforme a [documentação da IBM](https://www.ibm.com/support/pages/tcpip-ports-required-ibm-i-access-and-related-functions). Também recomendamos que você especifique o parâmetro **prompt=false** para que o _driver_ não tente solicitar credenciais, que são passadas automaticamente.
{% endhint %}

## SAP HANA <a href="#sap-hana" id="sap-hana"></a>

Sem informação de compatibilidade

**String de Conexão**

```
jdbc:sap://<server>:<port>
```

## Firebird <a href="#firebird" id="firebird"></a>

A Digibee Integration Platform oferece suporte às seguintes versões:

* 2.5+

**Strings de Conexão**

```
jdbc:firebirdsql://<HOST>:<PORT>/C:\PATH_TO_DATABASE/DATABASE_FILE.FDB
```

## DB Informix <a href="#h_397032b59c" id="h_397032b59c"></a>

Sem informação de compatibilidade

{% hint style="warning" %}
**Ao acessar as bases de dados especificadas nessa **_**string**_** de conexão, você concorda que possui as licenças IBM necessárias.**
{% endhint %}

**String de Conexão**

```
jdbc:informix-sqli://<HOST>:<PORT>/<DATABASE>:informixserver=<INFORMIX_SERVER>
```

## Netsuite <a href="#h_c94de6d619" id="h_c94de6d619"></a>

Sem informação de compatibilidade

{% hint style="warning" %}
**Ao acessar as bases de dados especificadas nessa **_**string**_** de conexão, você concorda que possui as licenças da Netsuite necessárias.**
{% endhint %}

{% hint style="info" %}
Esse _driver_ de banco de dados suporta somente a operação SELECT.
{% endhint %}

**String de Conexão**

```
jdbc:ns://{Server Host}:{Server Port};ServerDataSource={Server Data Source};encrypted=1;Ciphersuites={Cipher Suite};CustomProperties=(AccountID={Account Id};RoleID={Role Id})
```

## Snowflake <a href="#h_abaa247811" id="h_abaa247811"></a>

{% hint style="warning" %}
**Ao acessar as bases de dados especificadas nessa **_**string**_** de conexão, você concorda que possui as licenças da Snowflake necessárias.**
{% endhint %}

A Digibee Integration Platform oferece suporte às seguintes versões:

* 3.51.x +

**Strings de Conexão**

* **Sintaxe**

```
jdbc:snowflake://<account_name>.snowflakecomputing.com/?<connection_params>
```

* **Exemplo**

```
jdbc:snowflake://wxyz.us-central1.gcp.snowflakecomputing.com/?db=snowflake_sample_data&sfSchema=TPCH_SF100
```

Leia a [documentação da Snowflake ](https://docs.snowflake.com/en/user-guide/jdbc-configure.html)para saber mais sobre a configuração de parâmetros da string de conexão.

{% hint style="info" %}
* A versão 3.10.3 do _driver_ JDBC está sendo utilizada devido a uma limitação nas suas versões mais atuais: não é possível trabalhar com micro serviço alocando memória de 64MB (essa configuração é referente a um _pipeline small_ na Digibee Integration Platform). Acesse a [documentação sobre change log da Snowflake](https://docs.snowflake.com/en/release-notes/client-change-log-jdbc) para mais informações.
* O Snowflake não suporta os campos CLOB ou BLOB. Com isso, a opção “Blob as File” não funcionará nos componentes [DB V2](../components/structured-data/db-v2/) e [Stream DB V3](../components/structured-data/stream-db-v3.md). Leia as documentações da Snowflake sobre [tipos de dados não suportados](https://docs.snowflake.com/en/sql-reference/data-types-unsupported.html) e [entrada e saída binárias](https://docs.snowflake.com/en/user-guide/binary-input-output.html) para obter mais informações.
* Quando o _batch mode_ é utilizado e ocorre um erro, o _driver_ do Snowflake não retorna a quantidade de transações com sucesso nem a quantidade de erros. Só é retornado o erro da primeira exceção SQL e o _rollback_ de toda a transação é feito mesmo quando a opção “rollbackOnError” não é selecionada.
* O Snowflake não suporta os parâmetros OUT e INOUT, retornando o erro _SQLFeatureNotSupportedException_.
* Quando o _batch mode_ é utilizado, os campos do tipo BINARY e VARBINARY não são suportados.
{% endhint %}
