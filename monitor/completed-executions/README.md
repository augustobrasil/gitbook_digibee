---
description: Track and monitor deployed integration pipelines' metrics.
---

# Completed executions

A completed execution is the end-to-end execution of a pipeline, that is, the record of what happened inside it, from the moment the input passed through the trigger until it ran through the last component in the pipeline conveyor.

In the completed executions tab, you can keep track of pipeline executions and their log histories, as well as re-execute them.

## **Environment selector**

You can select the desired environment in the upper left corner. When you select an environment, the whole page refreshes to show the data related to the pipelines in that environment.

![](<../../.gitbook/assets/ambiente seleção.png>)

## **Search fields**

You can filter pipeline executions using the following parameters:

* **Time Period**: you can filter pipelines executed in the last 5, 15 or 60 minutes, as well as select a specific time interval
* **Message type:** the execution status of the pipeline
  * **Response**: executions completed without any interruption&#x20;
  * **Error**: interrupted executions
  * **All**: any execution
* **Pipeline name:** the pipeline's full name&#x20;
* **Pipeline version** (major or minor)&#x20;
* **Pipeline execution key:** a unique identifier of each execution of a pipeline
* **Payload:** the pipeline input or output in JSON format. This search field uses Elasticsearch’s [simple query string syntax](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-simple-query-string-query.html#simple-query-string-syntax)
* **Source:** the [pipeline trigger](https://docs.digibee.com/help-center/components/triggers)
* **Error code:** a pipeline execution error code, according to the [HTTP Status Code](https://en.wikipedia.org/wiki/List\_of\_HTTP\_status\_codes) pattern.

{% hint style="info" %}
**Command:** you can search using the CTRL+ENTER (Windows) or CMD+ENTER (Mac) command as an alternative to the Search button.
{% endhint %}

The completed executions are shown below according to the specified parameters:

<figure><img src="../../.gitbook/assets/Pipeline execution key in Completed executions EN.png" alt=""><figcaption><p>Completed executions table</p></figcaption></figure>

You can click the magnifying glass icon to open the [execution details](./#execution-details) sidesheet or the refresh icon to re-execute the pipeline.&#x20;

In order to re-execute a pipeline manually, its trigger must have the “Allow Redelivery of Messages” option activated. It’s important to note that you should only manually re-execute a pipeline when troubleshooting, not as part of your integration process.

## Execution details

If you click on the magnifying glass icon in the completed executions table, a sidesheet will appear showing the execution details.

<figure><img src="../../.gitbook/assets/Completed executions 2 EN.png" alt=""><figcaption><p>The execution details sidesheet </p></figcaption></figure>

In the execution details' sidesheet, you can see the:

* **Pipeline key:** a unique identifier of a pipeline execution&#x20;
* **Request message:** the JSON data sent by the pipeline trigger
* **Response message:** the pipeline’s JSON output
* [Execution logs](https://docs.digibee.com/help-center/monitor/pipeline-logs)&#x20;

You can also click the button in the upper right corner to access on Canvas the pipeline execution you are analyzing.&#x20;

<figure><img src="../../.gitbook/assets/open pipeline EN.png" alt=""><figcaption></figcaption></figure>

The “[message](https://docs.digibee.com/help-center/build/pipelines/messages-processing)” is the data that is transmitted in JSON format through the pipeline. Each component of the pipeline receives, manipulates, and exports a message. Only the first 50 pipeline messages are shown, and only for pipelines executed in the Execution panel.

In some cases, the Platform presents truncated payloads, according to the following criteria:

|      Payload Size      |              Exhibition             |
| :--------------------: | :---------------------------------: |
|    Smaller than 32kb   |           Full exhibition           |
| Between 32kb and 320kb |          Partial exhibition         |
|    Larger than 320kb   | Warning @@DGB\_TRUNCATED@@ is shown |
