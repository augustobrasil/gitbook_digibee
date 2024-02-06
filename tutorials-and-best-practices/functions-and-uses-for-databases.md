---
description: >-
  Learn about general functions and uses of the Digibee Integration Platform
  when creating integration pipelines.
---

# Functions and uses for databases

## Connection string with some databases <a href="#connection-string-with-some-databases" id="connection-string-with-some-databases"></a>

**Mysql**

```sql
jdbc:mysql://{host-ip}:{porta}/{nome-database}
```

**Progress DB**

```
jdbc:datadirect:openedge://{host-ip}:{porta};databaseName={nome-database};
```

**MSsql - SQL Server**

```
jdbc:sqlserver://{host-ip}:{porta};databaseName={nome-database}
```

**Oracle**

```
jdbc:oracle:thin:@(DESCRIPTION = (ADDRESS_LIST = (ADDRESS = (PROTOCOL = TCP)(HOST = {host-ip})(PORT = {porta})))(CONNECT_DATA =(SERVICE_NAME = {nome-database})))
```

**PostGreSQL**

```
jdbc:postgresql://{host-ip}:{porta}/{nome-database}
```

**Sybase**

This string is different from the others, because the connection properties go together with the string after the question mark:

```
jdbc:sybase:Tds:{host-ip}:{porta}/{nome-database}?DYNAMIC_PREPARE={dynamic-prepare}&APPLICATIONNAME={applcation-name}
```

## **SQL Server - Tables Description**

This is an example of how to list the columns of the table in SQL Server by using **select**:

```sql
desc SQL SERVER

SELECT column_name AS [name],
       IS_NULLABLE AS [null?],
       DATA_TYPE + COALESCE('(' + CASE WHEN CHARACTER_MAXIMUM_LENGTH = -1
                                  THEN 'Max'
                                  ELSE CAST(CHARACTER_MAXIMUM_LENGTH AS VARCHAR(5))
                                  END + ')', '') AS [type]
FROM   INFORMATION_SCHEMA.Columns
WHERE  table_name = 'TB_CLIENTES'
```

\
**SQL Server - Function equivalent to IN**

```
[{"data":{"name":"json-generator-connector",
    "type":"connector",
    "stepName":"Json-Generator-Connector",
    "params":{"json":"{\n \"ids\":[\n \"111\",\n \"222\",\n \"333\"\n ]\n}",
    "failOnError":false},
    "key":"component@connectorjson-generator-connector",
    "id":"ff69b6d7-919b-442d-810e-cca34ec3f46d",
    "onProcessTrack":null,"onExceptionTrack":null},
    "position":{"x":-16,"y":-107.25},
    "group":"nodes",
    "removed":false,
    "selected":true,
    "selectable":true,
    "locked":false,
    "grabbable":true,
    "pannable":false,
    "classes":"pasted eh-preview-active"
},
{
    "data":{"type":"transformer",
        "stepName":"Transform",
        "transformSpec":"[\n {\n \"operation\": \"modify-default-beta\",
            \n \"spec\": {\n \"ids_join\": \"=join(',',@(1,ids))\"\n }\n }\n]",
        "onProcessTrack":null,
        "onExceptionTrack":null,
        "id":"095bebef-ad82-48aa-8de7-159d4e6c62b7",
        "key":"component@transformertransformer"},
        "position":{"x":160,"y":-107.25},
        "group":"nodes","removed":false,
        "selected":true,
        "selectable":true,
        "locked":false,
        "grabbable":true,
        "pannable":false,
        "classes":"pasted eh-preview-active"
},
{
    "data":{"name":"json-generator-connector",
        "type":"connector",
        "stepName":"Json-Generator-Connector",
        "params":{"json":"{\n \"ids_list\": {{ CONCAT(\"'\", 
            REPLACE(message.ids_join, \",\", \"','\"), 
            \"'\") }}\n}","failOnError":false},
            "onProcessTrack":null,
            "onExceptionTrack":null,
            "id":"983100d7-d430-4997-b49d-55fcd61569bf",
            "key":"component@connectorjson-generator-connector"},
            "position":{"x":336,"y":-107.25},
            "group":"nodes",
            "removed":false,
            "selected":true,
            "selectable":true,
            "locked":false,
            "grabbable":true,
            "pannable":false,
            "classes":"pasted eh-preview-active"
},
{
    "data":{"params":{"operation":"QUERY",
        "url":"{{global.connection-string-sql-server}}",
        "sql":"DECLARE @SQL VARCHAR(500),
        \r\n\t\t@STATUS VARCHAR(500) = '''Enviado OMNIZE'''\r\n Set @SQL= 'UPDATE tbl_distribuidor_omnize_online_f SET STATUS = '+@STATUS+' WHERE card_id in (' + {{ message.ids_list }} + ')'\r\nEXEC (@SQL)",
        "failOnError":false,
        "blobAsFile":false,
        "connectionProperties":"{}",
        "typeProperties":"[]"},
        "accountLabel":"",
        "name":"db-connector-v2",
        "stepName":"DB-Connector",
        "type":"connector",
        "id":"a8f4651b-daa2-4013-9dcd-677e285af6a7",
        "onExceptionTrack":null,
        "onProcessTrack":null,
        "key":"component@connectordb-connector-v2"},
        "position":{"x":523.5,"y":-107.25},
        "group":"nodes",
        "removed":false,
        "selected":true,
        "selectable":true,
        "locked":false,
        "grabbable":true,
        "pannable":false,
        "classes":"pasted eh-preview-active"
},
{
    "data":{"source":"ff69b6d7-919b-442d-810e-cca34ec3f46d",
        "target":"095bebef-ad82-48aa-8de7-159d4e6c62b7",
        "id":"10a773ce-4acc-4b56-bcac-cbbe47151cfb"},
        "position":{"x":25,"y":25},
        "group":"edges",
        "removed":false,
        "selected":true,
        "selectable":true,
        "locked":false,
        "grabbable":true,
        "pannable":true,
        "classes":""
},
{
    "data":{"source":"095bebef-ad82-48aa-8de7-159d4e6c62b7",
        "target":"983100d7-d430-4997-b49d-55fcd61569bf",
        "id":"adcf7a25-8c0a-4c92-9b4a-39220c1c22c7"},
        "position":{"x":0,"y":0},
        "group":"edges",
        "removed":false,
        "selected":true,
        "selectable":true,
        "locked":false,
        "grabbable":true,
        "pannable":true,
        "classes":""
},
{
    "data":{"source":"983100d7-d430-4997-b49d-55fcd61569bf",
        "target":"a8f4651b-daa2-4013-9dcd-677e285af6a7",
        "id":"91edbd55-da58-484d-b1b9-9673df58074c"},
        "position":{"x":0,"y":0},
        "group":"edges",
        "removed":false,
        "selected":true,
        "selectable":true,
        "locked":false,
        "grabbable":true,
        "pannable":true,"classes":""
}
]
```

**My SQL - Tables Description**

```sql
DESCRIBE tb_nome_tabela;
SHOW COLUMNS FROM tb_nome_tabela LIKE ‘I%’;
```

**Oracle - Function equivalent to IN**

```sql
{"ufs":",SP,PR,"} 
SELECT c.IDCIDADES as  id_cidade, c.UF, c.nome, ','||c.UF||',' 
as UF FROM CIDADES c  where  instr({{ message.ufs }}, ','||c.UF||',')  > 0
```

**Oracle - Timestamp (number) to date convertion**

```sql
SELECT TO_CHAR( TO_DATE('19700101','yyyymmdd') 
    + (1551129634776/1000/24/60/60), 
        'YYYYMMDD HH24:MI:SS')thedate 
FROM dual
```

\
**Oracle - Select column names of a table**

```sql
SELECT table_name, column_name, data_type, data_length
FROM USER_TAB_COLUMNS
WHERE table_name = 'MYTABLE'
```

\
**SQL Server - Tips to use pagination**

```sql
DECLARE @PageNumber AS INT, @RowspPage AS INT
SET @PageNumber = 2
SET @RowspPage = 5

SELECT * FROM (
             SELECT ROW_NUMBER() OVER(ORDER BY ID_EXAMPLE) AS NUMBER,
                    ID_EXAMPLE, NM_EXAMPLE, DT_CREATE FROM TB_EXAMPLE
               ) AS TBL
WHERE NUMBER BETWEEN ((@PageNumber - 1) * @RowspPage + 1) AND (@PageNumber * @RowspPage)
ORDER BY ID_EXAMPLE
```

## **Timeout Oracle Configuration**

The following information must be entered in the **Custom connection properties** field in [DB v2 ](https://docs.digibee.com/documentation/components/structured-data/db-v2)component to have better control over the connection timeout with the database:



**Postgres**

```
{
  "loginTimeout": "50",
  "connectTimeout": "50",
  "socketTimeout": "50",
  "cancelSignalTimeout": "50"
}
```



**SQLServer**

```
{
    "cancelQueryTimeout": 5,
    "queryTimeout": 15,
    "lockTimeout": 15000,
    "socketTimeout": 15000
}
```



**Oracle**

```
{
    "oracle.jdbc.ReadTimeout": 15000,
    "oracle.net.CONNECT_TIMEOUT": 15000
}
```



**MySQL (via URL)**

```
jdbc:mysql://{{mysql-dbo-ip}}/dbo?serverTimezone=UTC&connectTimeout=400000
```
