# Custom Images of Kubernetes Nodes

Custom images for Kubernetes nodes may include additional software, security settings, or other necessary modifications to meet customer requirements. Custom images can be created by customers from a base image provided by the cloud vendor or from a custom image provided by the customer themselves.

{% hint style="info" %}
Digibee does not maintain or create these custom images and is not responsible for any problems related to them.
{% endhint %}

When using custom images, the customer is responsible for:

* Create and maintain the custom image.
* Update and manage the software and settings included in the image.
* Ensure custom image compatibility with Digibee Integration Platform and its components.

## **Considerations for Maintaining Custom Images**

As Digibee does not create or maintain customized images, it is important that customers are aware of the possible implications. Some considerations include:

* Digibee is not responsible for performance, security or compatibility issues resulting from the use of custom images.
* Customers should be aware that the use of monitoring agents, security or other features that consume additional resources may affect the performance of the Digibee Integration Platform.
* Responsibility for updating, correcting and general maintenance of custom images rests solely with the customer.

{% hint style="danger" %}
&#x20;It is important to be aware that **using custom images of Kubernetes nodes can result in downtime for the Digibee Integration Platform**, since it is certified to work in a standard Kubernetes environment. If, after an image update, the customer introduces issues in the custom image, this can lead to the loss of Kubernetes nodes and, consequently, generate long-term impacts on the performance and availability of the Platform.
{% endhint %}
