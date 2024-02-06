---
description: Learn about Digibee Dedicated SaaS implementation model.
---

# Digibee Integration Platform Dedicated SaaS

## Dedicated SaaS Model

Digibee Dedicated SaaS is an implementation model of the Digibee Integration Platform. In this model, Digibee installs and maintains the platform within the customer's cloud subscription. This is ideal for organizations with unique controls that need to be highly private to meet specific corporate policies (such as regulatory standards and cyber-security requirements) without requiring customization.

Customers can choose between major cloud providers such as Amazon Web Services (AWS), Google Cloud Platform (GCP) or Microsoft Azure to run Digibee's platform. The installation process is executed by Digibee's Cloud team while the customer provides the necessary requirements.

## Architecture

The Digibee Integration Platform runs on a Kubernetes cluster that is managed by services such as [Azure Kubernetes Service (AKS) from Azure](https://docs.digibee.com/documentation/platform/digibee-dedicated-saas-installation-on-azure), [Elastic Kubernetes Services (EKS) from Amazon](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/digibee-dedicated-saas-installation-on-aws) and Google Kubernetes Engine (GKE) from Google.

The following diagram details the architecture of the Digibee Integration Platform on a dedicated SaaS model.

<figure><img src="../../.gitbook/assets/Untitled (3).png" alt=""><figcaption></figcaption></figure>

Read our [complete achitecture documentation](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/digibee-integration-platform-architecture-on-dedicated-saas-model) to know more about key components and goals of the platform.&#x20;

## Requirements

### Prerequisites to install Digibee Integration Platform

The following prerequisites are important to ensure proper configuration of components (and communication between them) before you start installing Digibee Integration Platform:

*   **Domains and endpoints:** specify the names of the domains and endpoints to be used. These names are essential for configuring the components and communicating with each other. Test and production environments have specific endpoints that are dynamically deployed as pipelines on the Digibee Integration Platform.



    **Examples of domains and endpoints:**

    **Design time**: Digibee Integration Platform environment where pipelines are built.

```
*.core.digibee.customer-domain.com
*.static.digibee.customer-domain.com
*.portal.digibee.customer-domain.com
*.auth.digibee.customer-domain.com

```

* **Run time**: Digibee Integration Platform environment where pipelines developed in Design Time are executed.

```
*.test.digibee.customer-domain.com
*.api.digibee.customer-domain.com
```

* **Certification:** you have to provide a single wildcard SSL certificate for the specified domains. This certificate is used to ensure the security and privacy of communications between components and end users. For example, a wildcard certificate might be generated as `*.example.digibee.customer-domain.com.`

{% hint style="info" %}
The certificates must also follow the Design Time and Run Time subdomains presented above.
{% endhint %}

* **Access to the GitLab platform:** Access to the GitLab platform is required to configure and run the integration pipeline.

#### **Outbound Internet Access (Outbound traffic)**

Digibee Integration Platform must have access to some specific sites and ports to be installed and working correctly. Outbound traffic keeps the Platform up-to-date and is the customer's responsibility. Check out the [complete list](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/requirements-for-digibee-dedicated-saas-model) with the specific hosts required.

## Connectivity

### Virtual Private Network (VPN)

VPN is used to establish secure and encrypted connections over a public network such as the Internet. Digibee provides an IPSEC-based VPN solution that allows you to extend your private network (a private cloud or an on-premise data center) to your Digibee SaaS realm.

To do this, we create one VPN Linux instance per realm and configure this instance to connect to your VPN Gateway and realm infrastructure simultaneously. Read our documentation about [Digibee connectivity solutions](https://docs.digibee.com/documentation/platform/digibee-connectivity-solutions) to learn more about VPN.

<figure><img src="../../.gitbook/assets/Untitled Diagram (1).png" alt=""><figcaption></figcaption></figure>

#### Site-to-Site VPN for Dedicated SaaS Support

A Site-to-Site VPN allows Digibee support team to access the Digibee Integration Platform installed on client's cloud account for support purposes. Use our [documentation](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/site-to-site-vpn-for-dedicated-saas-customer-support) to know more about the prerequisites and learn the steps needed to set up a Site-to-Site VPN&#x20;

## Dedicated Saas customer responsibilities

We follow the **Shared Responsibility Model** to provide clarity on the responsibilities of customers and Digibee. In this model, the responsibilities are divided so both Digibee and customers can work together to ensure the quality and security of the Dedicated SaaS.

As the provider, Digibee is responsible for managing the environment infrastructure, including hardware maintenance, software updates, and security. On the other hand, the customer is responsible for managing their own data and setting up the environment according to their requirements.

| **Phases**                                 | **Digibee Responsibility** | **Customer Responsibility** |
| ------------------------------------------ | -------------------------- | --------------------------- |
| 1. Subscription Preparation                |                            | ✔️                          |
| 2. Sharing Credentials                     |                            | ✔️                          |
| 3. Validation of access to the environment | ✔️                         |                             |
| 4. File and script storage                 | ✔️                         |                             |
| 5. Explanation of roles and resources      | ✔️                         |                             |
| 6. Execution of installation steps         | ✔️                         |                             |

{% hint style="warning" %}
&#x20;Responsibilities may vary depending on the specific agreement between Digibee and the customer.
{% endhint %}

Read the [documentation](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/dedicated-saas-customer-responsibilities) to learn all of the Dedicated Saas customer responsibilities.

## Custom Kubernetes Node Image Policy

In some cases, customers may choose to use custom images of Kubernetes nodes. These images may include specific configurations, additional software, or modifications needed to meet specific customer requirements. Understand how to handle customer-customized images of Kubernetes nodes within the Kubernetes Service with [this documentation](https://docs.digibee.com/documentation/platform/digibee-integration-platform-dedicated-saas/custom-images-of-kubernetes-nodes).
