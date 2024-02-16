---
description: Learn more about the quotas of the Digibee Integration Platform.
---

# Capacity and quotas

This article presents the quotas that apply when running pipelines on the Digibee Integration Platform.

Platform quotas are technical limits created based on average platform usage and applied to each realm. A realm is a customer's private space within the platform where integrations are built, stored, and executed.

This usage policy was created to improve the management of the resources offered by the Platform and to bring more transparency to the process.

## Resource consumption

Computational resources are all items consumed to perform integrations between systems. These resources belong to the [Runtime Unit](https://docs.digibee.com/documentation/run/runtime) (RTU). The following are explanations of each feature.

* **Egress traffic**: measures the amount of data transferred from the Digibee Integration Platform network.
* **EPS** (Executions Per Second): is the metric that calculates how many messages are processed by a given pipeline in a single 1-second window. The maximum number of EPS is calculated for the entire Realm. This number is distributed among all pipelines in use. EPS is directly related to the average processing time and not necessarily to the maximum number of concurrent executions.
* **Queue**: the Platform allows pipeline queues to fill up with pending messages that need to be processed. Queue quotas are calculated for all RTUs used in a single pipeline.
* **Completed executions logs**: these are shown in the Platform's Monitor screen under Completed executions, and quotas are given by the retention time or amount of messages, whichever comes first. The number of messages is calculated according to the number of deployed RTUs for a given pipeline.
* **Pipeline logs:** these are shown in the Platform's Monitor screen under Pipeline Logs or under each completed execution's logs, and quotas are given by the retention time or the amount of stored bytes, whichever comes first. The number of bytes stored is considered per number of deployed RTUs used for a given pipeline.
* **Digibee storage**: it’s a cloud storage system for pipelines where files can be read and written. These files are accessed via [Digibee Storage Connector](https://docs.digibee.com/documentation/components/file-storage/digibee-storage). The Platform sets quotas for the number of bytes stored in this cloud storage system.
* **Relationship management**: the Digibee Integration Platform provides access to a ID relationship management system that can store mappings between data in different systems. The limitation of the relationship management system is related to the number of unique mappings stored.
* **Virtual Private Network** (VPN): it’s a technology that is used to create a secure and encrypted connection between two networks or devices over the internet. When a user connects to a VPN, their internet traffic is encrypted and routed through a secure tunnel to the VPN server. The user’s IP address is replaced with the IP address of the VPN server, which helps to mask the  user’s identity and location.

## Quotas

The quotas are applied in two different scopes.&#x20;

The first scope is called the **Global Scope**, because it includes all pipelines that belong to your entire realm. Your total quotas depend on the size of your contract with Digibee.

The second scope is called the **Local Scope** and is applied to each deployed pipeline. In this case, your total quota depends on the size of the deployment.

{% hint style="info" %}
The values for production and test environments are different.
{% endhint %}

### Contracted quotas

| Resource                | Test Environment                                    | Production Environ.                                   | Grows per        |
| ----------------------- | --------------------------------------------------- | ----------------------------------------------------- | ---------------- |
| Egress traffic          | 10 GB per RTU (monthly)                             | 1 TB per RTU (monthly)                                | Each RTU         |
| Execution rate          | 1 EPS per RTU                                       | 1 EPS per RTU                                         | Each RTU         |
| Digibee Storage         | 10MB                                                | 100MB                                                 | Each RTU         |
| Relationship Management | 100,000 objects (base) and 10,000 objects (per RTU) | 10,000,000 objects (base) 1,000,000 objects (per RTU) | Each RTU         |
| VPNs                    | 1 VPN gateway                                       | 1 VPN gateway                                         | Block of 10 RTUs |
| ZTNA                    | 1 Edge Router                                       | 1 Edge Router                                         |                  |

{% hint style="info" %}
In the case of ZTNA, there can also be 2 edge routers for “prod/test” (redundancy).&#x20;
{% endhint %}

### Deployed quotas

| Resource                  | Test Environment                     | Production Environ.                    | Grows per |
| ------------------------- | ------------------------------------ | -------------------------------------- | --------- |
| Queue                     | Maximum of 100,000 messages in queue | Maximum of 1,000,000 messages in queue | Each RTU  |
| Completed executions logs | 7 days or 604,800 records            | 30 days or 2,592,000 records           | Each RTU  |
| Pipeline logs             | 3 days or 250 MB                     | 10 days or 1 GB                        | Each RTU  |

We don't mix scopes, so you won't see a Global quota split into one pipeline, nor a Local quota summarized with all pipelines. Moreover, you can track your pipeline executions with more details on the Monitor page.

## Capacity

The capacity is very similar to quotas. However, in this case we don't have a usage limit, we have a usage capacity. In other words, this means that if you use the capacity excessively, you might face performance issues.

One of the resources is the **Object Store**. Digibee provides access to a[ temporary Object Store](https://docs.digibee.com/documentation/components/structured-data/object-store) system that can store any type of JSON object. In the **Production** environment, object stores are provisioned in increments that grow with the number of RTUs. This growth follows a similar pattern for each new block of 60 RTUs.

* Up to 60 RTUs: 2 vCPU and 4GB RAM
* Up to 120 RTUs: 2 vCPU and 8GB RAM
* Up to 180 RTUs: 4 vCPU and 12GB RAM

Although the Digibee Capacity Team is always reviewing these levels to ensure that pipelines make the best use of Object Stores, customers must design their pipelines to meet Object Store best practices. Overuse of the Object Store can result in performance degradation for the pipelines. In **Test** environment, Object Stores are shared between different realms and grow according to Digibee Capacity Team definitions. Test Object Stores are not intended to be used intensively. They should be used to validate the functional aspects of the pipelines.

###
