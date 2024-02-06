---
description: >-
  Discover more about the HTTP File Trigger and how to use it on the Digibee
  Integration Platform.
---

# HTTP File Trigger - Downloads

**HTTP File Trigger** downloads large files in a robust and efficient way, calling the GET method.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="213">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Methods</strong></td><td>Defines the methods accepted by the pipeline.</td><td>GET, PUT, POST, PATCH, and DELETE</td><td>String</td></tr><tr><td><strong>Response Headers</strong> <code>(DB)</code></td><td>Headers to be returned by the endpoint when processing in the pipeline is complete. This parameter cannot be left empty and accepts Double Braces. Special characters should not be used in keys, due to possible failures in proxies and gateways.</td><td>N/A</td><td>Key-value pairs</td></tr><tr><td><strong>Add Cross-Origin Resource Sharing (CORS)</strong></td><td>Adds the CORS headers to be returned by the endpoint when processing in the pipeline is complete. Cross-Origin Resource Sharing (CORS) is a mechanism that lets you tell the browser which origins are allowed to make requests.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>CORS Headers</strong></td><td>Defines CORS specifically for the pipeline and its constraints. To configure globally rather than individually on each pipeline, <a href="https://docs.digibee.com/documentation/components/triggers/triggers-settings/cors-global">see the CORS Global article</a>.</td><td>N/A</td><td>Key-value pairs</td></tr><tr><td><strong>Form Data Uploads</strong></td><td>Enables/disables the receipt of the form data upload (multipart form data).</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body Uploads</strong></td><td>Enables/disables the receipt of bodies upload.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Body Upload Content Types</strong></td><td>Defines the content types allowed by the pipeline for the bodies upload.</td><td>application/pdf, application/jpeg</td><td>String</td></tr><tr><td><strong>Response Content Types</strong></td><td>Defines the response content types allowed by the pipeline - when configuring this response, you determine the response format.</td><td>text/xml, application/xml</td><td>String</td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Maximum time (in milliseconds) that the pipeline takes to process information before returning a response. If the processing takes longer than the parameter definition, the request is finished and returns status code 500, but without a body. Default: 30000. Limit: 900000.</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Maximum Request Size</strong></td><td>Defines the maximum size of the file in the upload request (in MB). Maximum: 100 MB.</td><td>50</td><td>Integer</td></tr><tr><td><strong>External API</strong></td><td>If activated, the option publishes the API in an external gateway.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Internal API</strong></td><td>If activated, the option publishes the API in an internal gateway.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>mTLS enabled API</strong></td><td>If the option is activated, the API is published to a gateway dedicated to APIs with mTLS enabled by default. In this case, the access host will be different from the others. The pipeline can have both the <strong>External API</strong> and <strong>Internal API</strong> options enabled at the same time, but it is recommended to leave them inactive. This parameter does not support API Key and JWT. To use it in your realm, it is necessary to make a request via chat, and we will send you the necessary information to install this service.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>API Key</strong></td><td>If activated, the option will request the key for the API consumption.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Token JWT</strong></td><td>If activated, the option will request the token for the API consumption.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Basic Auth</strong> <a href="https://docs.digibee.com/documentation/general/beta-program"><strong>(Beta Phase)</strong></a></td><td>If the option is activated, the endpoint can only be consumed if a Basic Auth setting is present in the request. This setting can be registered beforehand through the <strong>Consumers</strong> page in the Digibee Integration Platform.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Additional API Routes</strong></td><td>If activated, the option allows you to add new routes.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Remove Digibee Prefix from Route</strong></td><td>This option is available only when <strong>External API</strong> and <strong>Internal API</strong> parameters are disabled, and <strong>mTLS enabled API</strong> and <strong>Additional API Routes</strong> parameters are enabled. Set this option to remove the default Digibee route prefix "/pipeline/{realm}/v{n}" from the pipeline route. <a href="http-file-trigger-downloads.md#remove-digibee-prefix-from-route">Learn more about the <strong>Remove Digibee Prefix from Route</strong> parameter in the section below</a>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>API Routes</strong></td><td>Custom routes.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Rate Limit</strong></td><td>If the option is activated, a rate limiting configuration will be applied on the API gateway. This option is only available if <strong>API Key</strong> or <strong>Basic Auth</strong> is active. <a href="http-file-trigger-downloads.md#http-file-trigger-in-action">See more about the <strong>Rate Limit</strong> parameter in the section below</a>.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Limit by</strong></td><td>Defines the entity to which the limits will be applied. Options: API.</td><td>API</td><td>String</td></tr><tr><td><strong>Aggregate by</strong></td><td>Defines the entity for aggregating the limits. Options: Consumer and Credential (API Key, Basic Auth).</td><td>Consumer</td><td>String</td></tr><tr><td><strong>Options</strong></td><td>Defines the limit of requests that can be made within a time interval.</td><td>N/A</td><td>Options of Rate Limit</td></tr><tr><td><strong>Interval</strong></td><td>Defines the time interval for the limit of requests. Options: second, minute, hour, day, and month.</td><td>second</td><td>String</td></tr><tr><td><strong>Limit</strong></td><td>Defines the maximum number of requests that users can make in the specified time interval.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>If activated, the option allows messages to be redelivered in case of Pipeline Engine failure.</td><td>N/A</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
There is a global configuration parameter that obliges all the pipelines to be published with **at least** the **API Key** or **Basic Auth** options enabled.
{% endhint %}

## Parameters additional information

### **Add Cross-Origin Resource Sharing (CORS) - CORS Headers**

We use a comma to enter multiple values in a header, but we don't add a space before or after the comma. Special characters should not be used in keys, due to possible failures in proxies and gateways.

## Remove Digibee Prefix from Route

As previously explained, this option is recommended for removing the default Digibee route prefix from the pipeline route.

Let’s say you’ve created a pipeline and set the trigger as follows:

<figure><img src="../../../.gitbook/assets/Doc update triggers Remove Digibee Prefix mar 2023 (2).png" alt=""><figcaption></figcaption></figure>

With the configurations applied and the pipeline deployed, you will get a new URL:

```
https://test.godigibee.io/products

```

{% hint style="info" %}
When removing the default prefix and setting the pipeline route through the **Additional API Routes** parameter, be careful not to set an existing pipeline route used by other pipelines. In case you have more than one pipeline major version, it’s also important to keep in mind that the pipeline route versioning must be done by the user due to the absence of a versioning path parameter. For example: /pipeline/realm/v1/.
{% endhint %}

## Rate Limit  <a href="#http-file-trigger-in-action" id="http-file-trigger-in-action"></a>

When creating APIs, we usually want to limit the number of API requests users can make in a given time interval.

This action can be performed by activating the **Rate Limit** option and applying the following settings:



<figure><img src="../../../.gitbook/assets/REST trigger rate limit example ago 2023 (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If the API has additional paths, the limit is shared among all paths. To apply the rate limit settings, the API must be configured with an API key or Basic Auth so that the **Aggregate by** parameter can be used by groups of credentials if the Consumer option is selected, or by an individual credential if the Credential option (API Key, Basic Auth) is selected.

If multiple **interval** parameters are configured with repeating values, only one of these values is considered. It’s also necessary that a value greater than zero be informed for the **Limit** parameter.

If the rate limiting options aren't set correctly, they'll be ignored and a warning log will be issued. You can view this log on the Pipeline Logs page.
{% endhint %}

## HTTP File Trigger in action <a href="#http-file-trigger-in-action" id="http-file-trigger-in-action"></a>

### Scenario: GET with any content type <a href="#scenario-get-with-any-content-type" id="scenario-get-with-any-content-type"></a>

Let's say you have a file with more than 5MB. You can call a pipeline endpoint configured with HTTP Trigger via GET with any content type for the request to be received and treated. The file is returned according to the output content type and its "as-is" content.

For that to happen, all you have to do is follow these steps:

1. Create a pipeline and configure its trigger as HTTP-File, including the GET method and the accepted **Response Content Types**.
2. Insert a File Connector in the pipeline to search the file to be enabled. You can, for example, configure **WGet** to obtain a file of a URL sent to the endpoint during a call.
3. Insert **JSON Generator** as the last step of your pipeline so that a JSON is generated in the following format:

```
{ 
    "file": "file-download.pdf", 
    "Content-Type": "application/pdf"
}
```

{% hint style="info" %}
This step is fundamental for _**HTTP File Trigger**_ to understand that the file works.
{% endhint %}

4\. Deploy the pipeline.

5\. Create a consumer and configure it so that it has access to the pipeline_._

6\. Call the pipeline through this curl:

```
curl https://godigibee.io/pipeline/realm_name/v1/pipeline_name -v -H 'Content-Type: application/pdf' -H 'apikey: generated_token' -H 'urlDownload: http://url/path'
```

* **realm\_name:** refers to the realm where the pipeline is located.
* **generated\_token:** refers to the API Key generated by the recently created consumer.
* **urlDownload:** parameter sent for WGet Connector to solve the value of the URL field. The attribute isn't mandatory but allows a more flexible approach through Double Braces. It works perfectly if you define the "path" directly in WGet Connector.

## HTTP File Trigger Response <a href="#http-file-trigger-response" id="http-file-trigger-response"></a>

It's simple to define the pipeline response format. Add a Transformer to the end of the pipeline and define the response:

```
{  
    "file": "file-download.pdf",  
    "code": 200,  
    "Content-Type": "application/pdf"
}
```

{% hint style="info" %}
_**Content-Type**_ must be one of the values defined in _**Response Content Types**_.
{% endhint %}

**HTTP File Trigger** responds to bodies that aren't files in the same way **HTTP Trigger** does. It allows the pipeline to respond with the file or with any other content type according to the invocation context. For **HTTP File Trigger** to respond with any body, the last step of the pipeline must have this structure:

```
{ 
    "body": "information that will be written in the endpoint output", 
    "Content-Type": "body content type", 
    "code": <a HTTP return code>
}
```
