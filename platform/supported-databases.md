---
description: >-
  Discover the types and versions of databases supported by the Digibee
  Integration Platform and how they can make integration pipeline creation
  easier for all users.
---

# Supported databases

You can access databases using specific components, such as:

* [DB V2](../components/structured-data/db-v2/)
* [Stream DB V3](../components/structured-data/stream-db-v3.md)
* [Stored Procedure](../components/structured-data/stored-procedure.md)

The database support mentioned here doesn't apply to deprecated versions of components. We recommend that you don't use deprecated components. Some examples of deprecated components are:

* [Stream DB V1](../components/structured-data/stream-db-v1.md)
* [DB V1](../components/structured-data/db-v1.md)

The Digibee Integration Platform currently supports the following databases:

## DB2

The Digibee Integration Platform offers support for the JDBC IBM DB2 driver and covers the following versions:

* DB2 level version: 11.5
* Driver version: 4.26.14

**Connection String**

```
jdbc:db2://127.0.0.1:1724/dbtest
```

{% hint style="info" %}
The available features are based on [the official documentation of DB2](https://www.ibm.com/support/pages/db2-jdbc-driver-versions-and-downloads). Your company's driver licensed by IBM must be activated to connect across supported database versions.&#x20;

This process is handled by the Digibee support team, but you must provide the JDBC IBM DB2 driver for activation. This process is exclusive to the requesting customer's realm.
{% endhint %}

## Apache Hive

The Digibee Integration Platform offers support for Apache Hive via JDBC Connector 2.6.17 for Cloudera Enterprise only and covers the following versions:

* Apache Hive versions 1.0.0 to 3.1

**Connection string**

```
 jdbc:hive2://localhost:10002
```

{% hint style="info" %}
The available features are based on [the official documentation of JDBC Cloudera driver](https://docs.cloudera.com/documentation/other/connectors/hive-jdbc/2-6-17.html). Your company's driver licensed by Cloudera must be activated to connect across supported database versions.&#x20;

This process is handled by the Digibee support team, but you must provide the Cloudera JDBC driver for activation. This process is exclusive to the requesting customer's realm.
{% endhint %}

## Teradata Database

&#x20;The Digibee Integration Platform offers support for the following versions:

* Teradata Database 16.10, 16.20, 17.00, 17.10 and 17.20.

**Connection String**

```
jdbc:teradata://192.168.64.2/DATABASE=DBC,DBS_PORT=1025
```

{% hint style="info" %}
Your company's driver licensed by Teradata must be activated to connect across supported database versions. \
\
This process is handled by the Digibee support team, but you must provide the Teradata JDBC driver for activation. This process is exclusive to the requesting customer's realm.
{% endhint %}

## SQL Server <a href="#sql-server" id="sql-server"></a>

The Digibee Integration Platform offers support for the following versions:

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
Connection via Microsoft SQL 2019 version is supported, but some features of this version may not be available.
{% endhint %}

**Connection String**

```
jdbc:sqlserver://[serverName[\instanceName][:portNumber]]
```

## Oracle <a href="#oracle" id="oracle"></a>

The Digibee Integration Platform offers support for the following versions:

* 19.x
* 18.3
* 12.2 or 12cR2
* 12.1 or 12cR1
* 11.2 or 11gR2

**Connection Strings**

* Oracle Net Syntax

```
jdbc:oracle:thin:@(DESCRIPTION=
(LOAD_BALANCE=on)
(ADDRESS_LIST=
(ADDRESS=(PROTOCOL=TCP)(HOST=host1) (PORT=5221))
(ADDRESS=(PROTOCOL=TCP)(HOST=host2)(PORT=5221)))
(CONNECT_DATA=(SERVICE_NAME=orcl)))
```

{% hint style="info" %}
In the Oracle database, the connection string can contain multiple endpoints. If your connection string contains more than one endpoint, the Oracle driver will attempt to connect to each endpoint until it's successful or there is no other endpoint.

So if your connection string contains multiple endpoints and you set the `"oracle.net.connect_timeout"` parameter in the **Custom Connection Properties** for components such as [DB V2](https://docs.digibee.com/documentation/components/structured-data/db-v2), [Stream DB V3](https://docs.digibee.com/documentation/components/structured-data/stream-db-v3), and [Stored Procedure](https://docs.digibee.com/documentation/components/structured-data/stored-procedure), it's important to know that the timeout applies to each specified endpoint individually. It doesn't apply to all endpoints at the same time.
{% endhint %}

* Syntax with Service Name

```
jdbc:oracle:thin:@//localhost:5221/orcl
```

{% hint style="info" %}
Only thin-type connections are supported. By accessing the databases specified in this connection string, you confirm that you have the required Oracle licenses.
{% endhint %}

## MySQL <a href="#mysql" id="mysql"></a>

The Digibee Integration Platform offers support for the following versions:

* 5.6
* 5.7
* 8.0

**Connection String**

```
jdbc:mysql://<host>:<port>/<database>
```

{% hint style="info" %}
Digibee Integration Platform deactivates MySQL driver’s interpretation of Maria DB strings. However, you can use Maria DB’s drive to connect to older versions of MySQL.
{% endhint %}

## Maria DB <a href="#maria-db" id="maria-db"></a>

The Digibee Integration Platform offers support for the following version:

* 5.5.3+

**Connection String**

```
jdbc:mariadb://<host>:<port>/<database>
```

{% hint style="info" %}
Digibee Integration Platform deactivates MySQL driver’s interpretation of Maria DB strings.
{% endhint %}

## Progress <a href="#progress" id="progress"></a>

The Digibee Integration Platform offers support for the following version:

* OpenEdge 10.1.x+

**Connection String**

```
jdbc:datadirect:openedge://hostname:port
```

## Sybase <a href="#sybase" id="sybase"></a>

The Digibee Integration Platform offers support for the following version:

* SAP/Sybase ASE

**Connection String**

```
jdbc:sybase:Tds:host:port
```

## PostgreSQL <a href="#postgresql" id="postgresql"></a>

The Digibee Integration Platform offers support for all versions.

**Connection String**

```
jdbc:postgresql://host:port/database
```

## OLAP DataSource via MDX <a href="#olap-datasource-via-mdx" id="olap-datasource-via-mdx"></a>

The Digibee Integration Platform offers support for the following versions:

* Hyperion Essbase 7
* Microsoft Analysis Services 2005
* Mondrian (no version information)
* SAP BW 3.0a+

**Connection Strings**

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
This type of connection uses the XML for Analysis (XMLA) standard, which must be enabled in the OLAP server to be accessed.
{% endhint %}

## JTOpen for AS/400 <a href="#jtopen-for-as400" id="jtopen-for-as400"></a>

No compatibility information

**Connection String**

```
jdbc:as400://<server>[:port];prompt=false
```

{% hint style="info" %}
The Database Access port (standard 8471) must be mapped according to the [IBM documentation](https://www.ibm.com/support/pages/tcpip-ports-required-ibm-i-access-and-related-functions). We also recommend specify the parameter **prompt=false** to prevent the driver from requesting credentials. These credentials are provided automatically.
{% endhint %}

## SAP HANA <a href="#sap-hana" id="sap-hana"></a>

No compatibility information

**Connection String**

```
jdbc:sap://<server>:<port>
```

## Firebird <a href="#firebird" id="firebird"></a>

The Digibee Integration Platform offers support for the following versions:

* 2.5+

**Connection String**

```
jdbc:firebirdsql://<HOST>:<PORT>/C:\PATH_TO_DATABASE/DATABASE_FILE.FDB
```

## DB Informix <a href="#h_6d7a9d14c9" id="h_6d7a9d14c9"></a>

No compatibility information

{% hint style="warning" %}
**By accessing the databases specified in this connection string, you confirm that you have the required IBM licenses.**
{% endhint %}

**Connection String**

```
jdbc:informix-sqli://<HOST>:<PORT>/<DATABASE>:informixserver=<INFORMIX_SERVER>
```

## Netsuite <a href="#h_0066b105ad" id="h_0066b105ad"></a>

No compatibility information

{% hint style="warning" %}
**By accessing the databases specified in this connection string, you confirm that you have the required Netsuite licenses.**
{% endhint %}

{% hint style="info" %}
This database driver supports only the SELECT operation.
{% endhint %}

**Connection String**

```
jdbc:ns://{Server Host}:{Server Port};ServerDataSource={Server Data Source};encrypted=1;Ciphersuites={Cipher Suite};CustomProperties=(AccountID={Account Id};RoleID={Role Id})
```

## Snowflake <a href="#h_57ed671444" id="h_57ed671444"></a>

{% hint style="warning" %}
**By accessing the databases specified in this connection string, you confirm that you have the required Snowflake licenses.**
{% endhint %}

The Digibee Integration Platform offers support for the following versions:

* 3.51.x +

**Connection Strings**

* **Syntax**

```
jdbc:snowflake://<account_name>.snowflakecomputing.com/?<connection_params>
```

* **Example**

```
jdbc:snowflake://wxyz.us-central1.gcp.snowflakecomputing.com/?db=snowflake_sample_data&sfSchema=TPCH_SF100
```

Read [Snowflake's documentation](https://docs.snowflake.com/en/user-guide/jdbc-configure.html) to know more about configuring connection string parameters.

{% hint style="info" %}
* We are currently using the legacy version 3.10.3 of the JDBC driver due to a limitation in more recent versions: it's not possible to work with micro service by allocating a 64MB memory (this configuration refers to a small pipeline in the Digibee Integration Platform). Visit [Snowflake’s change log documentation](https://docs.snowflake.com/en/release-notes/client-change-log-jdbc.html) for further information.
* Snowflake does not support CLOB or BLOB fields. For this reason, the "Blob as file" option doesn't work for the DB and Stream DB components. Read Snowflake's documentation about [unsupported data types](https://docs.snowflake.com/en/sql-reference/data-types-unsupported.html) and [binary input and output](https://docs.snowflake.com/en/user-guide/binary-input-output.html) for more information.
* When batch mode is used and an error occurs, the Snowflake driver doesn't return the number of successful transactions or the number of errors. Only the first SQL execution error is returned and the entire transaction is rolled back, even if the "rollbackOnError" option is deactivated.
* Snowflake doesn't support OUT and INOUT parameters. If you try to use these parameters, Snowflake returns a SQLFeatureNotSupportedException error.&#x20;
* When the batch mode is used, the BINARY and VARBINARY fields aren't supported.
{% endhint %}
