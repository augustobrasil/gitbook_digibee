---
description: Know the component and how to use it.
---

# SOAP V1 (Deprecated)

{% hint style="warning" %}
The **SOAP V1** is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [SOAP V2](https://docs.digibee.com/documentation/components/web-protocols/soap-v2) or [SOAP V3](https://docs.digibee.com/documentation/components/web-protocols/soap-v3-beta).&#x20;
{% endhint %}

**SOAP V1** invokes SOAP endpoints from a pipeline. It uses a Apache FreeMarker template to generate the SOAP request message and converts the response from SOAP to JSON, trying its best not to disrupt the translation.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>URL</strong></td><td>URL to be called - it may contain parameters following the {:param1} pattern, which will be replaced by the corresponding input message property.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Content Type</strong></td><td>Configures the Content Type and encoding.</td><td>N/A</td><td>String</td></tr><tr><td><strong>SOAP Action</strong></td><td>XML call header.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Account</strong></td><td>Account to be used by the component.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Template</strong></td><td>Apache FreeMarker template for the SOAP message to be sent in the request.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Connection Timeout</strong></td><td>Connection expiration time (in milliseconds).</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Reading Timeout</strong></td><td>Maximum time for reading (in milliseconds).</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Stop On Client Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Stop On Server Error</strong></td><td>If activated, the option will generate an error and suspend the pipeline execution.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Advanced configurations.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Allow Insecure Calls To HTTPS Endpoints</strong></td><td>When activated, the option allows non-reliable calls to HTTPS endpoints to be made.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Enable Retries</strong></td><td>When activated, the option allows new tries.</td><td>N/A</td><td>Boolean</td></tr><tr><td><strong>Maximum Number Of Retries Before Giving Up</strong></td><td>Maximum number of retries before giving up the call.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Time To Wait Before Each Retry</strong></td><td>Maximum time between retries (in milliseconds).</td><td>N/A</td><td>Integer</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{
	header: {
		"headerA":"valueA",
		"headerB":"valueB"
	},
	body: {
		// message structure that will be replaced by the Dust template
}
```

### Output <a href="#output" id="output"></a>

* successful

```
{
    status: XXX,
    body: {},
    headers: {}
}
```

* with error

```
{
    error: "error message",
    code: XXX,
    body: {},
    headers: {}
}
```

{% hint style="info" %}
For some errors, body and headers are unavailable.
{% endhint %}

## SOAP V1 in Action <a href="#soap-v1-in-action" id="soap-v1-in-action"></a>

### **About the template variable** <a href="#about-the-template-variable" id="about-the-template-variable"></a>

The name of the variable can also have minus (-), dot (.) and colon (:) at any position, but they must be escaped with a preceding backslash (\\). Otherwise, they can be interpreted as operators.

### **About numbers substitution** <a href="#about-numbers-substitution" id="about-numbers-substitution"></a>

```html
<#assign x=42>
  ${x}
  ${x?string}  <#-- the same as ${x} -->
  ${x?string.number}
  ${x?string.currency}
  ${x?string.percent}
  ${x?string.computer}
```

Output

```
42
42
42
$42.00
4,200%
42
```

**Number format**

```
<#setting number_format="0.####">
```

**To check if the field isn't null:**

```
<#if varTest??>${varTest}</#if>
```

### &#x20;SoapUI calls reprocedures in SOAP V1 <a href="#soapui-calls-reprocedures-in-soap-v1" id="soapui-calls-reprocedures-in-soap-v1"></a>

![](<../../.gitbook/assets/soap v1.png>)
