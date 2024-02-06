---
description: >-
  Understand how ZTNA works and how it is used on the Digibee Integration
  Platform
---

# Zero Trust Network Access on the Digibee Integration Platform

## Overview

**Zero Trust Network Access (ZTNA)** is a technology based on the principle of the Zero Trust security model to control access to corporate resources at network level. It provides advanced security and micro-segmentation by treating each user and device like their own perimeter, using identity-based authentication to establish trust and grant access.&#x20;

### How ZTNA works

ZTNA integrates device compliance and health into access policies, giving you the option to exclude non-compliant, infected, or compromised systems from accessing enterprise applications and data. It also eliminates a key threat vector and reduces the risk of data theft or leakage. This ensures that data and resources are inaccessible by default.&#x20;

It assumes that every connection and every endpoint is considered a threat. The framework protects against these threats, whether from outside or inside, even for existing connections. After authentication via an encrypted tunnel, the ZTNA establishes secure access. However, users can only see applications and services for which they have access authorization for.

It's as if ZTNA was the security guard at the entrance to a company. Instead of simply opening the doors for anyone entering the building (network), ZTNA verifies the identity and authorization of each person (device) before allowing access. This is done by requesting credentials, verifying them and granting access only to those who have the required permissions.

### Why use zero trust technology?

According to Gartner's “Emerging Technologies: Adoption Growth Insights for Zero Trust Network Access” report, by 2025, at least 70% of new remote access deployments will be primarily via ZTNA instead of VPN services — up from less than 10% at the end of 2021.

Many organizations are moving to a hybrid cloud infrastructure and adopting cloud and SaaS applications, resulting in enterprise data being distributed between many users and resources globally. This makes it difficult to connect this kind of infrastructure quickly and securely.&#x20;

With Zero Trust, we move away from the perspective of "trust by default" towards "trust by exception". In this way, it is possible to capture user information, manage identities and orchestrate access privileges for individuals within an organization through regulations for systems or networks.

## Benefits of ZTNA

ZTNA eliminates key threat vectors and reduces the risk of data theft or leakage with security-first design principles. It uses resources such as built-in tenant isolation and least privilege access to help with compliance and privacy regulations.\
\
ZNTA presents many benefits such as:

* Fast network configuration in minutes with remote and automated deployment;
* Flexibility to emulate Layer 2 Ethernet with multipath, multicast, and bridging capabilities;
* Security zero trust network solution that provides scalable security with 256-bit end-to-end encryption;
* Internal DNS to resolve distributed multi-network private Fully Qualified Domain Names (FQDN);
* Secure identity and authentication, based on bi-directional certificate verification;
* Least Privileged Access: replaces wide open VPNs to provide the segmentation and isolation you need;
* No more IP Address management: everything works based on the customer’s DNS, so FQDN can be used to target internal systems.

## ZTNA vs. VPN

Both ZTNA and Virtual Private Network (VPN) serve the purpose of securing access to resources and granting access to systems, services, and applications based on defined policies. However, there are significant differences in their functionality. Read the [full documentation](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-the-digibee-integration-platform/ztna-vs.-vpn) to learn the distinction between ZTNA and VPN in detail.

## ZTNA architecture on the Digibee Integration Platform

Digibee has implemented a strategic approach to optimize performance and reduce latency by leveraging the flexibility of ZTNA. The main goal is to improve the user experience for its customers, but also to position itself to effectively address the challenges posed by the dynamic and evolving nature of modern digital ecosystems.

Read the [ZTNA architecture documentation](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-the-digibee-integration-platform/ztna-architecture-on-the-digibee-integration-platform) to learn about the main roles and concepts of Zero Trust Network on the Digibee Integration Platform.

## Prerequisites for using ZTNA on the Digibee Integration Platform

{% hint style="warning" %}
We recommend that you read this topic carefully. It describes the essential settings to ensure that connectivity via ZTNA technology works correctly. If you have any questions about these requirements, please contact our support team.
{% endhint %}

### Firewall Requirements

* All communications between Edge Routers as well as communications from Edge Routers to the Network Controller are done over TLS.
* Proxies and Web Applications Firewalls should be bypassed (or an exception made) for Edge Routers to work properly.
* Deep packet inspection will also cause reachability issues with Edge Routers.
* All Edge Routers make outbound connections only, no inbound initiated traffic is required.

**Inbound Requirements**\
<mark style="color:red;">**Doesn't need any inbound ports.**</mark>

**Outbound Requirements**

Required Ports:

* **80/TCP/UDP** ⇒ towards the network controller for the establishment of the fabric/data layer.
* **443/TCP/UDP** ⇒ towards the network controller for sessions and initial authentication.
* **6262/TCP/UDP** ⇒ towards the network controller are a fabric/data layer for software maintenance.

The diagram below shows the necessary requirements to establish the connection between the Edge Router and the network controller:



<figure><img src="../../.gitbook/assets/Untitled (1) (2).png" alt=""><figcaption></figcaption></figure>

### Edge Router requirements

The installation of the Edge Router is the responsibility of the customer and must be performed in the steps that meet the specifications for each particular cloud environment:

* [Amazon Web Services (AWS)](https://support.netfoundry.io/hc/en-us/articles/360016342971-Deployment-Guide-for-AWS-Edge-Routers)
* [Microsoft Azure](https://support.netfoundry.io/hc/en-us/articles/360016343171-Deployment-Guide-for-Azure-Cloud-Edge-Routers)
* [Google Cloud Platform (GCP)](https://support.netfoundry.io/hc/en-us/articles/360058708912-Deployment-Guide-for-GCP-Edge-Routers)
* [OnPremise](https://support.netfoundry.io/hc/en-us/articles/360016129312-Run-the-Edge-Router-VM-on-Your-Own-Equipment)

{% hint style="info" %}
For either case, Digibee must provide the registration key for each of the Edge Routers that will be created.
{% endhint %}

#### Connectivity

Since the Edge Router will be the bridge between the Digibee side and the customer side, it is mandatory that this component can access all the resources that will be exposed. That is, if the customer needs to expose a database with FQDN[ prod-db.customerdomain.me](http://prod-db.customerdomain.me/), this DNS must be resolved from the Edge Router.

#### Edge Router VM Sizing

Sizing your Edge Router Virtual Machines (VM) correctly is essential for getting the required throughput from this component. Administrators should use these recommendations for allocation of CPU, RAM, and Disk Storage to allocate to VM instances running the Edge Router on the VM stack of your choice.

Check the [documentation](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-digibee-integration-platform/edge-router-vm-sizing) to know the specific configurations for operating Edge Routers VM according to customer environments.

## Customer and Digibee responsibilities

Digibee uses the Shared Responsibility Model, a security framework that outlines which cybersecurity processes and responsibilities are delegated to the service provider and which are delegated to the customer. The goal of this model is to promote stricter security and define responsibilities related to cloud security.

Read the [documentation ](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-the-digibee-integration-platform/customer-and-digibee-responsibilities-for-ztna)to learn more about customers and Digibee responsibilities related to ZTNA.

## Customers to-do list

1. [Get the VM](https://netfoundry.io/resources/support/downloads/networkversion7/#zitirouters) according to the cloud provider that will be used.
2. Check firewall requirements.
3. Check connectivity requirements (example, by using telnet).
4. Configure Edge Router.
5. Create a ticket that specifies the endpoint to be accessed.

