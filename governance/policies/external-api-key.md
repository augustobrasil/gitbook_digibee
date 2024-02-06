---
description: Learn more about External API Keys on the Digibee Integration Platform.
---

# External API Key

{% hint style="info" %}
The External API Keys feature is currently in beta phase. Learn more about the[ Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

External API key is a security standard used for API calls, allowing pipelines to be safely accessed over the Internet via HTTP.

You can choose between 3 options for each environment, as described below:

* **Use API Key:** all pipelines that use a trigger that exposes your pipeline for external calls must use a key. You can activate this option when configuring a trigger.
* **Use Token JWT:** all pipelines that use a trigger that exposes your pipeline for external calls must use a JWT token. This is similar to keys and has the same effect.
* **API Key, Token JWT, or neither:** this option allows the developer to choose whether to use one of the above-mentioned options or not. We strongly recommend you to use at least one of them.

In the image below, you can see how the alternatives are displayed and choose one for each environment. If you are not sure, go with the third option.

<figure><img src="../../.gitbook/assets/External EN.png" alt=""><figcaption></figcaption></figure>

## How it works

Once your **External API Key** policy is configured, each new pipeline must follow the rules according to your definitions. If a developer forgets to apply your policy, they will be reminded during the deployment phase. In other words, it isn't possible to deploy the pipeline, until they have resolved the issues.

[If you want to learn more about the concepts, refer to the Policies article.](https://docs.digibee.com/documentation/governance/policies)

To enable your API Key or JWT Token in your pipeline trigger, activate the toggle as shown in the image below:

<figure><img src="../../.gitbook/assets/Trigger (1).png" alt=""><figcaption></figcaption></figure>

## Creating your API Key

Now that you have your policy, and also a pipeline configured to use an API Key, you can create a new one or make use of an existing **External API Key** by accessing the Consumers (API Keys) page under the **Settings** menu.&#x20;

After you create your API Key, don't forget to associate it with your pipeline on both environments.&#x20;

[Read more in the  Consumers (API Keys) documentation.](https://docs.digibee.com/documentation/settings/api-keys-consumers)

## Creating your JWT Token

Once you decide to make use of **JSON Web Tokens**, it will be necessary to create a second pipeline that will serve as your login flow. The login flow is used to generate your JWT, so that can be used in your API calls.

[Please refer to the Digibee JWT (Generate and Decode) implementation if you want to learn more about it](https://docs.digibee.com/documentation/components/security-components/digibee-jwt/digibee-jwt-implementation).

\
