---
description: >-
  Discover more about the HTTP File Trigger and how to use it for uploads on the
  Digibee Integration Platform.
---

# HTTP File Trigger - Uploads

**HTTP File Trigger** sends large files (with size greater than 5 MB) to pipelines in a robust and efficient way, using HTTP.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="303">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Methods</strong></td><td>Defines the methods accepted by the pipeline.</td><td>POST, PUT, GET, PATCH and DELETE</td><td>String</td></tr><tr><td><strong>Response Headers</strong> <code>(DB)</code></td><td>Headers to be returned by the endpoint when the pipeline processing is complete. This parameter cannot be left empty and accepts Double Braces. Special characters should not be used in keys, due to possible failures in proxies and gateways.</td><td>N/A</td><td>Key-Value Pairs</td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS) - CORS Headers</strong></td><td>Add the Cross-Origin Resource Sharing (CORS) headers to be returned by the endpoint when processing in the pipeline is complete. CORS is a mechanism that lets you tell the browser which origins are allowed to make requests. This parameter defines CORS specifically for the pipeline and its constraints. To configure globally instead of individually in each pipeline, see the <a href="https://docs.digibee.com/documentation/components/triggers/triggers-settings/cors-global">CORS Global article.</a></td><td>N/A</td><td>Key-Value Pairs</td></tr><tr><td><strong>Form Data Uploads</strong></td><td>Enables/disables the receipt of the form data upload (multipart form data).</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body Uploads</strong></td><td>Enables/disables the receipt of bodies upload.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body Upload Content Types</strong></td><td>Define the content types allowed by the pipeline for the bodies upload.</td><td>application/pdf, application/jpeg</td><td>String</td></tr><tr><td><strong>Response Content Types</strong> <code>(DB)</code></td><td>Defines the response content types allowed by the pipeline. For example, when configuring this response, you determine the response format.</td><td>text/xml, application/xml</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td><p>Maximum time (in milliseconds) that the pipeline takes to process information before returning a response. Limit: 900000.</p><p></p><p>If the processing takes longer than the parameter definition, the request is finished and returns status code 500, but without a body. </p></td><td>30000</td><td>Integer</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Defines the maximum size of the file in the upload request (in MB). Maximum: 100 MB.</td><td>100</td><td>Integer</td></tr><tr><td><strong>External API</strong></td><td>If activated, the option publishes the API in an external gateway.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Internal API</strong></td><td>If activated, the option publishes the API in an internal gateway.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>If the option is enabled, the API is published to a gateway dedicated to APIs with mTLS enabled by default. In this case, the access host will be different from the others. The pipeline can have both the <strong>External API</strong> and <strong>Internal API</strong> options enabled at the same time, but it is recommended to leave them inactive.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>API Key</strong></td><td>If the option is activated, the endpoint can be consumed only if an API key is previously configured in the Digibee Integration Platform.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Token JWT</strong></td><td>If activated, the option will request the token for the API consumption.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/general/beta-program"><strong>(Beta Phase)</strong> </a></td><td>If the option is activated, the endpoint can only be consumed if a Basic Auth setting is present in the request. This setting can be registered beforehand through the <strong>Consumers</strong> page in the Digibee Integration Platform.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Additional API Routes</strong></td><td>If activated, the option allows you to add new routes.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>This option is available only when <strong>External API</strong> and <strong>Internal API</strong> parameters are disabled, and <strong>mTLS enabled API</strong> and <strong>Additional API Routes</strong> parameters are enabled. Set this option to remove the default Digibee route prefix "/pipeline/{realm}/v{n}" from the pipeline route. Learn more about the <strong>Remove Digibee Prefix from Route</strong> parameter in the section below.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Routes</strong></td><td>Custom routes.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Rate Limit</strong></td><td>If the option is activated, a rate limiting configuration will be applied on the API gateway. This option is only available if <strong>API Key</strong> or <strong>Basic Auth</strong> is active. See more about the <strong>Rate Limit</strong> parameter in the section below.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Limit by</strong></td><td>Defines the entity to which the limits will be applied. Options: API.</td><td>API</td><td>String</td></tr><tr><td><strong>Aggregate by</strong></td><td>Defines the entity for aggregating the limits. Options: Consumer and Credential (API Key, Basic Auth).</td><td>Consumer</td><td>String</td></tr><tr><td><strong>Options</strong></td><td>Defines the limit of requests that can be made within a time interval.</td><td>N/A</td><td>Options for limit and interval</td></tr><tr><td><strong>Interval</strong></td><td>Defines the time interval for the limit of requests. Options: second, minute, hour, day, and month.</td><td>second</td><td>String</td></tr><tr><td><strong>Limit</strong></td><td>Defines the maximum number of requests that users can make in the specified time interval.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>If activated, the option allows messages to be redelivered in case of Pipeline Engine failure.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
There is a global configuration parameter that obliges all the pipelines to be published with **at least** the **API Key** or **Basic Auth** options enabled.
{% endhint %}

## Parameters additional information

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers**

We use a comma to inform multiple values in a header, but we don't add a space before or after the comma. Special characters should not be used in keys, due to possible failures in proxies and gateways.

### **mTLS enabled API**

This parameter does not support **API Key**, **JWT**, or **Basic Auth**. To use it in your realm, it is necessary to make a request via chat, and we will send you the necessary information to install this service.

## Remove Digibee Prefix from Route

As previously explained, this option is recommended for removing the default Digibee route prefix from pipeline route.

Let’s say you’ve created a pipeline and set the trigger as follows:

<figure><img src="../../../.gitbook/assets/HTTP FILE TRIGGER.png" alt=""><figcaption></figcaption></figure>

With the configurations applied and the pipeline deployed, you will get a new URL:

```
https://test.godigibee.io/products
```

{% hint style="info" %}
When removing the default prefix and setting the pipeline route through the **Additional API Routes** parameter, be careful not to set an existing pipeline route used by other pipelines. In case you have more than one pipeline major version, it’s also important to keep in mind that the pipeline route versioning must be done by the user due the absence of a versioning path parameter. For example: /pipeline/realm/v1/.
{% endhint %}

## Rate Limit <a href="#http-file-trigger-in-action" id="http-file-trigger-in-action"></a>

When creating APIs, we usually want to limit the number of API requests users can make in a given time interval.

This action can be performed by activating the **Rate Limit** option and applying the following settings:



<figure><img src="../../../.gitbook/assets/RATE LIMIT - HTTP FILE TRIGGER.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If the API has additional paths, the limit is shared among all paths. To apply the rate limit settings, the API must be configured with an API key or Basic Auth so that the **Aggregate by** parameter can be used by groups of credentials if the **Consumer** option is selected, or by an individual credential if the **Credential** (API Key, Basic Auth) option is selected.

If multiple interval parameters are configured with repeating values, only one of these values is considered. It’s also necessary that a value greater than zero be informed for the **Limit** parameter.

If the rate limiting options aren't set correctly, they'll be ignored and a warning log will be issued. You can view this log on the Pipeline Logs page.
{% endhint %}

## HTTP File Trigger in action <a href="#http-file-trigger-in-action" id="http-file-trigger-in-action"></a>

### Scenario 1: POST with `multipart/form-data` content type of file <a href="#scenario-1-post-with-multipartform-data-content-type-of-a-file" id="scenario-1-post-with-multipartform-data-content-type-of-a-file"></a>

Let's say you want to send a file with more than 5 MB. You can call a pipeline endpoint configured with **HTTP Trigger** via POST with the `multipart/form-data` content type for this file to be available to be worked by the pipeline.

See how to do that:

1. Create a pipeline and configure its trigger as HTTP-File, enabling the **Form Data Uploads** option.
2. Deploy the pipeline.
3. Create a consumer and configure it so that it has access to the pipeline_._
4. Call the pipeline through this curl:

```
curl -d “@file_name” https://godigibee.io/pipeline/realm_name/v1/http-file-upload -v -H 'Content-Type: application/pdf' -H 'apikey: generated_token'
```

* **file\_name:** refers to a local file.
* **realm\_name:** refers to the realm where the pipeline is located.
* **generated\_token:** refers to the API Key generated by the recently created consumer.

The pipeline will receive an array `files[]` containing:

* fileName
* param
* contentType

That way, the file can be referred and accessed from the pipeline:

```
{
  "body": null,
  "form": {},
  "headers": {
  ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "application/pdf",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {      
      "fileName": "55acdc09-c0fc-4f6a-b3ee-f4199076b0c4",
      "param": "body",
      "contentType": "application/pdf"    
    }  
  ]
}
```

### Scenario 2: POST with "multipart/form-data" content type of multiple files <a href="#scenario-2-post-with-multipartform-data-content-type-of-multiple-files" id="scenario-2-post-with-multipartform-data-content-type-of-multiple-files"></a>

Let's say you have multiple files with more that 5MB. You can call a pipeline endpoint configured with **HTTP Trigger** via POST with the "multipart/form-data" content type for these files to be available to be worked by the pipeline.

To make it possible, follow these steps:

1. Create a pipeline and configure its trigger as HTTP-File, enabling the **Form Data Uploads** option.
2. Deploy the pipeline.
3. Create a consumer and configure it so that it has access to the pipeline_._
4. Call the pipeline through this curl:

{% code overflow="wrap" %}
```
curl -F dgbfile1=@file_name1 -F dgbfile2=@file_name2 https://godigibee.io/pipeline/realm_name/v1/http-file-upload -v -H 'apikey: generated_token'
```
{% endcode %}

* **file\_name1:** refers to a local file.
* **file\_name2:** refers to a local file.
* **realm\_name:** refers to the Realm where the pipeline is located.
* **generated\_token:** refers to the API Key generated by the recently created consumer.

The pipeline will receive an array files\[] containing:

* fileName
* originalFileName
* param
* charset
* contentLength
* contentType

That way, the files can be referred and accessed from the pipeline:

{% code overflow="wrap" %}
```
{
  "body": "",
  "form": {},
  "headers": {
    ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "multipart/form-data; boundary=------------------------b3c985803b952f2c",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {
      "fileName": "96f3ecb2-1c72-4980-9f01-6f44cafc719f",
      "originalFileName": "file1",
      "param": "dgbfile1",
      "contentType": "application/octet-stream",
      "charset": "UTF-8",
      "contentLength": 5242880
    },
    {
      "fileName": "58fb844f-a1d1-4788-b9b4-30df4b69165e",
      "originalFileName": "file2",
      "param": "dgbfile2",
      "contentType": "application/octet-stream",
      "charset": "UTF-8",
      "contentLength": 5242880
    }
  ]
}
```
{% endcode %}

### Scenario 3: POST with any content type and body with more than 5MB <a href="#scenario-3-post-with-any-content-type-and-body-with-more-than-5mb" id="scenario-3-post-with-any-content-type-and-body-with-more-than-5mb"></a>

Let's say you have multiple files with more than 5MB. You can call a pipeline endpoint configured with **HTTP Trigger** via POST with any content type for these files to be available to be worked by the pipeline.

All you have to do is:

1. Create a pipeline and configure its trigger as HTTP-File, enabling the **Body Uploads** option.
2. Deploy the pipeline.
3. Create a consumer and configure it so that it has access to the pipeline_._
4. Call the pipeline through this curl:

{% code overflow="wrap" %}
```
curl -d '@file_name1' https://godigibee.io/pipeline/realm_name/v1/http-file-upload -v -H 'apikey: generated_token'
```
{% endcode %}

* **file\_name:** refers to a local file.
* **realm\_name:** refers to the realm where the pipeline is located.
* **generated\_token:** refers to the API Key generated by the recently created consumer.

The pipeline will receive an array `files[]` containing:

* fileName
* param
* charset
* contentType

That way, the files can be referred and accessed from the pipeline:

```
{
  "body": null,
  "form": {},
  "headers": {
    ...
  },
  "queryAndPath": {},
  "method": "POST",
  "contentType": "application/pdf",
  "path": "/pipeline/realm_name/v1/http-file-upload",
  "files": [
    {
      "fileName": "55acdc09-c0fc-4f6a-b3ee-f4199076b0c4",
      "param": "body",
      "contentType": "application/pdf"
    }
  ]
}
```

## HTTP File Trigger Response <a href="#http-file-trigger-response" id="http-file-trigger-response"></a>

It's simple to define the pipeline response format. Add a **Transformer** to the end of the pipeline and define the response:

```
{  
    "body": "<xml>Output 1</xml>",  
    "code": 200,  
    "Content-Type": "application/xml"
}
```

Another solution is indicated for situations where a response limitation occurs for payloads larger than 5 MB. \
\
In this case, it is recommended that the pipeline response be a file and not a payload. This can be done using the [**File Writer**](../../files/file-writer.md) component to generate the file and reference it in the pipeline response with the `"file"` property instead of the `"body"` property:

```
{
"file": {{ message.fileName }},
"code": 200,
"Content-Type": "application/json"
}

```

{% hint style="info" %}
**Content-Type** must be one of the values defined in **Response Content Types**.
{% endhint %}

Read the [**HTTP File Trigger - Downloads**](https://docs.digibee.com/documentation/components/triggers/http-file-trigger/http-file-trigger-downloads) article to learn how to make sure that the pipeline output will be a file.
