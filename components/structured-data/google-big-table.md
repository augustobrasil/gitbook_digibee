---
description: Know the component and how to use it.
---

# Google Big Table

**Google Big Table** establishes a connection with the Google BigTable service in the pipeline. This feature allows the execution of different operations using Google BigTable database instances.&#x20;

Take a look at the configuration parameters of the component:

* **Account:** it is necessary to have a PRIVATE KEY account type in order to make the service authentication.
* **Project ID:** ID of the project on Google BigTable.
* **Instance ID:** ID of the instance on Google BigTable.
* **Table ID:** ID of the table on Google BigTable.
* **Operation:** sets the operation to be executed, which can be: write, read by rowkey, read by specific cell, read by prefix, read by range, or delete row by rowkey.
* **Payload as file:** if the option is enabled, the register will be made through a file located in the “File Name” field. Otherwise, the “Payload” field must be filled.
* **Payload:** object which will be registered in the database.
* **File Name:** file with the object which will be registered.
* **Rowkey:** identifies a rowkey of a single row on Google BigTable.
* **Family:** identifies a family on Google BigTable.
* **Qualifier:** identifies a qualifier on Google BigTable.
* **Prefix:** sets the prefix to query a rowkey of a single row on Google BigTable.
* **Start range:** sets the initial range to query a rowkey of a single row on Google BigTable.
* **End range:** sets the limit range to query a rowkey of a single row on Google BigTable.
* **Fail On Error:** if the option is enabled, the execution of the pipeline with error will be interrupted. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.

Some of the parameters above support Double Braces. Read the article [How to reference data using Double Braces](../../build/double-braces/how-to-reference-data-using-double-braces.md) to understand how this language works.

## Messages flow&#x20;

### Input

No specific input message is expected, but the filling of parameters (which vary according to the selected operation) is mandatory. See below the mandatory parameters for each operation:

* Write: Payload
* Read by rowKey: Rowkey
* Read by specific cell: Rowkey, Family, Qualifier
* Read by prefix: Prefix
* Read by range: Start Range, End range
* Delete row by rowkey: Rowkey

For the Write operation, the “File Name” field must contain the proper file name or file path if the option “Payload as File” is enabled.

### Output

If the operations Write or Delete row by Rowkey are executed, the following JSON structure will be generated:

```
{
  "success": true
}
```

* **success:** "true" if the last operation has been successful
* **error:** is displayed if there’s been an error and Fail on Error is "false"

If the operations Read by rowKey, Read by specific cell, Read by Prefix or Read by range are executed, the following JSON structure is generated:

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}

* **data:** data returned with the operation.
* **rowKey:** rowkey ID used in the operation.
* **cellList:** group of cells containing family, qualifier and value data.
* **family:** family of the database instance.&#x20;
* **qualifier:** qualifier of the database instance.
* **value:** value of the database instance.
* **success:** "true" if the last operation has been successful.

## Google Big Table in Action

Take a look at the input parameters and the expected output for each operation in the following examples:

### Write

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Write

**Payload:**\


```
[
   {
      "rowKey":"BBDC4#20200102",
      "cellList":[
         {
            "family":"familiaA",
            "qualifier":"data",
            "value":"20200103"
         },
         {
            "family":"familiaA",
            "qualifier":"data",
            "value":"20200103"
         }
      ]
   }
]
```

#### **Output**

```
{
  "success": true
}
```

### Read by RowKey

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read

**RowKey:** BBDC4#20200103

#### **Output**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}

### Read by specific cell

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by specific cell

**Rowkey:** BBDC4#20200103

**Family:** familiaA

**Qualifier:** data

#### **Output**

{% code overflow="wrap" %}
```
{
  "data": "{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"}]}",
  "success": true
}
```
{% endcode %}

### Read by prefix

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by prefix

**Prefix:** BBDC4#202001

#### **Output**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200102\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200102\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,20909119\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"32,90908813\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,07200241\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"20687260\"}]}]",
  "success": true
}
```
{% endcode %}

### Read by range

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Read by range

**Start range:** BBDC4#20200100

**End range:** BBDC4#20200106

#### **Output**

{% code overflow="wrap" %}
```
{
  "data": "[{\"rowKey\":\"BBDC4#20200102\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"}]},{\"rowKey\":\"BBDC4#20200103\",\"cellList\":[{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"ativo\",\"value\":\"BBDC4\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaA\",\"qualifier\":\"data\",\"value\":\"20200103\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"abertura\",\"value\":\"33,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"alta\",\"value\":\"34,54545212\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"baixa\",\"value\":\"33,52727127\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaB\",\"qualifier\":\"fechamento\",\"value\":\"34,09999847\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"fechamentoAjustado\",\"value\":\"33,08722305\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"},{\"family\":\"familiaC\",\"qualifier\":\"volume\",\"value\":\"33057090\"}]}]",
  "success": true
}
```
{% endcode %}

### Delete row by rowKey

#### **Input**

**Parameters**

**Account:** google-storage-test

**Project ID:** digibee-test

**Instance ID:** spike-bigtable-id

**Table ID:** historicoAtivos

**Operation:** Delete row by rowKey

**Rowkey:** BBDC4#20200102

#### **Output**

```
{
  "success": true
}
```
