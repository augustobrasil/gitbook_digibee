---
description: >-
  Learn more about the possible causes of “Out of memory” errors in pipeline
  deployment and how to fix them based on the type of error.
---

# Solving the “Out of memory” errors in deployment

When deploying a pipeline, some of the most common errors that can occur include an out of memory. The causes of these out of memory errors vary according to the situation . This article is mainly about correctly identifying the error and fixing it.

## Identifying the “Out of memory” errors <a href="#h_f619e89a4e" id="h_f619e89a4e"></a>

The “Out of Memory” error occurs when the pipeline tries to consume more memory than it was allocated during deployment.

The first step to solving this problem is to find its cause by analyzing the pipeline logs of the failed execution. A memory overflow may have occurred in the pipeline by:

* making queries on a large amount of data without pagination in an HTTP request, a database, or when downloading and reading a file in memory;
* running too many concurrent executions;
* using the Session Management component to store data and not clearing it after reading.

{% hint style="info" %}
**Note:** Check the date of the last deployment. If it is older than the last version,execute a redeploy to update the pipeline
{% endhint %}

## Fixing the errors <a href="#h_3802136885" id="h_3802136885"></a>

Now that you know how to identify what could be causing the errors listed earlier, learn how to solve each problem with a specific action.

### Update the Pipeline Engine to the latest version <a href="#h_f3ecbbc83c" id="h_f3ecbbc83c"></a>

To upgrade the [Pipeline Engine](https://docs.digibee.com/documentation/platform/pipeline-engine) to a possible new version, the first thing you need to do is redeploy the pipeline. [For more information, refer to Redeploying a pipeline.](https://docs.digibee.com/documentation/run/redeploying-a-pipeline)

This could happen because the Digibee Integration Platform regularly updates its infrastructure. Part of this update is to recycle the machines that support the infrastructure. [Learn more about recycling pipelines in Warnings on pipeline in Run.](https://docs.digibee.com/documentation/run/how-warnings-work-on-pipelines-in-run)

### Large amount of data without pagination <a href="#h_2f9e219c84" id="h_2f9e219c84"></a>

Out of Memory errors can also be solved by pagination and/or an event-driven architecture. Pagination allows you to process data in chunks, rather than all at once. [For more information about pagination, refer to Paginations Example.](https://docs.digibee.com/help-center/tutorials-and-best-practices/paginations-example)

Implementing an event-driven architecture means using the main pipeline to retrieve data and create a loop that goes through that data and calls a second pipeline that has an [event trigger](https://docs.digibee.com/documentation/components/triggers/event-trigger#event-trigger-in-action).

This way, you split the memory load and create a scalable integration flow that works with both small and large data sets. [To learn more about event-driven architectures, see this article.](https://docs.digibee.com/documentation/tutorials-and-best-practices/event-oriented-architecture)

After the necessary adjustments to the pipeline, redeploy it again in the test environment.

### Running too many concurrent executions <a href="#h_ca3feda4fc" id="h_ca3feda4fc"></a>

Consumers share the available memory in the container. That is, the more consumers, the less memory is available for each. It is recommended to add new replicas to this pipeline to flow the process.

A SMALL pipeline with 2 replicas has twice the processing and scalability performance and so on. Not only do the replicas provide more processing and scaling power, but also guarantee higher availability - if one of the replicas fails, there are others to take over. [For more information on these concepts, refer to Pipeline Engine.](https://docs.digibee.com/documentation/platform/pipeline-engine#operation-architecture)

After making the necessary adjustments to the pipeline, redeploy it to the test environment. If the error persists, you should increase the Size of the pipeline deployment.

### Not clearing Session Management component <a href="#h_ffdff6e5bf" id="h_ffdff6e5bf"></a>

Clear the Session Management component to save the data after reading it. This is a good practice to reduce the risk of memory overload and out of memory occurs. To perform this action, you must configure the DELETE function in the component operations.

Thus, after the component sends the message as the final response, it is possible to clear the stored data after reading it with the Delete operation if this component is the last step of the pipeline. [To learn more about the Session Management component, see this article.](https://docs.digibee.com/documentation/components/structured-data/session-management)
