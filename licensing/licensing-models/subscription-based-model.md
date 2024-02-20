---
description: >-
  Learn more about the new SaaS subscription model of the Digibee Integration
  Platform.
---

# Subscription-based model

This article introduces the key concepts of the new subscription model launched in April 2022.

Digibee offers a SaaS subscription-based committed use model where the customer has access to the Digibee Integration Platform, support and customer success for a certain period of time.&#x20;

In this model, deployments are made in the quantity of Pipeline Subscriptions and RTUs (Runtime Units) of tests or production. In addition, we apply Platform usage quotas and delivery limitations.

[If you want to know more about how to deploy a pipeline, read the article Deploying a pipeline.](https://docs.digibee.com/documentation/run/deployments)

## Definitions

### Pipeline subscription

Pipeline subscription is the starting price item that allows customers to access Digibee's Platform, support, customer success services, and Intellectual Property (IP). One pipeline subscription refers to one unique integration flow deployed into the Digibee Integration Platform.&#x20;

Includes two (2) Production RTUs deployed in the Production environment, one (1) Test RTU deployed in the Test environment, and all underlying infrastructure required to run them. [Learn more about the definition in the Capacity and Usage quotas article.](https://docs.digibee.com/documentation/licensing/usage-limits)

### Unique integration flow

A business or technology necessity to capture, transform, and/or deliver data from one source to another. Unique means a single Pipeline on a specific version.

### Pipeline version

It's a number (E.g.: 1.2) that represents the unique state of a pipeline. Digibee follows the simplified Semantic Versioning ([www.semver.org](https://semver.org/)) scheme with only the **Major** and **Minor** components. Digibee does not support "additional labels for pre-release and build metadata", and **Major** versions start with 1.&#x20;

For each pipeline subscription, only one pipeline major version can be active (deployed) in a given environment at a given time.

* **Pipeline Major Version**: specifies the version component that controls the breaking changes to a pipeline, that is, changes that would make two major versions incompatible in terms of exposed APIs, behavior, or output.
* **Pipeline Minor Version**: specifies the version component that controls the changes that do not cause two different minor versions to be incompatible with the same major version in terms of the exposed APIs, behavior, or output.

### RTU (Runtime Unit)

RTU (Runtime Unit) is a measure of computing capacity for processing integrations on the Digibee Integration Platform. RTUs can be used to scale integrations vertically and horizontally. When scaled vertically, they can be used in three different sizes: Small (consumes 1 RTU), Medium (consumes 2 RTUs), and Large (consumes 4 RTUs).&#x20;

When scaled horizontally, each new replica will consume the same amount of RTU as the original deployment. Each RTU comes with the underlying infrastructure to run them. [Refer to the Capacity and usage quotas for more information.](https://docs.digibee.com/documentation/licensing/usage-limits)

* **Test RTU** represents the processing capacity to run integrations under an active subscription in a test environment. RTUs must be paired with an existing pipeline subscription.
* **Production RTU** represents the processing capacity to run integrations under an active subscription in a production environment. To deploy a new pipeline in a production environment, pipeline subscriptions and Prod RTUs must be available in your realm.

### Platform Usage quotas

Platform Usage quotas are technical limits imposed on each realm in order to avoid Platform overload and were created based on the average usage of the Platform. These are some of the limits:

* Deployment Size and Replicas (meaning CPU and Memory to run a pipeline or a set of replicas);
* Egress Traffic Rate ;
* Messages being produced/consumed;
* Messages being held in the pipeline for processing;
* Logs retention;
* VPNs;
* Object Store, Digibee Storage, and Relationship data.

## Main rules

### Deployed pipeline subscription rules

You can **build** as many pipelines as you want in the Digibee Integration Platform. All limits are applied in the **deployment** stage. Each pipeline developed can be deployed in test or production environments, respecting the number of available pipeline subscriptions and RTUs.

Pipelines that are deployed on an environment consume (Test or Production) RTUs following their pipeline deployment size and replicas.

In the table below, you can see how many RTUs are consumed by each pipeline deployment size:

| Size   | RTUs consumption |
| ------ | ---------------- |
| Small  | 1                |
| Medium | 2                |
| Large  | 4                |

**Replicas** will consume as many RTUs as the multiplication of the number of replicas and the number of RTUs for the pipeline deployment size.

Every time a pipeline is deployed on a given environment, it is said that a pipeline subscription has been consumed in that environment. Regardless of the number of available RTUs, you can only deploy as many unique pipelines as the number of available pipeline subscriptions.

### Pipeline versions

Two different major versions of the same pipeline are considered two different and unique pipelines and, therefore, consume 2 pipeline subscriptions.

For each pipeline subscription, only one pipeline version can be active in a given environment at a given time.

### Subscription and RTUs validations

The following algorithm is applied before each pipeline deployment in a given environment: first, the algorithm checks if the number of unique pipelines deployed is lower than the number of available pipeline subscriptions.

If this checks out, then the algorithm checks if the number of available RTUs for that particular environment can accommodate the number of RTUs being requested for that pipeline deployment. If this further check passes, then the pipeline is deployed.&#x20;

Otherwise, the deployment fails due to the lack of available pipeline subscriptions or the number of available RTUs.

### Deployed RTU Rules

Test and production RTUs accumulate as more pipeline subscriptions are added. When a pipeline is deployed on any given environment, the number of corresponding RTUs is reduced from the total number of RTUs available on that environment. When there are no more available RTUs in a given environment, then no additional pipelines will be deployable.

Test RTUs and production RTUs and intended to be used in their respective environments and cannot be swapped.

The use of test or production RTUs always requires an existing pipeline subscription. Spare RTUs cannot be used to run pipelines that do not have a pipeline subscription associated with it.
