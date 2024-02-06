---
description: >-
  Learn more about deploying and managing the Digibee Integration Platform on
  Elastic Kubernetes Services (EKS)
---

# Digibee Dedicated SaaS installation on AWS

Digibee Dedicated SaaS is an implementation model of the Digibee Integration Platform, where Digibee installs and maintains the platform within the customer's cloud subscription. The Platform is a data management solution that can be installed within an EKS (Elastic Kubernetes Service) cluster on Amazon.

## Amazon Elastic Kubernetes Service

EKS is a managed Kubernetes service for running Kubernetes in the Amazon Web Service (AWS) cloud and in on-premises data centers without needing to install, operate, and maintain your own Kubernetes control plane or nodes.

#### **Digibee Platform architecture on EKS**

Digibee Integration Platform runs on a Kubernetes cluster that is managed by major cloud providers such as AWS, using EKS services and components to function efficiently and scalably. The architecture is designed to be flexible and secure, ensuring proper communication between components and availability of services. Installation is done via a GitLab integration pipeline, which builds the EKS cluster and does all platform upgrade administration through the Helm Chart.

#### **Use of AWS resources by the Digibee Integration Platform**

These are the resources used by Digibee Integration Platform on EKS:

* **Virtual Private Cloud (VPC):** the Virtual Private Cloud is a mandatory resource that enables the Digibee cluster to run inside subnets with a specific model, providing public access to control the kubernetes cluster and private access for worker nodes where the services run. This resource is configured as follows:
  * 1 VPC
  * 2 CIDRs
  * 3 Public Subnets (Internet Gateway)
  * 6 Private Subnets (Nat Gateway) \

* **EKS:** Digibee uses EKS as the Kubernetes solution since the control plane is maintained by AWS. The EKS architecture contains:
  * 1 Cluster EKS with a public and a private endpoint where the public endpoint is used only on the installation part.
  * 8 Managed Node Pools with ASG replicated in 6 private subnets \

* **Elastic File System (EFS):** this resource is essentially focused on availability. Digibee solutions use some databases inside Kubernetes that need a persistent volume solution. EFS is used to mount these persistent volumes with multiple zones. \

* **S3 Buckets:** this resource is used to store the backups from EKS clusters. \

* **Elastic Compute Cloud (EC2):** this resource consists of a virtual machine that enables using a Bastion server in case of quick troubleshooting on downtime or communication failure with the cluster.

### **Installation process on EKS**

#### **Prerequisites to install Digibee Integration Platform on EKS**

Before starting the installation, be sure to verify the installation of AWS Ad Balancer controller on EKS.&#x20;

#### Installation&#x20;

The installation process is supported by an automated Continuous Integration and Continuous Deployment pipeline running on Digibee's Gitlab subscription. This pipeline provides the essential infrastructure components, such as the Kubernetes Cluster and network topology, required to run Digibee's cluster.

Moreover, keeping the installation consistent across customers enables us to streamline support and troubleshooting efforts. By having a standardized infrastructure and deployment approach, we can quickly identify and address any issues, as well as provide effective support when needed. This consistency also facilitates collaboration and knowledge sharing within our team, ensuring a high level of expertise and efficiency in managing and operating the platform.

When a new customer installation occurs, we provision a new job to apply the IAC scripts that connect to your infrastructure using different techniques for each Cloud Provider.

These are the main requirements to install Digibee Integration Platform on Amazon EKS:

* **EKS cluster configuration:** Digibee uses customer-provided access keys and certificates to set up an EKS cluster on Amazon.
* **GitLab integration pipeline setup:** the GitLab platform is accessed to configure the integration pipeline that will build and manage the EKS cluster.
* **Installation of the Digibee Integration Platform:** the Helm Chart is used to install the Digibee platform within the EKS cluster.

#### **Upgrade**

The upgrade process is carried out every 15 days, using an agent internal to the Platform, called **Runner,** which captures the new versions available and upgrades the product, thus ensuring platform security and applying hotfixes.

### **Availability on EKS**

EKS automatically provisions, updates and scales the control plane and worker nodes for the cluster, so that the users do not have to worry about infrastructure management.

One of the key features of managed service is its built-in high availability for the control plane. The control plane is the set of components that manage the state of the cluster, such as the API server and etcd.&#x20;

It automatically creates multiple copies of these components and distributes them across multiple availability zones. This ensures that the cluster remains available even in the event of a single availability zone failure.

Additionally, the control plane provides built-in high availability for worker nodes. Worker nodes are the components that run the applications on the cluster. It also automatically provisions and updates multiple copies of worker nodes and distributes them across multiple availability zones. This ensures that the applications remain available even in the event of a single worker node failure.

### **Best Security Practices for EKS**

Ensuring data, applications and workload security is essential when managing Azure resources, including EKS clusters. Follow these practices to improve your security posture and mitigate potential risks:&#x20;

* **Use IAM roles and policies to control access to EKS resources**: the goal is always to ensure that compromised credentials pose minimal risks. An IAM role defines a set of permissions for a user or group and can control access to resources. Associate an IAM role with an EKS cluster and assign users or groups to the role so that their permissions can be defined.\

* **Use SSL/TLS to encrypt cluster traffic:** TLS is a protocol that provides security for communications over a network and can be used to encrypt cluster traffic between your EKS nodes and your applications.

{% hint style="info" %}
Remember that security is an ongoing process, and it is crucial to stay updated with the latest security recommendations and practices. Access the [official AWS documentation](https://aws.github.io/aws-eks-best-practices/security/docs/) for full details on security practices in EKS.
{% endhint %}
