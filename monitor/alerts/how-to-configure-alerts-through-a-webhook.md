---
description: Learn how to configure notification alerts using a webhook.
---

# How to configure alerts through a webhook

{% hint style="info" %}
&#x20;**Important information:**

* When we first create an alert, **it’s by default deactivated** and needs to be **manually activated**.
{% endhint %}

A webhook can be used to integrate with an existing customer flow. However, it is important to note that the endpoint needed to activate the webhook must be provided by the customer beforehand, as it is not created by the Digibee Integration Platform.

In addition to configuring alerts via email or [Telegram](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram), you can also use a webhook to set up your alerts.

Follow these steps to configure your alerts using a webhook:

1. Go to the **Settings** page.
2. Under Notifications, click on **Alerts**.
3. Click **Create**.
4. Select the pipeline to which you want to assign the alert.
5. Set up the alert according to the metric you want to use.
6. Activate the **Webhook** toggle.
7. Copy the endpoint and place it in the required field.

<figure><img src="../../.gitbook/assets/8.How to configure alerts through a webhook_EN.png" alt=""><figcaption></figcaption></figure>

After the configuration process is complete, the following JSON output is generated:

```
{
    "realm": "realm",
    "environment": "env",
    "alertName": "Alert-name",
    "pipelineName": "pipeline",
    "startsAt": "0001-01-01T00:00:00Z",
    "endsAt": "0001-01-01T00:00:00Z",
    "status": "firing" // This field can be firing or resolved
}

```
