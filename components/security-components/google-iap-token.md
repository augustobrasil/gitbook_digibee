---
description: >-
  Discover more about the Google IAP Token component and how to use it on the
  Digibee Integration Platform.
---

# Google IAP Token

The Google IAP Token component enables users to generate OpenID-type tokens for IAP (Identity Aware Proxy) proxies authentication.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="399">Description</th><th width="141.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>IAP Client ID</strong></td><td>It's the OAuth client ID, generated through the GCP platform, for resources protected by IAP.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Private Key</strong></td><td>It's the Account key containing the private key from the Google service account.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution. Otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="info" %}
In order to generate the token, it’s necessary to create a service account on Google Cloud and use the private key to configure an Account on the Digibee Integration Platform.
{% endhint %}

## Messages flow <a href="#h_6800fdfb9f" id="h_6800fdfb9f"></a>

### **Input** <a href="#h_1ecf22b816" id="h_1ecf22b816"></a>

No specific input message is expected. All it takes is to fill the required fields of each operation.

### **Output** <a href="#h_1d4ef0986a" id="h_1d4ef0986a"></a>

#### **Object**

```
{    
    "success": true,    
    "token": "eyJhbGciOiJSUz",    
    "refreshToken": "eyJhbGciOiJSUzI1N"
}
```

#### **Error**

```
{  
    "success": false,  
    "message": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Error loading connector google-authenticator-connector. Error: com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: Invalid account type received: GOOGLE_KEY"
    }
```

* **success:** “false” due to an execution error.
* **message:** it’s the component error message.
* **error:** it’s the error message received from the Google IAP Token component.

To understand how the messages flow work in the Digibee Integration Platform, [read the Messages processing documentation](../../build/pipelines/messages-processing.md).
