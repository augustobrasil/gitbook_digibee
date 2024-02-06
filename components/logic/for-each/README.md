---
description: >-
  Discover more about the For Each component and how to use it on the Digibee
  Integration Platform.
---

# For Each

**For Each** makes a loop inside a JSON structure, processing each element of the array in a subpipeline.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="267">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>JSON Path Expression</strong></td><td><p>Expression applied to the JSON structure received by <strong>For Each</strong>, filtering it. <strong>For Each</strong> can receive an object that has multiple elements, and the JSON Path expression allows the reception only of those that meet a specific condition.</p><p></p><p>To improve the use of the <strong>For Each</strong> component, we recommend that the expressions used in the <strong>JSON Path Expression</strong> parameter be validated using the following reference: <a href="https://jsonpath.com/">https://jsonpath.com/</a>.</p></td><td>$</td><td>String</td></tr><tr><td><strong>Element Identifier</strong></td><td>Unique element that identifies the line under processing (for example, "id" element).</td><td>N/A</td><td>String</td></tr><tr><td><strong>Parallel Execution</strong></td><td>When enabled, the option makes the elements of the array received by <strong>For Each</strong> to be processed in parallel, with a limit of up to 10 concurrent executions. That means if the array received by the component has 20 elements, the first 10 will have the processing started right away. As soon as one of these processings ends, the next element of the array will be processed, and so on, until the whole array is processed. If the <strong>Parallel Execution</strong> option is disabled, the elements of the array received by <strong>For Each</strong> will be processed in series. The first one must be processed for the processing of the second one to start.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fail On Error</strong></td><td>When activated, this parameter suspends the pipeline execution only if there’s a severe occurrence in the iteration structure, disabling its complete conclusion. The <strong>Fail On Error</strong> parameter activation doesn’t have any connection with the errors occurred in the components used for the construction of the subpipelines (onProcess and onException). If you want the execution to be interrupted for any type of occurrence, consider using <strong>Do While</strong>. <a href="https://docs.digibee.com/documentation/components/logic/do-while">Click here to read about this component and check if it applies to your scenario.</a></td><td>False</td><td>Boolean</td></tr></tbody></table>

## **JSON Path Expression Examples**

```
$.[?(@.status == 'EXPIRED')]
```

The expression above shows how the message received by the component can be filtered: in this example, the array is the root of the object and only the elements whose status attribute is EXPIRED will be processed by **For Each**.

```
$.body.*
```

Obtains all the received message body content.

```
$.body.products.*
```

Obtains the content of an _array_ products that's inside the received message body.

## Defining the subpipeline to be executed at each iteration <a href="#defining-the-subpipeline-to-be-executed-at-each-iteration" id="defining-the-subpipeline-to-be-executed-at-each-iteration"></a>

To define the subpipeline to be executed at each iteration, just click on the **onProcess** icon of **For Each**.



<figure><img src="../../../.gitbook/assets/for each onprocess nov 23.png" alt=""><figcaption></figcaption></figure>

When clicking on this icon, a subpipeline will be created (or shown, if it already exists). Then build the desired flow according to the execution need of each iteration.

{% hint style="info" %}
if [**Session** **Management**](../../structured-data/session-management.md) components are used to manipulate the data of each array element in the **For Each** subpipeline and the **Parallel Execution** option is enabled, it's necessary for the **Scoped** option from **Session Management** to be enabled so that each concurrent execution accesses its respective data.
{% endhint %}

## Handling errors in loop <a href="#handling-errors-in-loop" id="handling-errors-in-loop"></a>

The standard behavior of **For Each** is to interrupt the execution if some error is found. Errors are atypical situations in the execution of a pipeline that result in a stop. For example, the use of an [**Assert** **V2**](../../tools/assert-v2.md) component causes an error in the pipeline when the assertion condition isn't met. Other error situations occur when components are used with the **Fail On Error** configuration enabled.

As previously explained, it's possible to define a subpipeline to handle errors. The definition of this subpipeline is made through the **onException** icon of **For Each**:



<figure><img src="../../../.gitbook/assets/for each onexception nov 23.png" alt=""><figcaption></figcaption></figure>

[Read the subpipelines article to better understand how it works.](https://docs.digibee.com/documentation/build/pipelines/subpipelines)

{% hint style="warning" %}
It is not possible to interrupt the entire **For Each** loop. The interruption can only be done at the current iteration via components where the **Fail On Error** parameter is enabled in the onProcess and onException subpipelines.
{% endhint %}

## Serious structural error during the onException subpipeline <a href="#error-during-the-onexception-subpipeline" id="error-during-the-onexception-subpipeline"></a>

* the loop will be interrupted;
* the error will be thrown to the next component to which **For Each** is associated;
* if **For Each** is in the main pipeline flow, then the pipeline will be interrupted;
* if **For Each** is inside a pipeline that has a subpipeline, then the onException subpipeline will be informed in this pipeline input.

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

**For Each** accepts any JSON structure that has an array. If the array isn't the root of the object, then a JSON Path expression must be defined to locate and filter the array. If **For Each** doesn't receive any array, no processing will be executed.

### Output <a href="#output" id="output"></a>

```
{
    "total": 0,
    "success": 0,
    "failed": 0
}
```

* **total:** total number of processed elements.
* **success:** total number of successfully processed elements.
* **failed:** total number of elements that couldn't be processed.

{% hint style="info" %}
To inform that a line has been correctly processed and iterate the value of the `"success"` field, each execution of the onProcess subpipeline must respond with `{ "success": true }` by the end. That's the only way for the output message to correctly represent the result of the processings.
{% endhint %}
