---
description: Learn how to use alerts to monitor your pipelines.
---

# Alerts

{% hint style="info" %}
**Important information:**

* To access the Alerts page and use all the features in this article, you need to have permissions ALERT:READ, ALERT:CREATE, ALERT:UPDATE and ALERT:DELETE. Learn more in the [Roles documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).&#x20;
* The default Support, Developers, and Governance Manager groups already have them, but if you prefer, you can add the system role to your access group.
{% endhint %}

To access the alerts page, you must belong to groups that are bound to the **Alert Manager** system role, such as the **Support** and **Governance Manager** default groups.

Alerts work by continuously monitoring your pipelines in real-time and sending you a notification when a pipeline metric falls out of a specified range.

Setting up alerts can help you ensure that problems in your integration flows are quickly identified and fixed to reduce the risk of downtime or data loss.

In the alerts page, you can [create](https://docs.digibee.com/documentation/monitor/alerts/how-to-create-an-alert), [edit](https://docs.digibee.com/documentation/monitor/alerts/how-to-edit-an-alert), [activate](https://docs.digibee.com/documentation/monitor/alerts/how-to-activate-or-deactivate-an-alert) and [delete](https://docs.digibee.com/documentation/monitor/alerts/how-to-delete-an-alert) alerts.

Currently, these are the pipeline metrics you can use to set up alerts:

* [Pipeline Executions ](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/executions-per-second)
* [Pipeline Executions per Instance](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/pipeline-execution-per-instance)
* [Pipeline Inflight Executions](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/pipeline-inflight-executions)
* [Pipeline Messages on Queue ](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/messages-on-queue)
* [Pipeline Message Size](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/pipeline-message-size)
* [Pipeline Memory Usage](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/pipeline-memory-usage)
* [Pipeline Response Time](https://docs.digibee.com/documentation/monitor/alerts/available-metrics/pipeline-response-time)

## The alerts page

This page displays the alerts created for the selected environment. You can change the environment using the environment selector in the upper left corner.

<figure><img src="../../.gitbook/assets/1.The alerts page_EN.png" alt=""><figcaption><p><em>The alerts page</em></p></figcaption></figure>

The alerts page displays a table with the following variables:

* **Alert name:** the name assigned to the alert.

{% hint style="info" %}
It’s not possible to add special characters like "\_" to the alert name. The only exception is “-”, which can be used as a substitute for a blank space.&#x20;
{% endhint %}

* **Pipeline:** the pipeline to which the alert is assigned.
* **Status:** status of the alert, if activated or deactivated.

{% hint style="info" %}
When we first create an alert, **it’s by default deactivated** and needs to be **manually activated**.&#x20;
{% endhint %}

You can perform the following actions on the alerts page:

* [Create an alert](https://docs.digibee.com/documentation/monitor/alerts/how-to-create-an-alert)
* [Edit an alert](https://docs.digibee.com/documentation/monitor/alerts/how-to-edit-an-alert)
* [Activate or deactivate an alert](https://docs.digibee.com/documentation/monitor/alerts/how-to-activate-or-deactivate-an-alert)
* [Delete an alert](https://docs.digibee.com/documentation/monitor/alerts/how-to-delete-an-alert)
* [How to configure alerts on Slack](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-slack)
* [How to configure alerts on Telegram](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-on-telegram)
* [How to configure alerts through a webhook](https://docs.digibee.com/documentation/monitor/alerts/how-to-configure-alerts-through-a-webhook)

### Configuration with a single pipeline

The alert is related to the Major version of the deployed pipeline. If your pipeline has more than one Major version, you must create an alert for each Major version in your pipeline.&#x20;

However, this does not apply to the Minor versions of the pipeline, that is, if a pipeline has more than one Minor version, the configured alert remains valid for its Major version.

[In this article you can find more information about pipeline versioning.](https://docs.digibee.com/documentation/build/pipelines/pipeline-versioning)

### Configuration by realm

These alerts apply to all pipelines deployed in each realm. Once the alert is configured, all pipelines can generate a notification as long as they reach the threshold for the selected and configured metric.

[To learn more about the available metrics, read our documentation.](https://docs.digibee.com/documentation/monitor/alerts/available-metrics)

\
\
