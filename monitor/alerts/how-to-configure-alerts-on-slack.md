---
description: Learn how to configure notification alerts on Slack.
---

# How to configure alerts on Slack

{% hint style="info" %}
&#x20;**Important information:**

* When we first create an alert, it’s by default **deactivated** and **needs to be manually** **activated**.
* The notifications are available in Portuguese only.
{% endhint %}

In addition to configuring alerts via email, [Telegram](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram) or [Webhook](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-through-a-webhook), you can also use Slack as a channel to set up your alerts.

Follow these steps to configure alerts on Slack:

1. Log in to **Slack**.
2. Install the [Incoming Webhooks](https://godigibee.slack.com/apps/A0F7XDUAZ-webhooks-de-entrada?tab=more\_info) app on Slack.

{% hint style="info" %}
Only Slack administrators are able to install apps. If you don’t have this right, click **Request configuration** or contact your administrator directly.
{% endhint %}

3. Click **Add to Slack**.
4. Choose on which channel you want to receive alert notifications or create a new channel.
5. Click **Add integration with Incoming Webhooks**.
6. Copy and save the **Webhook URL**.
7. Personalize the name of the alert and the icon if you prefer.
8. Save settings.

Follow these steps to finalize configuring the alerts on the Digibee Integration Platform:&#x20;

1. Create the alert following the steps explained in the[ “How to create an alert documentation"](https://docs.digibee.com/documentation/monitor/alerts/how-to-create-an-alert).
2. Activate the **Slack toggle**.

<figure><img src="../../.gitbook/assets/6.How to configure alerts on Slack_EN.png" alt=""><figcaption></figcaption></figure>

3. Insert the Webhook URL previously copied.
4. Click **Save**.
