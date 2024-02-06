---
description: Understand the importance and impacts of the Pipeline Engine upgrade.
---

# Digibee Integration Platform Pipeline Engine v2

The Digibee Integration Platform [Pipeline Engine](https://docs.digibee.com/documentation/platform/pipeline-engine) is responsible for interpreting and executing pipelines created through the interface. The main goal of the updated version (Engine v2) is to evolve code and technology, fix vulnerabilities and improve the performance of the Platform.

## Benefits of the upgrade&#x20;

The Pipeline Engine update has many advantages for customers and Digibees such as:

* More stability for the Platform
* Evolution of the Platform architecture
* Cleaner and more powerful codes
* Easier development of new features
* Faster startup
* Performance gain

The Pipeline Engine v2 also presents significant improvements in container initialization and pipeline execution compared to the previous version:

**Container initialization**

|            | **Current Engine** | **Engine v2** | **Improvement %** |
| ---------- | ------------------ | ------------- | ----------------- |
| **Time**   | 3980ms             | 2674 ms       | 32,83%            |
| **CPU**    | 0.0409326          | 0.0301709     | 26,29%            |
| **Memory** | 257.51MB           | 246.445MB     | 4,3%              |

**Pipeline execution**

|            | **Current Engine** | **Engine v2** | **Improvement %** |
| ---------- | ------------------ | ------------- | ----------------- |
| **Time**   | 253 ms             | 171 ms        | 32,37%            |
| **CPU**    | 0.0063913          | 0.0034888     | 45,41%            |
| **Memory** | 3.044MB            | 0.905MB       | 70,27%            |

_\*The values ​​obtained are the result of the average of 10 repetitions. Data may vary based on customer pipelines._

### Numeric precision enhancement on Engine v2 (Restricted Beta)

In addition to the benefits mentioned above, the Beta version of the Pipeline Engine V2 also presents improvements in handling and use of floating points numbers.&#x20;

The Numeric precision enhancement feature mitigates rounding issues for fractional numbers and ensures that any decimal floating point numbers transmitted in a component's pipeline can be represented more accurately, making query results more precise.

Currently, numbers with a large number of decimal places such as 1250259129.48955334546546 end up being rounded through scientific notation and lose precision. With this improvement, all numbers will now be displayed with the original decimal places.

This enhancement is present in the Engine v2 implementation for both new realms and existing realms, the latter being activated through the Feature Flag mechanism. Customers who already have Engine v2 and want to activate this feature must contact Digibee's support team.

{% hint style="info" %}
Double Braces Math Functions such as DIVIDE, SUM, ABS, and others, are not included in this improvement, since it’s still in Beta phase. However, they are under development and should be covered soon.
{% endhint %}

### Support Dynamic Accounts (Restricted Beta)

[Support Dynamic Accounts](https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta) is a new functionality exclusive to Pipeline Engine v2. This improvement allows customers who use multipurpose pipelines on the Digibee Integration Platform to change their credentials configurations on the Run time screen, through the new [Store Account ](https://docs.digibee.com/documentation/components/tools/store-account)component. **The Store Account** component, only available on Pipeline Engine v2, dynamically stores accounts data locally.

This improvement allows greater flexibility, as credentials can be easily modified as needed and seamlessly integrated into the development pipeline without requiring a new registration in the Account section of the Platform.

That way, developers can efficiently manage and update credentials without unnecessary complexities, ensuring a smooth and streamlined development process. The Dynamic Accounts update is available in the following Digibee Integration Platform components:

* [SAP](https://docs.digibee.com/documentation/components/untitled/sap)
* [SFTP](https://docs.digibee.com/documentation/components/file-storage/sftp)
* [FTP](https://docs.digibee.com/documentation/components/file-storage/ftp)
* [REST v2](https://docs.digibee.com/documentation/components/web-protocols/rest-v2)
* [SOAP v3](https://docs.digibee.com/documentation/components/web-protocols/soap-v3-beta)
* [DB v2](https://docs.digibee.com/documentation/components/structured-data/db-v2)
* [Kafka](https://docs.digibee.com/documentation/components/queues-and-messaging/kafka)

The new configuration parameters are available in the documentation of each of their respective components.

{% hint style="warning" %}
The use of the Store Account component in parallel scenarios, such as parallel execution or For Each (where you override the dynamically configured account), is **not recommended** on the Restricted Beta Phase.
{% endhint %}

### Reduce pipeline first execution time - Pipeline Time to First Byte (Restricted Beta)&#x20;

This improvement reduces the time for the first pipeline execution by about 50%. For example, if the request would take 6.5 seconds, it now takes only 2.3 seconds (estimative). \
\
This optimization was made possible by an update to [Double Braces ](https://docs.digibee.com/documentation/build/double-braces)― a Digibee expression language that uses Java reflection ―to load the application classes during the pipeline startup, when the deployment happens.

## **Phases of the implementation**

### Alpha Phase

The first phase of Engine implementation starts in the Digibee Integration Platform Staging environment. This environment was chosen because it does not receive access from clients and problems related to updates occur in a controlled environment.

**In this phase, the Core Platform team performs tests and collects metrics**, trying to scale up the implementation and using complex pipelines to test possible worst-case scenarios. This phase was successfully executed.

In the second part of the Alpha Phase, the implementation was executed in Training and Enablement Environments. The goal is to monitor the container logs for exception validation and pipe execution, fix bugs and detect Common Vulnerabilities and Exposures (CVEs).\
\
The Core Platform team, in collaboration with the Education team, conducted Engine v2 testing in the Digibee Integration Platform during training sessions on January 9 and 23. During the training, the connectors behaved as expected and the Engine v2 remains active in these environments.

### Restricted Beta Phase

This phase begins with the analysis and selection of customers by the customer success managers (CSM) with the orientations of the Core Platform team (learn more about the chosen criteria in System requirements section below). The Beta Restricted Phase is divided in two parts:

* **PART 1 - Implementation of the Engine v2 in new realms of new and established customers:**  In the Part 1 new realms are being created with Engine v2 only, with the situation closely monitored by functional analysts and other Digibee teams. The implementation was executed on a customer’s new realm in cluster US and worked correctly in a POC performed by Digibee.
* **PART 2 - Implementation of the Engine v2 in existing realms of established customers:** This part runs parallel to the part 1, just for selected customers. The upgrade is performed in the test and production environments of existing realms. The update runs a beta version of the Engine v2 with dedicated support from the Product team.

The Restricted Beta phase goes through the following steps before it becomes Beta and thus General Availability (G.A.):

1. **Beta Phase - Invitation to customers to use Engine V2**
2. **G.A. Phase - Mandatory transition to Engine v2**

{% hint style="danger" %}
After the final date established for mandatory transition, Digibee will no longer provide support for pipelines associated with the previous version of the Engine.
{% endhint %}

## **System requirements**

Customers selected in the **Restricted Beta phase** will be the first to receive Engine v2 implementations. They are selected based on connector types, pipeline complexity, their maturity in using the Platform, and their relationship with Digibee.

This combination of criteria is critical for the Product team to make the implementations run as smoothly as possible while gathering metrics that will help with future implementations.

## **Implementation process**

* **Implementation of the engine v2 in new realms:** Engine v2 will be implemented in new realms by functional analysts in collaboration with the Pre-sales and Customer Success teams. It is done in POCs with close monitoring by Digibee (especially for customers that do not have an autonomous approach). In these cases, no action is required from customers. Engine V2 is already installed on their new realms.&#x20;
* **Implementation of the engine v2 in existing realms of established customers:** For the implementation of Pipeline Engine v2 in existing realms, the production pipelines will be replicated in the test environment. When the test environment is successfully updated, Engine v2 is deployed to the production environment.&#x20;
  *   **Redeployment Process**

      The upgrade process for Pipeline Engine v2 requires mandatory redeployments for full implementation of the new version. Since Pipeline Engine v2 is currently in Beta phase, eventual redeploys after installation are necessary for the complete implementation of identified improvements.\
      \
      Initially, the customer should coordinate the redeployment process with their respective CSM. After the initial redeployment, Engine v2 should operate normally. The customer will be notified in advance of upcoming redeploy dates according to their planning needs, in alignment with the CSM.

## **Pipeline Engine API (Beta Version)**

The Pipeline Engine API was a feature created to allow two versions of the engine to exist simultaneously on the Digibee Integration Platform, only available from the Beta phase onwards.

This can provide different features according to the version of the Engine, in case an issue occurs. Read the documentation to learn [how to change the Pipeline Engine version in your pipelines.](https://docs.digibee.com/documentation/run/how-to-change-the-version-of-the-pipeline-engine-restricted-beta)

{% hint style="info" %}
Both Pipeline Engine API and Engine v2 are in their Beta stages, which means that they may present instability in some scenarios.
{% endhint %}

## **Support Resources**

The implementation of the Engine v2 is expected to be carried out safely, without negative impact on customers and is being closely monitored by the Product team.

If any issues related to the execution of the pipelines appear after the implementation, the customer should contact the Digibee Customer Support through chat via Digibee Integration Platform or via email sent to [support@digibee.com](mailto:support@digibee.com). To improve resolution time, Digibee recommends sharing the following information:

* Pipeline name;
* Project name (if any);
* Environment (Prod or Test);
* Pipeline key (for errors or incidents);
* Error message with date and time;
* Other pertinent information to assist in identification and analysis.
