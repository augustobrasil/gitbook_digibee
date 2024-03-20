---
description: Learn more about how to deploy a multi-instance pipeline.
---

# Deploying a multi-instance pipeline

## **How to deploy a multi-instance pipeline**_**?**_ <a href="#h_4d29138653" id="h_4d29138653"></a>

### 1. Create the multi-instance model <a href="#h_c5a383bb41" id="h_c5a383bb41"></a>

Before you create the instances, you need to create a multi-instance model. To do this, go to the **Multi-Instance** page, click **Create**, and define a name, description, and the fields of the instances, that is, the variables that should receive values in each environment.

Take a look at the following example:

![](../../.gitbook/assets/1.create-multi-instance.png)

Once this is done, click **Confirm** to create the model.

### 2. Configure the instances <a href="#h_0333a40f3d" id="h_0333a40f3d"></a>

Now, you can create the instances that will match the model you created in the last step. To do this, find the model in the list and click on the corresponding **Configure** action button. This way you can create the instances of this model one by one, entering and setting values for each field.

In the following example, "instance1" and "instance2" are two stores that receive the values of each variable that can be configured for both test and prod. This is repeated for all other instances to be created.

![](../../.gitbook/assets/2.\[new]configure-instances.gif)

After entering the variables, just click **Save**.

### 3. Create a multi-instance pipeline <a href="#h_09aa37808b" id="h_09aa37808b"></a>

In this step, we create a pipeline and define it as a multi-instance. To do this, access the settings by clicking on the **Settings** button and activate the **Is it a multi-instance?** option:

<figure><img src="../../.gitbook/assets/3.multi-instance-pipeline.gif" alt=""><figcaption></figcaption></figure>

After selecting the **Is it multi-instance?** option, specify which multi-instance model the pipeline will report to. In our example, we are using the "multi-instance-model".

{% hint style="info" %}
Once the pipeline is set to multi-instance, it is not possible to undo this setting. On the other hand, it is possible to convert any pipeline, whether already deployed or not, to a multi-instance pipeline.
{% endhint %}

Since this is an event, we need to inform the trigger an instance variable that will be executed using the pattern **`-{{replica.instance_variable_name}}.`**, as in the example below:

<figure><img src="../../.gitbook/assets/4.event-trigger.png" alt=""><figcaption></figcaption></figure>

#### Running queries in Execution panel <a href="#h_689a26cf02" id="h_689a26cf02"></a>

If you are running an execution in a multi-instance pipeline, you can select the instance you want to run in the **Test** tab, as in the following example:

<figure><img src="../../.gitbook/assets/5.multi-instance-execution-panel.gif" alt=""><figcaption></figcaption></figure>

In this way, it is possible to consult the values previously configured in the selected instance via the pattern **`{{replica.instance_variable_name}}`**.

### 4. Deploying a multi-instance pipeline <a href="#h_bb732a39e5" id="h_bb732a39e5"></a>

Now that you have configured the template and set the pipeline to multi-instance, you need to edit the pipeline request with the instance on which you want to deploy it. This way, the instance name will be added to the pipeline name after deployment.&#x20;

**For example**: once the "multi-instance-pipeline" is deployed on "instance1", its name on the **Run** pipeline card will be "multi-instance-pipeline-instance1".

In the following example, the "multi-instance-pipeline" is deployed on "instance1" and "instance2".

![](../../.gitbook/assets/6.deploy-pipeline.gif)

After editing, simply click **Deploy**.

Below is the “multi-instance-pipeline” already deployed on "instance1" and "instance2" instances in the **Run** phase shown in the pipeline card:

<figure><img src="../../.gitbook/assets/7.deployed-pipelines (1).png" alt=""><figcaption></figcaption></figure>
