# Site-to-Site VPN for dedicated SaaS customer support

The purpose of the Site-to-Site VPN connection is to allow our support team to access the Digibee Integration Platform that is installed in your dedicated SaaS environment. This secure connection allows our team of experts to provide direct assistance, helping to develop pipelines and promote integrations, thus optimizing the use of the Digibee Integration Platform.

This VPN configuration also allows our experts to directly access the Digibee Portal built into your environment. In this way, they can provide the necessary support in real time, ensuring the efficiency and effectiveness of the integration operations, as well as clarifying any doubts that may arise.

## **Prerequisites**

VPN configuration is performed by Digibee on Google Cloud Platform (GCP) and is based on the Internet Protocol Security (IPSec) protocol. IPSec is a set of protocols that secure network communications by authenticating and encrypting each data packet in a communication session.\
\
Before Site-to-Site VPN setup, you need to share the following information to establish the VPN connection with Digibee:

* **Static public IP address:** The dedicated SaaS environment must have a static public IP address for the VPN device/application.
* **Dedicated SaaS subnets:** The IP address ranges (CIDRs) of the subnets that Digibee needs to access to support the platform. However, if the installation was carried out using Digibee default values, this data is not necessary.&#x20;
* **VPN device/application:** The manufacturer and model of your VPN device/application. This is needed to provide more specific setup instructions.

## Recommendations&#x20;

* The Digibee VPN that will be configured is a native Google Cloud Platform (GCP) VPN. For more details on configuring VPNs on GCP, refer to the [official Google documentation](https://cloud.google.com/network-connectivity/docs/vpn?hl=pt-br).&#x20;
* In some cases, it may be useful to hold a joint meeting with Digibee's Cloud Engineer to assist with the configuration activity. If necessary, contact us to schedule the meeting.&#x20;
* Once the Site-to-Site VPN is configured and functional, the Digibee support team should be able to access the Digibee Integration Platform resources in the dedicated SaaS environment for support purposes.

## **Setup instructions for customers**

After Digibee configures the VPN on GCP, the you need to perform some actions for the process to complete successfully:

1. **Set Peer IP Address:** the IP address of the Digibee VPN Gateway that will be provided.
2. **Configure the Pre-Shared Key (PSK):** this is the shared key that will be provided by Digibee. This must be the same on both sides of the VPN.&#x20;
3. **Configure traffic selectors:** the traffic selectors are the local (client) and remote (Digibee) subnets that will communicate over the VPN.
4. **Configure forwarding rules (if needed):** if your VPN device/application requires forwarding rules to be configured, configure them to forward VPN traffic to the correct remote subnets.

{% hint style="info" %}
Please note that these are general instructions. We strongly recommend that you review your VPN device/application manufacturer's documentation for specific instructions.
{% endhint %}
