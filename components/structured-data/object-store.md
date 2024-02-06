---
description: >-
  Discover more about the Object Store component and how to use it on the
  Digibee Integration Platform.
---

# Object Store

**Object Store** makes operations to store any document in the Object Store of Digibee. It's a simple and quick way to save useful JSON-type information, which has operations to help in multiple uses during the creation of a pipeline.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="355">Description</th><th width="131.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Account to be used by the component. This item can't be changed.</td><td>Digibee Object Store Account</td><td>String</td></tr><tr><td><strong>Operation</strong></td><td>Operation to be executed inside <strong>Object Store</strong> - Find by Object ID, Find By Query, Insert, Aggregate, Update By Object ID, Update By Query, Delete By Object ID, and Delete By Query.</td><td>Find by Object ID</td><td>String</td></tr><tr><td><strong>Object Store Name</strong></td><td>Name of the collection to be used to record or read information. If it doesn't exist, it will be automatically created.</td><td>sales</td><td>String</td></tr><tr><td><strong>Object ID</strong> <code>(DB)</code></td><td>Identifier of the object to be stored or searched. It can be a unique number or a UUID. This item supports Double Braces.</td><td>1</td><td>String</td></tr><tr><td><strong>Limit</strong> <code>(DB)</code></td><td>Maximum number of objects to be returned in a search. This item supports Double Braces.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Skip</strong> <code>(DB)</code></td><td>Amount of objects to be skipped before returning to the query. This parameter is usually used along with the <strong>Limit</strong> parameter to create a way of pagination. This item supports Double Braces.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Sort</strong> <code>(DB)</code></td><td>Specification of the query ordination rules.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Query</strong> <code>(DB)</code></td><td>This JSON field for a query is available only if Find by Query, Aggregate, Update by Query, or Delete by Query operations are selected. Double braces expressions are allowed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Document</strong> <code>(DB)</code></td><td>Available only if Insert, Update by Object ID, or Update by Query are selected. Double braces expressions are supported.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Unique Index</strong></td><td>If the option is activated, an Object ID will be created to accept unique values only; otherwise, a non-unique index will be created.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Isolated</strong></td><td>If the option is activated, all the queries will be delimited in the execution scope.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Upsert</strong></td><td>This option is available only if Update By Object ID or Update By Query operations are selected. When enabled, the item informed for the object will be inserted in the collection in case it doesn't exist.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Best practices <a href="#h_202a6806b9" id="h_202a6806b9"></a>

**Object Store** is an auxiliary database (NoSQL) for integrations. Its use provides more agility and practicality in the development of integrations. To exemplify the applicability of this component, we list the following good usage practices:

* The **Object Store** component has the function of an intermediary database, i.e., it is used to mediate information between the flows of an integration. It must therefore only be used to store information that is relevant to the integration in question.
* The **Object Store** is a temporary database. Once it is used to intermediate relevant information to the integration flow, old and dispensable data must be periodically removed from the database.
* Since it is an auxiliary base, the **Object Store** component must not be used as a permanent database and only in certain cases, with the purpose of supporting the user in the development of integrations.
* All data is stored with maximum security within the Digibee Integration Platform. However, we recommend that sensitive data stored in the **Object Store** be encrypted. To do this, use our encryption connectors available in Canvas.

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

For this specific component, the only mandatory input message pattern is the JSON format applied to the object. The input parameter can use the Double Braces syntax to send the received message to the component.

### Output <a href="#output" id="output"></a>

* **Insert**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Find**

```
{
   "data": [
       {
           "name": "Galaxy s20",
           "uuid": "123",
           "_oId": "1"
       }
   ],
   "rowCount": 1
}
```

* **Update**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Delete**

```
{
    "data": [],
    "updateCount": 1
}
```

* **Aggregate**

```
{
    "data": [],
    "rowCount": 0
}
```

## Object Store in Action <a href="#object-store-in-action" id="object-store-in-action"></a>

Some output examples of each operation were shown above. See below more applications that demonstrate the correct configuration for a determined result to be obtained:

### **Insert multiple items at once in a collection**

When sending an object array in the query field, the component inserts each item in a separate way inside the selected collection.

Observe how to configure the component with the **Operation** (Insert), **Unique Index** (False) and **Query** parameters:

```
[
   {
       "id": 1,
       "name": "Galaxy s20",
       "price": 5000
   },
   {
       "id": 2,
       "name": "Samsung 4k 55\"",
       "price": 5000
   },
   {
       "id": 3,
       "name": "Galaxy A10",
       "price": 699
   },
   {
       "id": 4,
       "name": "Galaxy A51",
       "price": 1620
   }
]
```

#### **Output**

```
{
    "data": [],
    "updateCount": 4
}
```

{% hint style="info" %}
**Important:** the insertion of multiple objects at once is allowed in collections created with **Unique Index** (False) only. The **Unique Index** property is defined in the collection creation. After the index is created, it's not possible to change the property.
{% endhint %}

### **Find items from a determined query**

As an example, consider an **Object Store** that already has registered product-type items and whose characteristics are name and price.

Observe how to configure the component with the **Operation** (Find By Query) and **Query** parameters:

```
{
    "product.price": { $gt: 2000 }
}
```

#### **Output**

```
{
   "data": [
       {
           "product": {
               "id": 1,
               "name": "Galaxy s20",
               "price": 5000
           },
           "_oId": "1"
       },
       {
           "product": {
               "id": 2,
               "name": "Samsung 4k 55\"",
               "price": 5000
           },
           "_oId": "2"
       }
   ],
   "rowCount": 2
}
```

### **Find all the items from a query**

As an example, consider an **Object Store** that already has registered product-type items and whose characteristics are name and price.

Observe how to configure the component with the **Operation** (Find By Query), **Limit** (10) and **Query** parameters:

```
{}
```

#### **Output**

```
{
   "data": [
       {
           "product": {
               "id": 1,
               "name": "Galaxy s20",
               "price": 5000
           },
           "_oId": "1"
       },
       {
           "product": {
               "id": 2,
               "name": "Samsung 4k 55\"",
               "price": 5000
           },
           "_oId": "2"
       },
       {
           "product": {
               "id": 3,
               "name": "Galaxy A10",
               "price": 699
           },
           "_oId": "3"
       },
       {
           "product": {
               "id": 4,
               "name": "Galaxy A51",
               "price": 1620
           },
           "_oId": "4"
       }
   ],
   "rowCount": 4
}
```

In this specific scenario, the **Limit** parameter was configured so there wouldn't be an unnecessary overload when returning the objects from an **Object Store**. If the option isn't configured that way, an "Out Of Memory" error can occur inside the pipeline. In the indicated way, there's control over how many objects are seen in the response.

### **Update an item from a specific ID**

As an example, consider an **Object Store** that already has registered product-type items and whose characteristics are name and price.

Observe how to configure the component with the **Operation** (Update By Object ID), **Object ID** (3) and **Document** parameters:

```
{
   $set: {
       "product": {
         "id": 3,
         "name": "Galaxy A10",
         "price": 605
       }
   }
}
```

#### **Output**

```
{
    "data": [],
    "updateCount": 1
}
```

In this specific scenario, it's possible to see that the output is only an object identifying an update. To check if the object has been properly updated, repeat the ID search scenario.

{% hint style="info" %}
**Important**: if the _**Object Store**_ component is involved in updates, inside an iteration component ([**For Each**](../logic/for-each/), [**Stream File Reader**](../files/stream-file-reader.md), etc.) and making parallel executions, there can be concurrence in the registers update if the update instructions are exactly the same. Consequently, one instruction will return _"updateCount":1_ and the other _"updateCount": 0_. It happens when 2 registers that are exactly the same get into the _**Object Store**_ operation pool and the update or insertion instructions (with the **Upsert** parameter enabled) are sequentially executed. The first instruction makes an update and the second one finds the already-persisted register and checks there's nothing to be changed, returning there was no need for an action (_"updateCount": 0_).
{% endhint %}

### **Remove an item from a specific ID**

As an example, consider an _**Object Store**_ that already has registered product-type items and whose characteristics are name and price.

Observe chow to configure the component with the **Operation** (Delete By Object Id) and **Object ID** (4) parameters:

#### **Output**

```
{
    "data": [],
    "updateCount": 1
}
```

In this specific scenario, it's possible to see that the output is only an object that identifies the update. To check if the object has been properly updated, repeat the ID search scenario.

### **Aggregation to copy the collection**

As an example, consider an **Object Store** called "product" that already has registered product-type items and whose characteristics are name and price. From that, create a new **Object Store** called "product-backup", copying all the items of the collection mentioned above.

You must receive an object array containing the query aggregation pipelines in the **Document** parameter.

Observe how to configure the component with the **Operation** (Aggregate) and **Query** parameters:

```
[
   {
       $merge: {
           into: "product-backup",
           on: "_id",
           whenMatched: "replace",
           whenNotMatched: "insert"
       }
   }
]
```

In this specific scenario, the query was configured to replace the repeated items with the new ones in the collection.

#### **Output**

```
{
    "data": [],
    "rowCount": 0
}
```

To check if the collection has been properly created with the proposed items, repeat the search scenario with all the items and inform the new collection.

### **Aggregation to filter collection items**

You must receive an object array containing the query aggregation pipelines in the **Document** parameter.

Observe how to configure the component with the **Operation** (Aggregate) and **Query** parameters:

```
[
   {
       $match: {
           "product.price": {
               $gt: 3000
           }
       }
   },
   {
       $group: {
           _id: null,
           count: {
               $sum: 1
           }
       }
   }
]
```

In this specific scenario, the query was configured to search products that has a determined value and to show their sum.

#### **Output**

```
{
    "data": [{
        "count": 2
    }],
    "rowCount": 0
}
```

## Technology <a href="#technology" id="technology"></a>

**Object Store** uses search operators and objects aggregation similar to the MongoDB syntax. [Refer to the MongoDB external documentation to learn more. ](https://www.mongodb.com/docs/manual/reference/operator/)
