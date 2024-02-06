# Dedicated Saas customer responsibilities

The following list outlines the specific responsibilities that Dedicated SaaS customers need to be aware of during the installation and operation of Digibee Integration Platform:

* **Infrastructure Costs:** Cloud costs are solely the responsibility of the customer. This includes expenses related to the cloud provider's services, such as computer instances, storage, networking, and any additional resources required for the Digibee Integration Platform. It is recommended that you closely monitor and manage your cloud costs to ensure they align with your organization's budget and requirements.&#x20;
* **Security and Data Management:** Overall security of customer’s infrastructure and data management remains a shared responsibility. While Digibee works diligently to provide a secure platform, it is essential for you, as the customer, to implement and maintain appropriate security measures within your environment. This includes managing user access, implementing data encryption, and adhering to your organization's data governance policies. Regular security assessments and monitoring potential vulnerabilities are recommended.&#x20;
* **Account Credentials/Privileges Safekeeping:** It is essential to ensure that all account access information (usernames, passwords, and any privileged credentials) are stored securely and accessible only to authorized personnel. Any unauthorized access resulting from inadequate safekeeping of these credentials will be solely the responsibility of the customer.

{% hint style="info" %}
We strongly advise implementing strong password policies, enabling multi-factor authentication, and regularly reviewing and updating access privileges to mitigate the risk of unauthorized access.
{% endhint %}

* **Roles and Policies:** As part of the installation process, specific roles and policies need to be established within your cloud environment. These roles and policies determine access and permissions for installing, managing, and operating the Digibee Integration Platform.&#x20;
* **Network:** The customer is responsible for routing traffic to Load Balancers that match the specifics of their environment. Digibee's dedicated SaaS is a fully private cluster. This means that internally these load balancers only respond to the VPC where the platform is installed.&#x20;
* **Outbound Internet Access:** Is mandatory that Digibee Integration Platform has access to the internet. If the customer's policies require controlled internet access you can proxy requests allowing access to specific addresses and ports.&#x20;
* **\[Optional] Certificates:** Customers can provide custom certificates for the Digibee Integration Platform or allow the platform installation to create private certificates using cloud-native services.&#x20;
* **\[Optional] Digibee Object Store:** In case the customer decides to purchase the Object Store MongoDB Atlas, they will be completely responsible for it, including security, privacy, and data management settings. The customer must also ensure that the MongoDB Atlas service is contracted, as it is a necessary component for the Object Store functionality of the platform.
