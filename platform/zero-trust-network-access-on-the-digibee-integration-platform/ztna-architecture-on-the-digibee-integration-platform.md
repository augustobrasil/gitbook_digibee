---
description: Learn about the details of Zero Trust Network access on Digibee
---

# ZTNA architecture on the Digibee Integration Platform

Understanding the roles and concepts of ZTNA components is crucial for implementing and managing a Zero Trust architecture effectively. Here are the main roles and concepts of this technology:

### Edge Router

* Function: Acts as the gateway between the internal network and external networks, providing a secure entry point for traffic.
* Role in Zero Trust: Implements security policies, access controls, and may play a role in the segmentation of the network

### Fabric

* Function: The fabric is the overarching network architecture that ties together various components and ensures a consistent, secure, and adaptable framework.
* Role in Zero Trust: Enables the dynamic enforcement of security policies and controls across the entire network, regardless of the location or nature of the devices and users.

### MTLS

* Mutual TLS east-west and north-south.  Mutual TLS (mTLS) is a big deal.  Not just for ZTNA or compliance requirements, but because it is far more secure.  It is also simpler since mTLS immediately reduces the noise which ops needs to deal with by ensuring only authenticated clients can talk on your zero trust network.&#x20;

## Digibee Initial Topology

The integration of ZTNA, Edge Routers, and smart routing solutions creates a robust and flexible network infrastructure that ensures both security and optimal performance. The diagram below illustrates how ZTNA works within the Platform:\
\


<figure><img src="https://lh7-us.googleusercontent.com/izrv7ggjQjnvLe_EQO8dDpJ2F_wmMxmyTSPbXF499D3zGD4dTO5hVf474cYmzEYLlCGpZNDEv4D5dS6vj5wJLKL14C6RNXpNq4rSnY1tb38PmO6dEu98xBcvTArvKtx9GpF-G1_eiUBlaMOs35isNkM" alt=""><figcaption></figcaption></figure>

\
