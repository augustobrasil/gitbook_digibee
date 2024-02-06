---
description: >-
  Discover more about the Pipeline Executor component and how to use it on the
  Digibee Integration Platform.
---

# Pipeline Executor

**Pipeline Executor** makes synchronous or asynchronous calls to other pipelines that have already been deployed. When using the synchronous approach, you can obtain the result of the called pipeline.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="294">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>SYNC for synchronous calls to the pipeline and ASYNC for asynchronous calls to the pipeline.</td><td>SYNC</td><td>String</td></tr><tr><td><strong>Pipeline Name</strong></td><td>Name of the pipeline to be called.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Version Major</strong></td><td>Major version of the pipeline to be called.</td><td>1</td><td>Integer</td></tr><tr><td><strong>Payload</strong></td><td>Payload to be sent when the pipeline is called.</td><td>N/A</td><td>Any</td></tr><tr><td><strong>Timeout</strong></td><td>Maximum time of the pipeline execution (in milliseconds).</td><td>20000</td><td>Integer</td></tr><tr><td><strong>Expiration</strong></td><td>Time that the message remains in the queue when trying to execute the pipeline (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow

### Input

No specific payload is expected in this component input. The input will be dynamically configured in the **Payload** field according to the need of the pipeline to be called.

#### Output

```
{
   "operation": "SYNC",
   "pipelineName": "pipeline-example",
   "versionMajor": 1,
   "success": true,
   "payload": {},
   "pipelineResponse": {}
}

```

* **operation:** the selected operation, SYNC or ASYNC.
* **pipelineName:** name of the called pipeline.
* **versionMajor:** major version of the called pipeline.
* **success:** if the call was successful.
* **payload:** payload used to call the configured pipeline.
* **pipelineResponse:** response of the executed pipeline. This property is returned only in the SYNC operation.

## Pipeline Executor in action

See below how the component behaves in certain situations and how it is configured in each case.

### Making an asynchronous call

**Operation:** ASYNC

**Pipeline Name:** name of the pipeline to be called

**Version Major:** 1

**Payload:** {}

**Timeout:** 20000

**Expiration:** 30000

**Fail On Error:** false

In the scenario above, an asynchronous call to the configured pipeline will be made and the current flow will continue normally without waiting for the called pipeline response. You will be able to see the execution and the call logs of this pipeline in the Platform logs screen.

**Output**

```
{
   "operation": "ASYNC",
   "pipelineName": "name of the pipeline to be called",
   "versionMajor": 1,
   "success": true,
   "payload": {}
}
```

### Making a synchronous call

**Operation:** SYNC

**Pipeline Name:** name of the pipeline to be called

**Version Major:** 1

**Payload:** {}

**Timeout:** 20000

**Expiration:** 30000

**Fail On Error:** false

**Output**

```
{
   "operation": "SYNC",
   "pipelineName": "name of the pipeline to be called",
   "versionMajor": 1,
   "success": true,
   "payload": {},
   "pipelineResponse": {}
}
```

When deploying pipelines with **Pipeline Executor**, pay attention to concurrent execution configurations in the origin and destination pipelines, especially when the **Operation** parameter is in SYNC.

{% hint style="info" %}
To avoid enqueue and timeout errors in the destination pipeline, it is recommended that the same concurrent execution configuration be applied on both pipelines.
{% endhint %}

#### Red flag examples

pipeline1(Medium) <-> pipeline2(Small)\
pipeline1(Large) <-> pipeline2(Medium)\
pipeline1(Large) <-> pipeline2(Small)

#### Maximum Concurrent Executions by deploy type

Small - max 10\
Medium - max 20\
Large - max 40\
