---
description: >-
  Discover more about the WGet (Download HTTP) component and how to use it on
  the Digibee Integration Platform.
---

# WGet (Download HTTP)

**WGet (Download HTTP)** is a component that downloads an arbitrary file via a URL.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.&#x20;

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>Where the file will be downloaded from - Double Braces expressions are supported.</td><td>https://sendgrid.com/docs/API_Reference/Web_API_v3/Mail/index.html</td><td>String</td></tr><tr><td><strong>Headers</strong></td><td>Headers of the call.</td><td>N/A</td><td>Key-value Pairs</td></tr><tr><td><strong>Query Params</strong></td><td>Query parameters of the call.</td><td>N/A</td><td>Key-value Pairs</td></tr><tr><td><strong>Account</strong></td><td>Account to be used by the component. Supported accounts: ApiKey, Basic, Certificate Chain, Custom Auth Header, Oauth2, and Oauth Bearer Token.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Allow Insecure Calls To HTTPS Endpoints</strong></td><td>When activated, the option allows non-reliable calls to HTTPS endpoints to be made.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Binary File</strong></td><td>If activated, the option returns the base64 of the file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Local Save</strong></td><td>If activated, the option allows the file to be saved locally.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name or full file path (i.e. tmp/processed/file.txt) of the local file to be downloaded or uploaded.</td><td>N/A</td><td>String</td></tr></tbody></table>

## WGet in action <a href="#wget-in-action" id="wget-in-action"></a>

### Example with static Double Braces <a href="#example-with-static-double-braces" id="example-with-static-double-braces"></a>

URL

```
https://sendgrid.com/docs/API_Reference/Web_API_v3/Mail/index.html
```

### Example with dynamic Double Braces <a href="#example-with-dynamic-double-braces" id="example-with-dynamic-double-braces"></a>

URL

```
{{ message.example.url }}
```

```
https://www.download.com/file/{{ message.id }}/pdf
```

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

If using Double Braces to fill in the parameters, you don’t have to specify the input format&#x20;

**File Name** overrides the default name and **URL** overrides the default URL.

### Output <a href="#output" id="output"></a>

If the option **Local Save** is activated:

```
{
    "fileName": "","success": ""    
}
```

If the options **Local Save** and **Binary File** are activated:

```
{
    "fileBase64": ""
}
```

If the options **Local Save** and **Binary File** are NOT activated:

```
{
    "fileText": ""
}
```

In case of errors:

```
{
    "error": {
        "exception": "",
        "message": ""
    }
}
```
