---
description: Learn how to download logs from a pipeline execution.
---

# Pipeline execution logs download

{% hint style="info" %}
**Important information:**

* To access Pipeline Execution Logs Download and use all the features in this article, you need to have permission EXPORT:READ. Learn more in the[ Roles documentation](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
* The default Support, Developers, and Governance Manager groups already have permissions, but if you prefer, you can add the system role to your access group.
{% endhint %}

You can download logs of a given pipeline execution related to a specific pipeline execution key in CSV format via the page **Completed Executions** in Monitor.

A **pipeline execution key** is a unique identifier for each execution of a pipeline.

To use the feature, follow the steps below:

1. Access the **Completed Executions** page.
2. On the box icon, under the Action column, click **Download Execution Logs**.&#x20;
3. On the confirmation dialog (pop-up), click **Download pipeline execution key logs**, then **Download** and obtain a CSV file up to 5MB.

<figure><img src="../../.gitbook/assets/Download Logs EN.gif" alt=""><figcaption></figcaption></figure>

The CSV file contains the following information:

* timestamp
* realm
* pipelineKey
* pipelineName
* logLevel
* logMessage

It’s now also possible to customize the separator by characters of the user’s choice, limited to one character at a time, being the default character a “;” (semicolon). Note that you must select the same exported character separator when opening the file in the CSV reader for it to work correctly.
