---
description: >-
  The new version of the Pipeline Engine provides a new feature to dynamically
  configure the credentials for each pipeline run.
---

# Support Dynamic Accounts (Restricted Beta)

{% hint style="info" %}
Currently, this feature is in the [Restricted Beta phase](https://docs.digibee.com/documentation/general/beta-program) and is only available to specific customers.
{% endhint %}

In the current version of the Pipeline Engine of the Digibee Integration Platform, account configuration is done statically, and it is not possible to change them at runtime. This can slow down processes in some scenarios. For example: receiving a certificate from an endpoint and authenticating in a REST API or receiving an ephemeral authentication token for dynamic authentication over an SFTP.\
\
Now, customers who use multipurpose pipelines on the Digibee Integration Platform can change their credentials configurations on the Runtime screen, through the new [Store Account component](https://docs.digibee.com/documentation/components/tools/store-account-restricted-beta).

With the new functionality, Digibee simplifies credential management, providing greater agility and security at all stages of your workflow. **Now it will be possible to support dynamic accounts for Digibees Customers using Engine v2**.

### **Architecture**

The dynamic accounts functionality allows you to adapt account settings to the specific needs of each connector, maximizing the efficiency of your integrations and processes. This update is available as a new parameter configuration for the following Digibee Integration Platform components:

* [SAP](https://docs.digibee.com/documentation/components/untitled/sap)
* [SFTP](https://docs.digibee.com/documentation/components/file-storage/sftp)
* [FTP](https://docs.digibee.com/documentation/components/file-storage/ftp)
* [REST v2](https://docs.digibee.com/documentation/components/web-protocols/rest-v2)
* [SOAP v3 ](https://docs.digibee.com/documentation/components/web-protocols/soap-v3-beta)
* [DB v2](https://docs.digibee.com/documentation/components/structured-data/db-v2)
* [Kafka](https://docs.digibee.com/documentation/components/queues-and-messaging/kafka)

The new configuration parameters are available in the documentation of each of their respective components.

{% hint style="info" %}
For your security, **never** store credentials openly anywhere, nor save them in the Object Store.
{% endhint %}

### How to use Dynamic Accounts in pipelines&#x20;

To add your dynamic credentials to the pipeline on the canvas, just follow these steps:

1. **Drag** the Store Account connector from the components list onto the canvas.
2. **Select** the type of account you want to register.
3. **Enter** the required credentials.
4. Click **save** and **run**.

Your credentials are now dynamically available on every pipeline run, ready to be referenced by other connectors.

### How to use Dynamic Accounts on Digibee Integration Platform components

It is very simple to use dynamic accounts in components:

1. **Enable** the **Use Dynamic Accounts** option on the desired connector (See list of components above).
2. **Enter** the name of the account previously created with the Store Account component in the **Account Name** field.
3. The connector is now **ready** to authenticate using this credential.

### Using Double Braces&#x20;

To use the account scope in the body of requests in connectors such as REST V2 and SOAP v3, just register the credential `{{ account.custom-1.password }}` using the **Store Account** connector. That way, you can easily use this information in your operations.\
\
For example, a BASIC type account was created using the Store Account and the name given to it was **account-test**. it will be enough to inform it like this: `{{account.account-test-password }}.`

{% hint style="warning" %}
Use of the Store Account component in parallel scenarios, such as parallel execution or For Each, is **not recommended** on the Restricted Beta Phase.
{% endhint %}
