---
description: >-
  Discover more about the Retry component and how to use it on the Digibee
  Integration Platform.
---

# Retry

**Retry** allows new retries of steps defined in a subpipeline to be executed.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="301">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Maximum Number of Retries</strong></td><td>The first retry also counts, so if the step fails in the first execution and you want a new retry to be made, the value of this parameter should be 2.</td><td>3</td><td>Integer</td></tr><tr><td><strong>Timeout Of The Whole Retry Operation</strong></td><td>Maximum length of the sum of all retry attempts, including the first one (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the Retry execution that reaches the maximum number of tries or the maximum length will end with an error and will be interrupted; otherwise, the pipeline execution continues, but the result of the last try will be delivered to the next component.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Defining the subpipeline to be executed on each new retry <a href="#h_f35aa906d6" id="h_f35aa906d6"></a>

To work with this type of component, it's important to consider:

* **Subpipeline defined in onProcess:** subpipeline to be executed on each new retry.
* **Subpipeline defined in onException:** subpipeline to be executed after an unsuccessful retry.

To better understand how subpipelines work, [read the Subpipelines documentation](../../build/pipelines/subpipelines.md).

{% hint style="warning" %}
On each new retry, the first step on the subpipeline defined in onProcess receives the output message from the last processed step. Therefore, data to be reused on new retries must be correctly handled to be accessible during the new retries (that is, the data manipulation through the Session component).
{% endhint %}

### Informing success to a Retry block execution <a href="#h_36ddd4e0d5" id="h_36ddd4e0d5"></a>

The **Retry** component expects a "success" property with the "true" value to be informed in the last step of the subpipeline for the execution to be considered successful. If an error occurs or the “success” property is informed with a "false" value or doesn’t even exist, **Retry** will understand that a new retry must be executed.

## Messages flow <a href="#h_6b4f740e2e" id="h_6b4f740e2e"></a>

### Input <a href="#h_ab3c90c301" id="h_ab3c90c301"></a>

Any structure is accepted.

### Output <a href="#h_61b077be56" id="h_61b077be56"></a>

The output message of the last processed step.

## Handling Errors <a href="#h_6ab171494f" id="h_6ab171494f"></a>

When an error occurs during the processing of the subpipeline in onProcess, the subpipeline defined in onException will be invoked, if it's defined.

In onException, it's possible to:

* have access to the details of the error that occurred during the processing of the last retry.
* define if the **Retry** component continues with the retries, informing a “success” property with the "false" value. If a “success” property is specified with the "true" value, then **Retry** will be successfully finished and no other retry will be executed.

## Usage scenarios of the Retry component with errors handling <a href="#h_80a4cf14f3" id="h_80a4cf14f3"></a>

### Enabled Fail on Error property and no subpipeline defined in onException <a href="#h_9326e217ba" id="h_9326e217ba"></a>

* the pipeline will be interrupted after all the retries;
* an error will be thrown from the **Retry** component;
* no other component will be invoked after the **Retry**_._

### Enabled Fail on Error property and a subpipeline defined in onException <a href="#h_856f7dcd14" id="h_856f7dcd14"></a>

* the pipeline will be interrupted after all the retries;
* the _subpipeline_ defined in _onException_ will be executed after every new retry;
* an error will be thrown from the **Retry** component;
* no other component will be invoked after the **Retry**_._

### Disabled Fail on Error property and no subpipeline defined in onException <a href="#h_44a1561e6a" id="h_44a1561e6a"></a>

* the pipeline will not be interrupted after all the retries;
* no error will be thrown from the **Retry** component;
* the next component will be invoked receiving the output message from the **Retry**.

### Disabled Fail on Error property and a subpipeline defined in onException <a href="#h_ad50cd6968" id="h_ad50cd6968"></a>

* the pipeline will not be interrupted after all the retries;
* the _subpipeline_ defined in _onException_ will be executed after every new retry;
* no error will be thrown from the **Retry** component;
* the next component will be invoked receiving the output message from the **Retry**.

{% hint style="warning" %}
If an error component (such as Throw Error or Assert_)_ is used on the subpipeline in onProcess or if an error occurs, then Retry will be finished and the error will be propagated to the pipeline. Besides, whenever the "success" property is defined with the "true" value on the last step of the subpipeline in onException, the Retry execution will be finished, even if the Fail on Error property is activated.
{% endhint %}
