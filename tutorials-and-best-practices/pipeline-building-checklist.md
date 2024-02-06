---
description: Learn what you should look for before deploying a pipeline
---

# Pipeline building checklist

To ensure the safety and efficiency of your integration flows, you should always review the following points before deploying a pipeline:

## Use API Keys <a href="#qrct7r3o0lig" id="qrct7r3o0lig"></a>

If you use [HTTP](../components/triggers/http-trigger.md), [REST](../components/triggers/rest-trigger.md), or [HTTP File](../components/triggers/http-file-trigger/) triggers on your pipelines, the services created by those pipelines will be exposed on the Internet.

By default, for security reasons, the Digibee Integration Platform only allows the use of these triggers along with an API key.

To create an API key:

1. Go to **Configurations**;
2. Click on **Consumers**;
3. Choose the desired environment;
4. Click on **CREATE**.

{% hint style="info" %}
Create a different API key for each system that consumes an API, and restrict access only to the desired pipelines.
{% endhint %}

Aside from using API keys, we also recommend that you increase the security of your pipelines by using a [JWT](../components/security-components/jwt-deprecated.md) (JSON Web Token).

Although we strongly advise against it, if you wish to publish a pipeline with the aforementioned triggers without an API key, send us a request via Intercom using the following template:

> I request the inclusion of the following pipelines in the whitelist not to use an API Key.
>
> * Realm name
> * Name of the pipeline(s) to be included in the realm’s whitelist
> * Reason for the request

## Store usernames and passwords on the Accounts page <a href="#id-3ymitm2dkyw5" id="id-3ymitm2dkyw5"></a>

If you use a username and password to access a service in an integration flow, don’t expose them in a component’s configuration settings. Instead, store the login and password on [the Accounts page](../settings/accounts/) and refer to them in the component settings.

## Censor Sensitive fields <a href="#uo494fvvwmf" id="uo494fvvwmf"></a>

[Set sensitive fields in the pipeline configurations](../build/new-canvas-beta-restricted/#h\_f0d7247948) to censor this information in pipeline logs and messages.

## Use the HTTPS protocol <a href="#w4b2u5ppknwp" id="w4b2u5ppknwp"></a>

Whenever possible, use HTTPS instead of HTTP requests when accessing an external service in your integration flows.

## Clear Object Store and encrypt sensitive data <a href="#oh28ar2ofd53" id="oh28ar2ofd53"></a>

If you store sensitive data in an [Object Store](../components/structured-data/object-store.md), encrypt it. You can do this using [cryptography components](../components/security-components/).

Additionally, be sure to clear the Object Store periodically. Object Stores are auxiliary databases that help you develop integration flows. They are not intended to store large amounts of data.

If you don’t clear your Object Store periodically, it can cause errors in your integration flows.

## Use the Script component only when necessary <a href="#dtqoqf8eynr9" id="dtqoqf8eynr9"></a>

The [Script component](../components/tools/script.md) should only be used if there are no components on the Digibee Integration Platform that perform the desired task.

If you find yourself in a situation where you think you should use the Script component, contact our team. Maybe we can suggest a solution using our components.

## Check the response when connecting to external services <a href="#id-7zrojenam3q" id="id-7zrojenam3q"></a>

If you use a component in your pipeline to make a request to an external service, such as an API or database, check that the response type matches the expectations for that request. If it does not, make sure to take an action, such as reprocessing or generating an error.

To learn more about this, read [our documentation on event-driven architecture](event-oriented-architecture.md).
