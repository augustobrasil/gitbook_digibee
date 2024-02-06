---
description: >-
  Discover more about the Block Execution component and how to use it on the
  Digibee Integration Platform.
---

# Block Execution

**Block Execution** declares a part of a pipeline for a specific purpose. It can be used to:

* logically separate parts of an extense pipeline in a way its behavior becomes easier to understand;
* allow the different created flow deviation paths to get together in the end of the declared piece (more details ahead);
* declare a pipeline piece for specific errors handling.

## Parameters

**Block Execution** doesn't have any specific configuration to function. All it takes is for you to build the onProcess and onException subpipelines.&#x20;

## Subpipelines

**Block Execution** is part of a set of components that work with subpipelines to execute their functions. For more information, [read the Subpipelines documentation](../../build/pipelines/subpipelines.md). &#x20;

To work with this type of component, you must consider 2 important concepts:

* **Subpipeline defined in the onProcess block:** the pipeline defined in this block is the execution piece of the component.
* **Subpipeline defined in the onException block:** the pipeline defined in this block is executed whenever there's a failure in the onProcess block. See more details below.

## Defining the executed subpipeline as part of the block <a href="#defining-the-executed-subpipeline-as-part-of-the-block" id="defining-the-executed-subpipeline-as-part-of-the-block"></a>

To define the subpipeline to be executed, just click on the **onProcess** icon of the component:



<figure><img src="../../.gitbook/assets/block exec example nov 23.png" alt=""><figcaption><p>The onProcess icon is highlighted above the component</p></figcaption></figure>

When clicking on this icon, a subpipeline will be created (or shown, if it already exists). Then all you have to do is to build the desired flow as the execution need demands.

{% hint style="info" %}
This pipeline input will be fed with the message that comes before **Block Execution**.
{% endhint %}

## Using Block Execution to bring together different paths of a flow deviation component <a href="#using-block-execution-to-bring-together-different-paths-of-a-flow-deviation-component" id="using-block-execution-to-bring-together-different-paths-of-a-flow-deviation-component"></a>

When a flow deviation component is used, such as [**Choice**](choice.md), multiple paths are created in the pipeline to attend the desired flow deviation. For example:



<figure><img src="../../.gitbook/assets/block exec ex2 nov 23.png" alt=""><figcaption><p>Example of pipeline using multiple paths </p></figcaption></figure>

For the case above, you can see 2 flow deviations: **path 1** and **path 2**, which take to completely different paths in the pipeline. Let's say it's necessary to bring these paths together to move on with the pipeline deployment. The **Block Execution** component has the function to group different paths in a separate execution block. When one of the paths is done, the control goes back to **Block Execution**, that is followed by the next component. Check it out:



<figure><img src="../../.gitbook/assets/block exec ex3 nov 23.png" alt=""><figcaption><p>Example of Block Execution being used to group different paths</p></figcaption></figure>



For the other example above, **Block Execution** is followed by [**JSON Generator**](../tools/json-generator.md). Inside the onProcess subpipeline of **Block Execution**, A **Choice** component with deviations was used.

When deviations come to the end, they close **Block Execution**, which returns to the main pipeline and executes the following component - in this case, **JSON Generator**.

That way, it's possible to bring together and organize subpipelines that have flows with ramifications.

## Handling errors <a href="#handling-errors" id="handling-errors"></a>

As all the other components that have the onProcess and onException subpipelines, **Block Execution** also handles errors by executing the onException pipeline.

An error can be caused by other components when they identify adverse situations. Generally, the components have a configuration property named **Fail On Error**, which controls if you want to generate an error that might be handled in onException flows.

So, when a component "throws" an error and has the **Fail On Error** property activated, **Block Execution** intercepts the errors and sends its for handling in the onException subpipeline.

These are the special situations you must keep in mind:

* if an onException flow isn't defined, **Block Execution** simply moves the error forward for another component with execution by pipeline to handle it. On the other hand, if the main flow of the pipeline is used, then the pipeline is finished with the error;
* if a new error occurs during the onException subpipeline, **Block Execution** also moves the error forward for another component with execution by pipeline to handle it. But if the main flow of the pipeline is used, the pipeline is equally finished with the error.
