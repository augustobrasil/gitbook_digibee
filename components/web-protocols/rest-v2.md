---
description: >-
  Discover more about the REST V2 component and how to use it on the Digibee
  Integration Platform.
---

# REST V2

**REST** **V2** makes calls to HTTP endpoints, turning actions as GET, POST, PUT and DELETE much simpler.

The main difference to the V1 is the use of Double Braces expressions to compose URL, headers, query parameters and body of the message, allowing direct access to the pipeline data.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.&#x20;

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="206">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>Address that will receive the HTTP call.</td><td><a href="https://viacep.com.br/ws/%7B%7B">https://viacep.com.br/ws/{{</a> DEFAULT(message.$.cep, "04547-130") }}/json/</td><td>String</td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Configures all types of headers necessary for the call (for example, Content-Type: application/json or multipart/form-data). <br><br>This parameter supports Double Braces for both key and value fields.</td><td>Content-Type : application/json</td><td>Key-value pairs</td></tr><tr><td><strong>Query Params</strong> <code>(DB)</code></td><td>Configures the query parameters necessary for the call.</td><td>N/A</td><td>Key-value pairs</td></tr><tr><td><strong>Verb</strong></td><td>Specifies the HTTP method.</td><td>GET</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: ApiKey, AWS v4, Basic, Certificate Chain, Custom Auth Header, Google Key, Oauth2, and Oauth Bearer Token.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #1</strong></td><td>Additional account to be used by the component through Double Braces <em>{{ account.custom-1.value }}.</em> </td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom Account #2</strong></td><td>Additional account to be used by the component through Double Braces <em>{{ account.custom-2.value }}.</em> </td><td>N/A</td><td>String</td></tr><tr><td><strong>Connect Timeout</strong></td><td>Time for the connection expiration (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Read Timeout</strong></td><td>Maximum time for reading (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>If activated, interrupts the execution of the pipeline on a 4xx HTTP error.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>If activated, interrupts the execution of the pipeline on a 5xx HTTP error.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Advanced configurations.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Raw Mode</strong></td><td>If activated, receives or sends a non-JSON payload.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Raw Mode As Base64</strong></td><td>When activated, shows the response as base64.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Save As Local File</strong></td><td>When activated, saves the response as a file in the local pipeline directory.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Response File Name</strong> <code>(DB)</code></td><td>File name or complete file path (for example, tmp/processed/file.txt).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Allow Insecure Endpoints</strong></td><td>When activated, allows unsafe calls to HTTPS endpoints to be made.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Enable Retries</strong></td><td>When activated, allows new tries in case of server errors.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Number Of Retries</strong></td><td>Maximum number of tries before giving up the call.</td><td>0</td><td>Integer</td></tr><tr><td><strong>Time To Wait Between Retries</strong></td><td>Maximum time between tries (in milliseconds).</td><td>0</td><td>Integer</td></tr><tr><td><strong>Compress Body With GZIP</strong></td><td>When activated, allows the body to be compressed with GZIP.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Force HTTP 1.1</strong></td><td>When activated, forces the request to use HTTP 1.1.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Override Response Charset</strong></td><td>When activated, overwrites the charset returned to the endpoint with the specified charset in "Response Charset" property.<br><br>Otherwise, the return of the charset in the “Content-Type” header will be respected.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Response Charset</strong></td><td>Used only when "Override Response Charset" is activated; forces the use of the specified charset (Standard: UTF-8).<br><br></td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Disable Connection Pooling</strong></td><td>When activated, doesn't keep connections in a pool. <br><br>Recommended for endpoints with connection reuse issues.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Invalidate SSL Sessions on Every Call</strong></td><td>When activated, invalidates SSL sessions on every call.<br><br>Recommended for endpoints with SSL session reuse issues.<br><br>Activating the option will make the component single-threaded - it means that every execution will be sequential for the same REST added to the pipeline canvas.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Use Dynamic Account</strong></td><td>When active, uses the account dynamically; when inactive, uses the account statically.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Account Name</strong></td><td>Account name to be set, generated dynamically via the <a href="https://docs.digibee.com/documentation/components/tools/store-account"><strong>Store Account</strong> </a>component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Scoped</strong></td><td>When activated, the stored account is isolated to other sub-processes. Not supported for accounts used in headers or body.<br><br>To know more about the Scoped flag, check out the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta">Dynamic Accounts documentation</a>.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
Currently, the **Use Dynamic Account**, **Account Name** and **Scoped** parameters can only be used in Pipeline Engine v2 and are only available in the Restricted Beta phase. To learn more about it, [read the article Beta program.](https://docs.digibee.com/documentation/general/beta-program)
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

You can use the following configuration in the body of the message and also use Double Braces:

```
{
    "id": {{ DEFAULT(message.customer.id, UUID()) }},
    "name": {{ message.customer.name }},
    "type": "1"
}
```

{% hint style="warning" %}
It doesn't apply to the verb GET.
{% endhint %}

### Output <a href="#output" id="output"></a>

* **in case of success**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: {},
    headers: {}
}
```

* **in case of success (using the "Raw Mode As Base64" flag)**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: "content in base64 format",
    headers: {}
}
```

* **in case of success (using the “Save As Local File” flag)**

```
{
    status: 2xx,
    statusMessage: "STATUS_MESSAGE",
    body: {
        file: "name of the file defined in the Response File Name property"
    },
    headers: {}
}
```



* **in case of error**

```
{
    error: "error message",
    code: XXX,
    body: {},
    headers: {}
}
```

## REST V2 in Action <a href="#rest-v2-in-action" id="rest-v2-in-action"></a>

### Sending a binary file <a href="#sending-a-binary-file" id="sending-a-binary-file"></a>

To send a binary file through _**REST V2**_, all you have to do is inform:

* the destination endpoint
* the content type (MIME Type of the file) in the header (eg.: application/pdf)
* the path where the file can be found (show it in the **File Name** field)

### How to make requests by using content-type: MultiPart/form-data <a href="#how-to-make-requests-by-using-content-type-multipartform-data" id="how-to-make-requests-by-using-content-type-multipartform-data"></a>

The first thing you have to do is to specify this header in the component (Content-Type: Multipart/form-data).

After that, when selecting any HTTP verb (except to GET), a field will be opened for you to specify the head of the payload to be sent. This must be the standard to:

* **specify fields**

```
{
"fields": {
     "field_name1": "field_value_1",
     "field_name2": "field_value_2",
     …….
    }
}
```

* **specify files**

```
{"files": {"file_field_name1": "path_where_the_file_is_found1","file_field_name2": "path_where_the_file_is_found2",…..}}
```

If you need to use both specifications, you can combine them with Double Braces expressions:

```
{
    "files": {
        "file_field_name1": "path_where_the_file_is_found1",
        "file_field_name2": "path_where_the_file_is_found2",
        …..
    }
}
```

### How to make requests by using content-type: **application/x-www-form-urlencoded** <a href="#h_0fa1297eb7" id="h_0fa1297eb7"></a>

The first thing you have to do is to specify this header in the component&#x20;

`(Content-Type: application/x-www-form-urlencoded).`

After that, when selecting any HTTP verb (except to GET), a field will be opened for you to specify the head of the payload to be sent.

Example:

```
{
    "files": {
        "file": {{ message.fileName }},
        "file2": {{ message.fileName2 }}
    },
    "fields": {
        "name": {{ message.name }},
        "'address": {{ message.address }}
    }
}
```

### Using accounts <a href="#using-accounts" id="using-accounts"></a>

See the accounts supported by **REST V2**:

* **APIKEY**

With URL-PARAM-NAME and API-KEY defined in the Basic-type account, the Platform makes the substitution in the call in the following way:

```
https://www.address.com?<URL-PARAM-NAME>=<API-KEY>
```

* **BASIC**

With USERNAME and PASSWORD defined in the Basic-type account, the Platform makes the substitution in the call in the following way:

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

**Authorization:** `Basic BASE64(<USERNAME>:<PASSWORD>)`

* **CUSTOM\_AUTH\_HEADER**

With HEADER-NAME and HEADER-VALUE defined in the CUSTOM\_AUTH\_HEADER-type account, the Platform makes the substitution in the call in the following way:

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

`<HEADER-NAME>: <HEADER-VALUE>`

* **OAUTH\_BEARER\_TOKEN**

If you already have a OAUTH token, you can save it in this type of account and the Platform makes the substitution in the call in the following way:

`h`[`ttps://www.address.com`](https://www.address.com/)

**HEADERS**

Authorization: `Bearer <TOKEN>`

* **OAUTH\_2**

It's specific of each type of supported provider. With this account, the access token is given the way each provider expects.

**Microsoft and Google**

[`https://www.address.com`](https://www.address.com/)

**HEADERS**

**Authorization:** `Bearer <ACCESS_TOKEN>`

**Mercado Livre**

`https://www.address.com?access_token=`\<ACCESS\_TOKEN>

To have an overview about the use of accounts, click [here](../../settings/accounts/) and access our other article.

* **GOOGLE\_KEY**

You can go for this account if it's necessary to use a key for authentication in the Google service.

To have an overview about the use of accounts, access our [documentation](../../settings/accounts/).&#x20;

* **AWS\_4**

For you to access some AWS service via REST, it's necessary to use this type of account. With it, the component is responsible for generating the headers of authentication and signing the message. To make it possible, we use the AWS 4 signature.

{% hint style="warning" %}
For DynamoDB, it's necessary to specify the header:
{% endhint %}

* **`X-Amz-Target = DynamoDB_20120810.GetItem`**

If you want to search an item in the database

* **`X-Amz-Target = DynamoDB_20120810.PutItem`**

If you want to insert data, access the [AWS documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.LowLevelAPI.html) and know which header to specify in the use of DynamoDB.

For other AWS services it's necessary to check if the header **X-Amz-Content-Sha256** is mandatory. In this case, you must inform in the header of the component the “required” value:

`X-Amz-Content-Sha256 = required`

And if it's necessary to use more than one account type in the same call, get rid of your doubts about _Double Braces custom account_ by clicking [here](broken-reference).
