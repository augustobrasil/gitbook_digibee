---
description: >-
  Discover more about the JSON Path Transformer V2 component and how to use it
  on the Digibee Integration Platform.
---

# JSON Path Transformer V2

**JSON Path Transformer V2** has the function of receiving any valid JSON input and making filters and data extractions from an expression. This version of the component also supports Double Braces expressions.

JSONPath is a consulting language for JSON with resources similar to XPath. This expression is normally used to select and extract property values from a JSON object. Learn more in the [documentation about JSONPath](https://goessner.net/articles/JsonPath/).

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON Path</strong> <code>(DB)</code></td><td>Used to show which expression will be used when processing JSON. It's a mandatory parameter and must be configured according to what you want to process. A Double Braces expression can be used to obtain the JSON Path value dynamically from the input.</td><td>$.store.books[?(@.title=='IT')]</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

See a list of options for declaring JSONPath:

* **$:** object root or vector.
* **.property:** selects a specific property in the related object.
* **\['property']**: selects a specific object in the related object. Use single quotes only around the property name. Tip: keep this instruction in mind if the property name has special characters, such as spaces, or if it starts with characters different than A..Za..z\_.
* **\[n]:** selects the n element of a vector. The indexes start with 0.
* **\[index1,index2,…]:** selects elements from the vector with specific indexes and returns a list.
* **..property:** descending recursive. It makes a descending search in property names and returns a vector of all the values with this property name. It always returns a list, even if only 1 property is found.
* _**:** the asterisk selects all the elements in an object or vector, whatever their names or indexes are. For example, “address._” means all the properties of the object address, while “book\[\*]” means all the items of a book vector.
* **\[input:output] / \[input:]:** selects elements from an input vector and even, but not necessarily, an output vector. If the output is omitted, select all the vectors until the end of the vector. A list is returned.
* **\[:n]:** selects the first n elements of the vector. A list is returned.
* **\[-n:]:** selects the last n elements of the vector. A list is returned.
* **\[?(expression)]:** filter expression. It selects all the elements in an object or vector that match with the specified filter. A list is returned.
* **\[(expression)]:** script expressions can replace explicit names from properties or indexes. For example, \[(@.size-1)], that selects the last items of a vector. Here, the size refers to the vector size in question more than a JSON file named "size".
* **@:** used in filter expressions to make reference to the current joint that is being processed.
* **==:** equal to .1 and '1' are considered the same result. String values must be attached in single quotes (and not in double quotes): \[?(@.cor=='vermelho')].
* **!=:** different than. String values must be attached in single quotes.
* **>:** greater than.
* **>=:** greater than or equal to.
* **<:** smaller than.
* **<=:** smaller than or equal to.
* **=\~:** compatible with a regular RedEx Java Script. For example, \[?(@.description =\~ /cat.\*/i)] matches items whose description starts with cat (upper and lowercase aren't considered).
* **!:** used to deny a filter. For example, \[?(!@.isbn)] matches items that don't have the isbn property.
* **&&:** AND logical operator. Example: \[?(@.category=='fiction' && @.price < 10)]
* **||:** OR logical operator. Example: \[?(@.category=='fiction' || @.price < 10)]

## Messages flow

### Input

To show the functionality of this component, you must configure an input JSON in a pipeline with **JSON Path Transformer V2**. After adding it to the pipeline, it's necessary to configure the JSONPath expression as **$.address..\[?(@.postalCode == '02375')].streetAddress** or the example won't work.

The intention of this example is to filter the input addresses by one postal code only and return just the address street. See:

```
{
  "address": [
      {
          "streetAddress": "Bogisich Terrace",
          "city": "New Napoleonville",
          "postalCode": "02375"
},
      {
          "streetAddress": "Schuster Spring",
          "city": "Lake Loraineborough",
          "postalCode": "68244"
      },
      {
          "streetAddress": "Hettinger Ports",
          "city": "Dorcaschester",
          "postalCode": "86760"
      },
      {
          "streetAddress": "Rippin Mount",
          "city": "Lake Bernadettetown",
          "postalCode": "57163"
      },
      {
          "streetAddress": "Gutmann Village",
          "city": "West Darlene",
          "postalCode": "00064"
      }
  ]
}
```

### Output

The structure will be the JSON filtered by the JSONPath specification.

```
[  
   "Bogisich Terrace"
]
```

## JSON Path Transformer V2 in action

Below you can see how the component responds to certain situations and how it is configured in each case.

### Return the book authors only with a recursive descendant parser

In this example, you'll see only the authors of an array with books inside a store. The expression configuration of the component must be **$..author**.

#### Input

```
{
  "store": {
      "book": [
          {
              "category": "reference",
             "author": "Nigel Rees",
              "title": "Sayings of the Century",
              "price": 8.95
      },
          {
              "category": "fiction",
              "author": "Evelyn Waugh",
              "title": "Sword of Honour",
              "price": 12.99
},
 {
  "category": "fiction",
  "author": "Herman Melville",
  "title": "Moby Dick",
  "isbn": "0-553-21311-3",
  "price": 8.99
 },
  {
 "category": "fiction",
 "author": "J. R. R. Tolkien",
 "title": "The Lord of the Rings",
 "isbn": "0-395-19395-8",
 "price": 22.99
         }
  ],
"bicycle": {
"color": "red",
"price": 19.95
 }
}
}
```

#### Output

```
[
  "Nigel Rees",
  "Evelyn Waugh",
  "Herman Melville",
  "J. R. R. Tolkien"
]
[
  "Nigel Rees",
  "Evelyn Waugh",
  "Herman Melville",
  "J. R. R. Tolkien"
]
```

### Return products with a value lower than the one specified only

In this example, you'll see only the products of an array with prices lower than US$3,300. The expression configuration of the component must be **$..\[?(@.price<3300)]**.

#### Input

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
​
```

#### Output

```
[
  {
      "product": "Samsung 4k Q60T 55",
      "price": 3278.99
  }
]
```

### Informing an invalid expression with the "Fail On Error: false" configuration

With this example you can configure the component with **Fail On Error** as “false” and use the expression **$**.

With these configurations, the result will be an error message and with the property `"success": false`.

#### Input

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

#### Output

```
{
  "success": false,
  "error": "The Json Path transformation has failed. Please check your specification: $.",
  "exception": "com.jayway.jsonpath.InvalidPathException: Path must not end with a '.' or '..'"
}
```

### Informing an invalid expression with the "Fail On Error: true" configuration

With this example you can configure the component with **Fail On Error** as “true” and use the expression **$**.

With these configurations, the result will be an error message and the deployment will be immediately interrupted.

#### Input

```
{
  "data": [
      {
          "product": "Samsung 4k Q60T 55",
          "price": 3278.99
      },
      {
          "product": "Samsung galaxy S20 128GB",
          "price": 3698.99
      }
  ]
}
```

#### Output

```
{
  "timestamp": 1603900161240,
  "error": "Json Path Transformer has failed",
  "code": 500
}
```

### Returning only error results from an array input

In this example, only the error results are extracted from an array of executions. The expression configuration of the component must be `$..[?(@.error)]`.

#### Input

```
[
  {
    "executionId": "execution-1",
    "result": {
      "error": "Error 404",
      "code": 404,
      "statusMessage": "Not Found"
    }
  },
  {
    "executionId": "execution-2",
    "result": {
      "error": "Error 500",
      "code": 500,
      "statusMessage": "Internal Server Error"
    }
  },
  {
    "executionId": "execution-3",
    "result": {
      "code": 200,
      "statusMessage": "Success"
    }
  }
]
```

#### Output

```
[
   {
      "error":"Error 404",
      "code":404,
      "statusMessage":"Not Found"
   },
   {
      "error":"Error 500",
      "code":500,
      "statusMessage":"Internal Server Error"
   }
]
```

### Obtain the JSON Path expression dynamically from the input

In this example, the JSON Path is dynamically obtained from the input using a Double Braces expression. The expression configuration of the component must be `{{ message.jsonPath }}`.

#### Input

```
{
  "jsonPath": "$.store.books[?(@.title=='IT')]",
  "store":{
    "books":[
      {
        "author":"Stephen King",
        "title":"IT"
      },
      {
        "author":"Agatha Christie",
        "title":"The ABC Murders"
      }
    ]
  }
}
```

#### Output

```
[
   {
      "author":"Stephen King",
      "title":"IT"
   }
]
```
