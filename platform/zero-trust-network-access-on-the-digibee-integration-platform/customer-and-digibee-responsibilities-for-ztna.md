# Customer and Digibee responsibilities for ZTNA

This documentation describes the respective responsibilities of the customer and Digibee for the installation, implementation and operation of the ZTNA connection on the Digibee Integration Platform.

## Responsibilities

| Task                                                                                                                                                                                                                                                    | Digibee's responsibility | Customer Responsibility |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ----------------------- |
| Edge Router Registration (2 ER's, client and Digibee)                                                                                                                                                                                                   | ✔                        | <p><br></p>             |
| Edge router installation (Digibee side)                                                                                                                                                                                                                 | ✔                        | <p><br></p>             |
| Edge router installation (client side)                                                                                                                                                                                                                  | <p><br></p>              | ✔                       |
| Grant access to Edge Router (client side) for each service, endpoint, server, etc. which will be accessed by the DGB platform through the ZTNA tunnel                                                                                                   | <p><br></p>              | ✔                       |
| Using the Chat feature on realm, creating a ticket that provides the endpoint that will be accessed (the resource must be accessible on the Edge Router client side). The ticket must include a table with the endpoint real (FQDN and Port).           | <p><br></p>              | ✔                       |
| Manually patching security vulnerabilities using the “apt” command or a tool/solution like Automox, Ivanti or Ansible can be done during any client patch routine window. Digibee will correct your side monthly or if a zero-day is identified sooner. | ✔                        | ✔                       |
| Black Carbon and other security tools can be used on the image, but exceptions must be made for the 3 binaries: ziti, ziti-router and ziti-edge-tunnel                                                                                                  | <p><br></p>              | ✔                       |
| Creates SERVICES related to each relationship table entry sent by the customer                                                                                                                                                                          | ✔                        | <p><br></p>             |
| Defines APPWANs to ensure that the Edge Router on the DGB side can route traffic to the customer's SERVICES.                                                                                                                                            | ✔                        | <p><br></p>             |

{% hint style="info" %}
&#x20; To install the Edge Router (client side) follow the instructions in this[ link](https://support.netfoundry.io/hc/en-us/articles/5700949793293-Deployment-guides-for-provisioning-customer-edge-routers-in-a-private-cloud)
{% endhint %}

\
Look at the relationship table example below supposing we need to expose two resources from customer side:

1 database server: my\_super\_critical\_database.thebestcustomer.me (FQDN), PORT 3306

1 SFTP server: my\_best\_sftp\_server.thebestcustomer.me (FQDN). DOOR 22

| Real Endpoint (DNS that can be resolved on the client side) | True Door | Result after route creation (used in pipelines)  | Brings |
| ----------------------------------------------------------- | --------- | ------------------------------------------------ | ------ |
| my\_super\_critical\_database.thebestcustomer.me            | 3306      | my\_super\_critical\_database.thebestcustomer.me | 3306   |
| my\_best\_sftp\_server.thebestcustomer.me                   | 22        | my\_best\_sftp\_server.thebestcustomer.me        | 22     |

The columns on the right are result of the implementation of ZTN, those routes will be accessed from the realm pipelines. \
\


\


\
