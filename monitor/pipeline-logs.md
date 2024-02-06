---
description: Visualize execution logs.
---

# Pipeline logs

Pipeline logs are detailed data that allow the user to see in depth what is happening with each execution present during the pipeline's running cycle.

In the pipeline logs tab, you can track the event logs that are recorded during the execution of a pipeline.

## Environment selection <a href="#h_86e7473448" id="h_86e7473448"></a>

You can select the desired environment in the upper left corner. Keep in mind that the log history expires after 3 days in the test environment and after 10 days in the production (prod) environment.

When you select an environment, the whole page refreshes and displays the corresponding data.

![](<../.gitbook/assets/ambiente seleção (1).png>)

## Search fields <a href="#h_f6b9a8f0a6" id="h_f6b9a8f0a6"></a>

You can filter pipeline logs using the following parameters:

* **Time period**: the time in which a pipeline was executed. Filter pipelines that were executed in the last 5, 15, or 60 minutes or select a specific time interval.
* **Log message:** the information sent by a component that returns logs during the pipeline execution. You must search for whole words when using this parameter.
* **Pipeline name:** the pipeline name as given by the user. You must search for whole words when using this parameter.
* [**Pipeline version**](https://docs.digibee.com/help-center/build/pipelines/pipelines-version-history)**.**
* **Pipeline execution key:** a unique identifier of each execution of a pipeline.
* **Sort by** (beta): a filter that allows you to sort the pipeline logs in ascending or descending order, according to the timestamp.
* **Log level:** the log message classification, according to the following criteria:
  * INFO: information about ordinary events during pipeline execution.
  * WARN: information about possible problems during pipeline execution.
  * ERROR: information about errors during pipeline execution.
  * ALL: any kind of information.

{% hint style="info" %}
**Command:** you can search using the CTRL+ENTER (Windows) or CMD+ENTER (Mac) command as an alternative to the Search button.
{% endhint %}

The logs are shown below according to the specified parameters. You can click the eye icon to see the log details in a modal or the copy icon to copy the log message.

![](<../.gitbook/assets/EN (3).png>)

## How to format messages with JSONs?&#x20;

Now it is possible to format log messages containing JSONs and copy the formatted content.&#x20;

To use this feature, follow these steps:

1. In Pipeline Logs, click the **“Eye”** icon, which will open Logs details.
2. Under Log messages, click the **“Wand”** icon to format any available JSON. In the same tab there is an icon to copy the content.

<figure><img src="../.gitbook/assets/Format JSON EN.gif" alt=""><figcaption></figcaption></figure>
