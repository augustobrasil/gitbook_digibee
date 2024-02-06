---
description: Learn how to create an alert.
---

# How to create an alert

{% hint style="info" %}
**Important information:**

* To access the Alerts page and use all the features in this article, you need to have permission ALERT:CREATE. Learn more in the [Roles documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).&#x20;
* The default Support, Developers, and Governance Manager groups already have them, but if you prefer, you can add the system role to your access group.
{% endhint %}

Please note that you also have the option to configure alert notifications via **email**, [**Slack**](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-slack), [**Telegram**](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram)**,** and [**Webhook**](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-through-a-webhook).&#x20;

<figure><img src="../../.gitbook/assets/2a.How to create an alert_EN.gif" alt=""><figcaption></figcaption></figure>

Follow these steps to create an alert:

1. Go to the **Settings** page.
2. Under Notifications, click on **Alerts**.
3. Click **Create**.
4. If you choose to create alerts by pipeline, select the pipeline to which you want to assign them.
5. Set up the alert according to the metric you want to use.

{% hint style="info" %}
**Important information:**

* Alert configurations may change depending on the metric you selected.
* [See the documentation for the currently available metrics for more information on setting them up.](https://docs.digibee.com/documentation/monitor/alerts/available-metrics)
{% endhint %}

6. Enter the email addresses to which the alert notification should be sent.

<figure><img src="../../.gitbook/assets/2b.How to insert multiple email addresses_EN.png" alt=""><figcaption><p><em>How to insert multiple email addresses</em></p></figcaption></figure>

7. Enter a name for the alert.

{% hint style="info" %}
It’s not possible to add special characters like "\_" to the alert name. The only exception is “-”, which can be used as a substitute for a blank space.
{% endhint %}

8. Enter the content of the email to be sent.

{% hint style="info" %}
**For steps 7 and 8:** if you leave these fields empty, a default message will be sent.
{% endhint %}

9. Click **Save**.

{% hint style="info" %}
When we first create an alert, **it’s by default deactivated** and needs to be **manually activated**.&#x20;
{% endhint %}
