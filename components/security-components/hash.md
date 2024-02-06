---
description: >-
  Discover more about the Hash component and how to use it on the Digibee
  Integration Platform.
---

# Hash

**Hash** generates a hash from a string.&#x20;

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="137">Parameter</th><th width="408">Description</th><th width="142.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Types of available operation (Hash Fields, Hash Payload, and Hash File).</td><td>Hash Fields</td><td>String</td></tr><tr><td><strong>File name</strong></td><td>Name of the file or full file path (i.e. tmp/processed/file.txt). This field is available only when Hash File is selected in the <strong>Crypto Operation</strong> parameter and supports MD5 Crypto Algorithm only.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Crypto Algorithm</strong></td><td>Type of algorithm used to generate the hash. Possible values for this parameter are MD5, SHA-1, SHA-256, SHA-384, SHA-512, HmacSHA1, HmacSHA256, HmacSHA384, HmacSHA512, and BCrypt.</td><td>SHA-512</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>It will be shown only if the selected algorithm in the <strong>Crypto Algorithm</strong> field is HmacSHA1, HmacSHA256, HmacSHA384, or HmacSHA512. The account must be from the SECRET_KEY type, and the key for the hash must be informed.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Secret Key</strong> <code>(DB)</code></td><td>It will be shown only if no account is selected and the algorithm selected in the Crypto Algorithm field is HmacSHA1, HmacSHA256, HmacSHA384, or HmacSHA512. This is an alternative for the component to receive the key for the hash generation in a dynamic way.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Secret Key Type</strong></td><td>It will be shown only if the algorithm selected in the <strong>Crypto Algorithm</strong> field is HmacSHA1, HmacSHA256, HmacSHA384, or HmacSHA512. This field also informs the component which is the type of the informed key, which can be of the String, Hexadecimal, or base64 type.</td><td>Hexadecimal</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset of the provided key type. This field is only available when the <strong>Secret Key Type</strong> parameter value is String.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>BCrypt Version</strong></td><td>Version of the BCrypt algorithm to be considered when generating the hash. This option is only available when the <strong>Crypto Algorithm</strong> parameter value is BCrypt.</td><td>2y</td><td>N/A</td></tr><tr><td><strong>Salt</strong></td><td>A 16-byte string added to the hash value. If not informed, a random value will be assumed. This option is only available when the <strong>Crypto Algorithm</strong> parameter value is BCrypt.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Cost Factor</strong></td><td>Determines the number of rounds for the hash to be executed. The cost factor will be raised to a power of 2, and the possible values are between 4 and 20. E.g.: if the parameter value is 10, then the number of rounds for the hash will be 2^10 = 1024 rounds. This option is only available when the <strong>Crypto Algorithm</strong> parameter value is BCrypt. See more in the <a href="hash.md#cost-factor">section</a> below.</td><td>0</td><td>Integer</td></tr><tr><td><strong>JSON Field Path</strong></td><td>JSON as the path of the string field in dotted notation.</td><td>xml.text</td><td>String</td></tr><tr><td><strong>Payload</strong></td><td>Field to directly inform the payload that will have the hash done. It will be shown only if the selected operation is Hash Payload.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Preserve Original</strong></td><td>If activated, the option preserves the original field as "Field" property in the same level as the original one.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Result As Hexadecimal</strong></td><td>If activated, the option keeps the hash in hexadecimal format; otherwise, the format will be base64.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
**Important:** the component gerenates a hash from a string provided in the **Payload** field if the selected operation is Hash Payload. However, if the selected operation is Hash Fields, then the component generates a hash from a string provided in the fields specified in the input JSON.
{% endhint %}

## Cost Factor

In the BCrypt algorithm, the cost factor exponentially affects processing time and resources, as the algorithm will be executed consecutively according to the number of rounds obtained from the 2ˆn calculation result, in which “n” is the cost factor.

These are some execution examples to serve as a hash calculation duration parameter. As a premise to apply the BCrypt algorithm hash, a 1MB payload and a cost factor with a minimum and maximum allowed are being used. The obtained results are:

**Cost Factor 4**

* **Pipeline Small:** average of 0.98s
* **Pipeline Medium:** average of 0.64s
* **Pipeline Large:** average of 0.07s

**Cost Factor 20**

* **Pipeline Small:** average of 8m 7s
* **Pipeline Medium:** average of 3m 56s
* **Pipeline Large:** average of 1m 53s

The results above may vary according to the integration flow built, the message size to be applied to the hash and the cost factor.

Another important point to be highlighted is the limit of the cost factor. The cost factor of the BCrypt algorithm allows a range between 4 and 31, but factors above 20 end up consuming very high processing load and time, what makes the execution timeout parameters of a pipeline unfeasible.&#x20;

Therefore, the **Hash** component was limited to accept a maximum value of 20 as a cost factor. Based on this premise, when a value is hashed through the **Hash** component and the BCrypt algorithm is used, mind the limit of 20 as a cost factor so that you don't have problems with validation or checking in your integration flow.

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

## Input <a href="#input" id="input"></a>

If you select the _Hash Fields_ operation, the component receives any input message, but you must configure the path for the message hash in the **JSON Field Path** property. For example:

**JSON Field Path:** data.test

```
{    
    "data":[
        {"test":"xpto"},        
        {"test":"xpto1"},        
        {"test":"xpto2"},        
        {"test":"xpto3"}    
    ]
}
```

Therefore, the component makes a search in the “test” property, inside the “data” property.

On the other hand, if you select the Hash Payload operation, then the input message must be informed inside the **Payload** field.

## Output <a href="#output" id="output"></a>

### **Operation Hash Fields**

If you select the Hash Fields operation, the output has the same input structure, but shows the message hash. If the **Preserve Original** property is enabled, then the output preserves the original field in the same level, adding the `'_'` prefix before the field:

```
{
  "data": [
    {
      "test": "3851b1ae73ca0ca6e3c24a0256a80ace",
     "_test": "xpto"
    },
    {
      "test": "ca9e9bf198149d78f4aad334c838a263",
   "_test": "xpto1"
    },
    {
      "test": "83709b4f9067a83bbdfb0c358dc23a5e",
      "_test": "xpto2"
    },
    {
      "test": "e427f7e6f1bd29d91ea0cc53e40fba12",
      "_test": "xpto3"
    }
  ]
}

```

### **Operation Hash Payload**

If you select the Hash Payload operation, the output shows the "result" property with the hash of the provided message:

```
{  
    "result": "3851b1ae73ca0ca6e3c24a0256a80ace"
}
```

#### **Error**

```
{
  "success": false,
  "message": "Something went wrong while trying to use the HashConnector. Error: java.lang.StringIndexOutOfBoundsException: String index out of range: 1",
  "error": "java.lang.StringIndexOutOfBoundsException: String index out of range: 1"
}
```

* **success:** “false”, because there was an error in the execution.
* **message:** error message of the component.
* **error:** error message received from the hash algorithm.

## Hash in Action <a href="#hash-in-action" id="hash-in-action"></a>

### Operation Hash Fields <a href="#operation-hash-fields" id="operation-hash-fields"></a>

#### **Example 1**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** SHA-256
* **JSON Field Path:** data.test
* **Preserve Original:** active
* **Result As Hexadecimal:** active

#### **Input**

```
{
    "data": [
        {"test":"xpto"},
        {"test":"xpto1"},
        {"test":"xpto2"},
        {"test":"xpto3"}
    ]
}
```

#### **Output**

```
{
  "data": [
    {
      "test": "2e954593b0b51547656f7f06ec3818a2b42fed46307b81bd493133aa1ce45173",
      "_test": "xpto"
    },
    {
      "test": "8b948d95169f851545f8161fb4dc8e1d37a4c79014ac1d02186fa8946a91aab9",
      "_test": "xpto1"
    },
    {
      "test": "4c9e0d7ca22d9ab7cc675de59226f9477fd847ede13894b835d0ae204139f63a",
      "_test": "xpto2"
    },
    {
      "test": "b5bd5abe3eb5958153af6615df06ccbdfe5857a13da2601f49e4de9fbb102f9a",
      "_test": "xpto3"
    }
 ]
}
```

#### **Example 2**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** HmacSHA256
* **Account:** empty
* **Secret Key:** 001def0209
* **Secret Key Type:** Hexadecimal (the key provided in the **Secret Key** property must be in hexadecimal)
* **JSON Field Path:** data.test
* **Preserve Original:** active
* **Result As Hexadecimal:** active

#### **Input**

```
{
    "data": [
        {"test":"xpto"},
        {"test":"xpto1"},
        {"test":"xpto2"},
        {"test":"xpto3"}
    ]
}
```

#### **Output**

```
{
  "data": [
    {
      "test": "257966929b29a6e0618d47a152e2856a888072400a5cb458fa1d40ff3cedc734",
      "_test": "xpto"
    },
    {
      "test": "ce0e754ab2f57f1fca1a00fce3e834a6940bea8013ae59b6641a4911e349b480",
      "_test": "xpto1"
    },
    {
      "test": "ff0cd9c0df219f99567aeb25d7d5ab9acff3c29728b0f4f71f50e750750a26d5",
      "_test": "xpto2"
    },
    {
      "test": "04a11cbc118ea455c0072e6c70607f68324e5444c8a4795443d25933d9dfa9c6",
      "_test": "xpto3"
    }
  ]
}
```

#### **Example 3**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** BCrypt
* **Bcrypt Version:** 2y
* **Salt:** N9qo8uLOickgx2ZM
* **Cost:** 6
* **JSON Field Path:** data.test
* **Preserve Original:** active

#### **Input**

```
{
    "data": [
        {"test":"xpto"},
        {"test":"xpto1"},
        {"test":"xpto2"},
        {"test":"xpto3"}
    ]
}
```

#### **Output**

```
{
    "data": [
        {
            "test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROhJmATBMG6eXfkYkffexdfdFHzzp27Iu",
            "_test": "xpto"
        },
        {
            "test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROm9TaJZ6QQUstIomnJG/Qgc7fPU5x8S.",
            "_test": "xpto1"
        },
        {
            "test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROHAP1dIbNu3SenuQ6B.W9OkJ0/NzYF6e",
            "_test": "xpto2"
        },
        {
            "test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROPsXkmxUVt8Suo8d3GuOl9q0pryw6iJy",
            "_test": "xpto3"
        }
    ]
}

```

### Operation Hash Payload <a href="#operation-hash-payload" id="operation-hash-payload"></a>

#### **Example 1**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** SHA-256
* **Payload:** xpto
* **Result As Hexadecimal:** active

#### **Output**

```
{  
    "result": "2e954593b0b51547656f7f06ec3818a2b42fed46307b81bd493133aa1ce45173"
}
```

#### **Example 2**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** HmacSHA512
* **Account:** empty
* **Secret Key:** 001def0209
* **Secret Key Type:** Hexadecimal (the key provided in the **Secret Key** property must be in hexadecimal)
* **Payload:** xpto
* **Result As Hexadecimal:** active

#### **Output**

```
{  
    "result": "517da9449385a43478309459adf9304bd3c8f63cd1d388abd5cbc02b81d8ccb39d303f877019aebfed073166e6c410197e10077f6df3f7a3b3f50adb8cd09580"
}
```

#### **Example 3**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** BCrypt
* **Bcrypt Version:** 2b
* **Salt:** N9qo8uLOickgx2ZM
* **Cost:** 10
* **Payload:** \{{ message.data \}}

#### **Input**

```
{
    "data": [
        {"test":"xpto"},
        {"test":"xpto1"},
        {"test":"xpto2"},
        {"test":"xpto3"}
    ]
}
```

#### **Output**

```
{  
    "result": "$2b$10$RhjvZxfzRC7nW0rlcBHYROa3UXROXVeKZ3oK4DSc1mV6iJ/pBqBm6"
}
```
