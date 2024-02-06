---
description: >-
  Discover how users can configure Cross-Origin Resource Sharing (CORS) for
  triggers HTTP, HTTP File and Rest while using the Digibee iPaaS.
---

# CORS - Global Configuration

CORS stands for Cross-Origin Resource Sharing. It is a mechanism that allows informing the browser the origins which have permission for requests to the server.

Digibee offers the option of configuring CORS parameters globally for your realm so that it updates your triggers HTTP, HTTP File and REST. The triggers that use HTTP protocol will return response headers according to the CORS specifications. Here are some examples of configuration:\


```
 "Access-Control-Allow-Origin":"mydomain1.com,mydomain2.com",
 "Access-Control-Allow-Methods": "GET,POST,DELETE",
 "Access-Control-Allow-Headers": "Authorization,x-digibe-custom-header ",
 "Access-Control-Expose-Headers": "x-digibe-custom-header",
 "Access-Control-Allow-Credentials": "true"
```

### **How to Configure**

In order to configure CORS in your realm, contact our support team through the chat within the Digibee Integration Platform.

{% hint style="info" %}
**IMPORTANT:** This feature is part of our [Beta program](../../../general/beta-program.md).
{% endhint %}

\
