---
description: >-
  Discover more about the Do While component and how to use it on the Digibee
  Integration Platform.
---

# Do While

**Do While** allows the construction of blocks in loop inside a pipeline. It's part of a set of components that work with subpipelines to execute their functions.

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="295">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Iteration</strong></td><td>Defines the maximum number of times a loop is executed (it's possible to stop the loop before this number is reached).</td><td>10</td><td>Integer</td></tr><tr><td><strong>Timeout</strong></td><td>Maximum time the loop must execute.</td><td>300000</td><td>Integer</td></tr><tr><td><strong>Loop Index</strong></td><td>If the option is activated, a <code>“loopIndex”</code> property will be inserted in the presented message at each loop iteration and will inform the current iteration index (1, 2, 3, …).</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Interrupt Loop On Error</strong></td><td>If the option is activated, an error occurred inside an iteration will cause the loop interruption as a whole. Otherwise, the loop will continue from the next iteration.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Defining the subpipeline to be deployed at each iteration <a href="#defining-the-subpipeline-to-be-deployed-at-each-iteration" id="defining-the-subpipeline-to-be-deployed-at-each-iteration"></a>

To work with this type of component, it's important to keep in mind:

* **Subpipeline defined in the onProcess block:** the pipeline defined in this block is deployed at each loop iteration. Therefore, if the loop has 10 iterations, the subpipeline is executed 10 times.
* **Subpipeline defined in the onException block:** the pipeline defined in this block is deployed whenever a loop iteration results in error.

To define the subpipeline to be deployed at each iteration, just click on the **onProcess** icon of the **Do While** component:

<figure><img src="../../.gitbook/assets/Do While onprocess nov 23.png" alt=""><figcaption></figcaption></figure>

When clicking on this icon, a subpipeline will be created (or shown, if it already exists). Then all you have to do is build the desired flow according to the execution need of each iteration.

{% hint style="warning" %}
The input of this pipeline will be fed with the message that comes before **Do While**. This will happen in the #1 loop execution. For the other iterations, the presented message will be the final message of the previous iteration and so on. If **Loop Index** is activated, a `loopIndex` property will be inserted in the message informing the current iteration.
{% endhint %}

## Interrupting a loop <a href="#interrupting-a-loop" id="interrupting-a-loop"></a>

To interrupt a loop before the maximum number of defined iterations, just inform a `"loopBreak: true"` property in the end of the iteration. If the property is found, the loop will be broken.

A way to inform this property is by using the [**JSON Generator**](../tools/json-generator.md) component, which allows the definition of arbitrary JSONs in the pipeline flow.

## Handling errors in the loop <a href="#handling-errors-in-the-loop" id="handling-errors-in-the-loop"></a>

The standar behavior of **Do While** is to interrupt the loop if an error is found. Errors are atypical situations in the deployment of a pipeline that end up generating a stop. For example, the use of an Assert component causes an error in the pipeline when the assertion condition isn't met. Other error situations happen when components are used with the enabled **Fail On Error** configuration.

As previously explained, it's possible to define a subpipeline to handle errors. The definition of this subpipeline is made through the **onException** icon of the **Do While** component:

<figure><img src="../../.gitbook/assets/Do While onexception nov 23.png" alt=""><figcaption></figcaption></figure>

The input of this subpipeline will be fed with an error message, which will inform what happened to the iteration and the index of the iteration (`loopIndex`) that caused the failure.

```
{
    "timestamp": <error's timestamp>
    "error": <error message>
    "code": 500
    "loopIndex": <iteration index where the error occurred>
}
```

## Usage scenarios of the Do While component with errors handling <a href="#usage-scenarios-of-the-do-while-component-with-errors-handling" id="usage-scenarios-of-the-do-while-component-with-errors-handling"></a>

### "Interrupt loop on error" property enabled and no subpipeline defined in onException <a href="#interrupt-loop-on-error-property-enabled-and-no-subpipeline-defined-in-onexception" id="interrupt-loop-on-error-property-enabled-and-no-subpipeline-defined-in-onexception"></a>

* the subpipeline will be immediately interrupted;
* an error will be thrown from the **Do While** component;
* no other component will be invoked after **Do While**_._

### "Interrupt loop on error" property enabled and a subpipeline defined in onException <a href="#interrupt-loop-on-error-property-enabled-and-a-subpipeline-defined-in-onexception" id="interrupt-loop-on-error-property-enabled-and-a-subpipeline-defined-in-onexception"></a>

* the subpipeline will be immediately interrupted;
* the subpipeline defined in onException will be executed and its output will feed the component that follows **Do While**;
* the component that follows **Do While** will be invoked.

### "Interrupt loop on error" property disabled and no subpipeline defined in onException <a href="#interrupt-loop-on-error-property-disabled-and-no-subpipeline-defined-in-onexception" id="interrupt-loop-on-error-property-disabled-and-no-subpipeline-defined-in-onexception"></a>

* the iteration where the error occurred will be interrupted;
* a standard error message will be informed in the input of the following iteration and the loop will keep being normally executed.

### "Interrupt loop on error" property disabled and a subpipeline defined in _onException_ <a href="#interrupt-loop-on-error-property-disabled-and-a-subpipeline-defined-in-onexception" id="interrupt-loop-on-error-property-disabled-and-a-subpipeline-defined-in-onexception"></a>

* the iteration where the error occurred will be interrupted;
* the subpipeline defined in onException will be executed and its output will feed the following iteration;
* the loop will keep being normally executed.

## Error during the onException subpipeline <a href="#error-during-the-onexception-subpipeline" id="error-during-the-onexception-subpipeline"></a>

* the loop will be interrupted;
* the error will be thrown for the following component which the **Do While** component is associated to;
* if **Do While** is in the pipeline main flow, then the pipeline will be interrupted;
* if **Do While** is inside a component that has a subpipeline, then the onException subpipeline will be invoked and the error will be informed in this pipeline input.\
