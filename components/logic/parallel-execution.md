---
description: >-
  Discover more about the Parallel Execution component and how to use it on the
  Digibee Integration Platform.
---

# Parallel Execution

**Parallel Execution** allows the configuration of parallel execution lines inside the pipeline flow.

## Parameters

The component has 2 configuration steps: one for the parameters that define the executions general behavior and another one for the specific parameters of the execution lines.

### Component

Take a look at the configuration parameters of the component:

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="284">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Aggregation Type</strong></td><td>It can be configured as SUMMARY or COLLATE; see more details below.</td><td>COLLATE</td><td>String</td></tr><tr><td><strong>Show Execution Ids</strong></td><td>If enabled, the property will make sure that the ID of each execution line is informed in the result.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Report Exceptions</strong></td><td>If enabled, the property will make sure that any exceptions are informed in the result; see more details below.</td><td>True</td><td>Boolean</td></tr></tbody></table>

### Execution lines

Now take a look at the configuration parameters of the execution lines:

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="284">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Description</strong></td><td>Property that can be used to document the execution lines, because it turns into the component presented text in the pipeline canvas.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Execution ID</strong></td><td>Defines the ID of each parallel execution.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

No specific payload is expected in this component input. However, the input will be informed at each parallel execution line.

### Output <a href="#h_60dd0b12fe" id="h_60dd0b12fe"></a>

* **Output with Aggregation Type = SUMMARY**

In this case, only one summary about each parallel invocation will be displayed:

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

A summary will be informed at the end of the execution of all the parallel lines. For an execution line to be considered as `"success"`, a `"success"` property with the `“true”` value must be informed at the end of the execution.

* **Output with Aggregation Type = COLLATE and Show Execution ID = true**

In this case, the result of each execution will be available as an array item identified with the `executionId` property, which defines the path run by that execution and `“result”` containing its result.

```
[{
    "executionId": "p-a",
    "result": {
        "parallel": "A"
    }
}, {
    "executionId": "p-b",
    "result": {
        "parallel": "B"
    }
}, {
    "executionId": "p-c",
    "result": {
        "parallel": "C"
    }
}]
```

* **Output with Aggregation Type = COLLATE and Show Execution ID = false**

In this case, the result of each execution will be informed as an array item without specifying which path was run.

```
[{
         "parallel": "A"
}, {
        "parallel": "B"
}, {
        "parallel": "C"
}]
```

* **Output with error and Report Exceptions = true**

This case is relevant only when used with **Aggregation Type** **= COLLATE**.

If an error occurs during the execution of the p-b parallel line, the error will be informed in the output:

```
[{
    "executionId": "p-a",
    "result": {
        "parallel": "A"
    }
}, {
    "executionId": "p-b",
    "result": {
        "timestamp": 99999, "error": "XXXX", "code": 999
    }
}, {
    "executionId": "p-c",
    "result": {
        "parallel": "C"
    }
}]
```

* **Output with error and Report Exceptions = false**

This case is relevant only when used with **Aggregation Type = COLLATE**.

If an error occurs during the execution of the p-b parallel line, `null` will be informed as result:

```
[{]
    "executionId": "p-a",
    "result": {
        "parallel": "A"
    }
}, {
    "executionId": "p-b",
    "result": null
}, {
    "executionId": "p-c",
    "result": {
        "parallel": "C"
    }
}] 
```

## Parallel Execution in action <a href="#parallel-execution-in-action" id="parallel-execution-in-action"></a>

See below how the component behaves in specific situations and what its respective configurations are.

### **Putting the result of the parallel execution together**

To put the result of the parallel executions together, it's important to configure the **Parallel Execution** component inside a [**Block Execution**](block-execution.md). By the end of **Block Execution**, all the parallel executions will be synchronized and the result will be shown.

<figure><img src="../../.gitbook/assets/parallel exec example onprocess nov 23.png" alt=""><figcaption><p>Example of Parallel Execution configured inside a Block Execution (onProcess)</p></figcaption></figure>

### **Parallel Execution used in the main flow of the pipeline**

If the component is used in the main flow of the pipeline, then the parallel execution lines will be "put together" by the end of the execution and the pipeline will be finished with the output result.

<figure><img src="../../.gitbook/assets/parallel exec example root nov 23.png" alt=""><figcaption><p>Example of Parallel Execution configured in the pipeline's main flow</p></figcaption></figure>

### **Parallel Execution used inside another Parallel Execution**

In this case, new parallel execution lines will be started and "put together" by the end of the parallel execution line that had the inner **Parallel Execution**. The more-external **Parallel Execution** will put its respective lines together only when the inner ones are finished.

<figure><img src="../../.gitbook/assets/parallel exec example branch nov 23.png" alt=""><figcaption><p>Example of the joint use of two Parallel Execution components</p></figcaption></figure>
