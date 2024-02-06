---
description: >-
  Learn more about deploying and managing the Digibee Integration Platform on
  Azure Kubernetes Service (AKS).
---

# Digibee Dedicated SaaS installation on Azure

Digibee Dedicated SaaS is an implementation model of the Digibee Integration Platform, where Digibee installs and maintains the platform within the customer's cloud subscription. Customers can choose between EKS from Amazon, GCP from Google or AKS from Azure to run Digibee's platform.

### **Azure Kubernetes Service (AKS)**

AKS is a management service used to run Kubernetes on Microsoft Azure, which makes it possible to deploy, scale, and manage docker containers and container-based applications in a clustered environment. The Digibee Integration Platform uses AKS to manage the cluster and provide built-in high availability features.

### **Digibee Platform architecture on AKS**

Digibee Integration Platform uses a number of Azure services and components to function efficiently and scalably. The architecture is designed to be flexible and secure, ensuring proper communication between components and availability of services.

#### Main components:

* **Azure Active Directory (AD)**: used to manage and control access to platform resources. Digibee creates and configures a Service Principal with the role "Contributor" to ensure proper access to Azure resources.&#x20;
* **Resources Groups:** are used to organize and manage the resources related to the Digibee Integration Platform. They allow centralized management of resources, which facilitates maintenance and monitoring.&#x20;
* **Virtual Networks and Subnets:** Digibee uses virtual networks and subnets to isolate and protect components and services. They ensure secure communication between components and limit exposure to external threats.&#x20;
* **Load Balancers:** are used to distribute traffic between Digibee Integration Platform components, ensuring service availability and scalability.
* **Kubernetes and Containers:** Digibee uses AKS to manage and operate the containers that make up the solution.
* **Azure Key Vault:** used to securely store and manage application certificates and secrets. Digibee uses Key Vault to retrieve wildcard TLS certificates through NGINX Ingress Controller annotations.

**NOTE:** Digibee uses the NGINX Ingress Controller to ensure consistent and efficient deployment,which provides better user experience and performance.

### **Implementation process**

The installation process is powered by an automated Continuous Integration and Continuous Deployment pipeline running on Digibee's Gitlab subscription. This pipeline provisions the essential infrastructure components such as Kubernetes Cluster and Network Topology required to run Digibee's cluster.

When a new customer installation occurs, Digibee provides a new job to apply the IAC scripts that connect to customer’s infrastructure using specific techniques for each Cloud Provider.

#### **Installation considerations and prerequisites**

During installation of Digibee Integration Platform on Azure, customers must provide specific information and resources such as:

* Domain names for installation
* Access endpoints for test and production environments
* Credentials and permissions required for Service Principal and AD Groups
* NGINX Ingress Controller Configuration and Obtaining TLS Certificates from Azure Key Vault
* Ensure that outgoing traffic is properly configured to allow access to hosts and services required by the Digibee Integration Platform.

#### **Azure installation steps**

1. **Azure environment configuration:** The customer prepares the Azure environment by creating Service Principal, assigning the role of "Contributor" and configuring the specific subscription for Digibee as well as the AD group for the operation team to perform support and maintenance.&#x20;
2. **Sharing of Service Principal Credentials:** The customer shares Service Principal credentials with Digibee's cloud engineering team.&#x20;
3. **GitLab repository configuration:** The Digibee team configures the GitLab repository, including configuration files and Terraform scripts. (up to 1 week with validated data).&#x20;
4. **GitLab Runner Configuration:** The Digibee team configures GitLab Runner to run jobs and pipelines in the customer's environment. (parallel to the previous item).&#x20;
5. **Installation pipeline execution:** The Digibee team executes the installation pipeline, which creates and configures the required Azure resources such as AKS, specific VNet and other components (up to 2 weeks).&#x20;
6. **Installation verification:** The Digibee team verifies that the installation was successful and that all components are working as expected (up to 1 week with validated data).&#x20;
7. **Quality Check:** The Digibee team performs quality tests to ensure that all platform features are in compliance (up to 1 week with validated data).&#x20;
8. **Platform delivery:** The Digibee team provides access and delivers the ready-to-use platform.

### **Creating a Specific Subscription for Digibee**

For better resource management and cost control, it is strongly recommended that the customer create a specific subscription in Azure for Digibee. This provides a level of isolation and control and allows the customer to know which features are associated with the Digibee Integration Platform and more effectively monitor the costs associated with those features.

### **Use of Azure Resources by the Digibee Integration Platform**

The Digibee Integration Platform utilizes a variety of Azure resources to provide its functionality. Here are some of the key resources that are created and managed by the GitLab pipeline using the Service Principal:

* **Azure Kubernetes Service (AKS)**: AKS is Azure's container orchestration service. It is used to manage and scale the containers that make up the Digibee Integration Platform.
* **Virtual Network (VNet):** A VNet is created specifically for AKS. This provides an isolated and secure environment for the AKS and the containers it manages.
* **Bastion Host:** The Bastion Host is a virtual machine that provides a secure point of access to AKS. It is used by the cloud operations team to access the AKS and perform maintenance and troubleshooting tasks.

### Customer and Digibee responsibilities&#x20;

| **Phases**                                 | **Digibee Responsibility** | **Customer Responsibility** |
| ------------------------------------------ | -------------------------- | --------------------------- |
| 1. Subscription Preparation                |                            | ✔️                          |
| 2. Sharing Credentials                     |                            | ✔️                          |
| 3. Validation of access to the environment | ✔️                         |                             |
| 4. File and script storage                 | ✔️                         |                             |
| 5. Explanation of roles and resources      | ✔️                         |                             |
| 6. Execution of installation steps         | ✔️                         |                             |

**NOTE:** Responsibilities may vary depending on the specific agreement between Digibee and the customer.

### **Best Security Practices for AKS**

Ensuring data, applications and workload security is essential when managing Azure resources, including AKS clusters. Follow these practices to improve your security posture and mitigate potential risks:&#x20;

* **Enable threat protection:** Enable Defender for Containers to help secure containers. This Microsoft tool can assess cluster configurations, provide security recommendations, run vulnerability scans, provide real-time protection, and alert for Kubernetes nodes and clusters.\

* **Secure access to the Kubernetes API server and cluster nodes:** The Kubernetes API server provides a single connection point for requests to perform actions within a cluster. This is important to secure and audit access to the API server, limit access, and provide the lowest possible permission levels. \

* **Restrict access to Instance Metadata API:** Add a network policy in all user namespaces to block pod egress to the metadata endpoint.\

* **Regularly update to the latest version of Kubernetes:** To stay current on new features and bug fixes, regularly upgrade the Kubernetes version in your AKS cluster.\

* **Secure container access to resources:** Limit access to actions that containers can perform. Provide the least number of permissions, and avoid the use of root access or privilege escalation.

Remember that security is an ongoing process, and it is crucial to stay updated with the latest security recommendations and practices. Access the [official Microsoft documentation](https://learn.microsoft.com/en-us/azure/aks/operator-best-practices-cluster-security?tabs=azure-cli) for full details on security practices in Microsoft Azure.

### **To-do list for customers**

1. Create a specific subscription for Digibee in Azure.
2. Create a Service Principal in Azure AD.
3. Configure the "Contributor" role for the Service Principal.
4. Share Service Principal credentials with Digibee.
5. Provide the names of the domains and endpoints necessary for the installation of the Digibee Integration Platform.
6. Generate and provide an SSL/TLS wildcard certificate for the Digibee Integration Platform.
