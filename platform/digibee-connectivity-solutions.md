---
description: Learn more about Digibee’s VPN and NAT solutions
---

# Digibee connectivity solutions

## Digibee connectivity solutions

### Learn more about Digibee’s VPN and NAT solutions

Virtual Private Network (VPN) is a technology used to establish secure and encrypted connections over a public network such as the Internet. You can use Digibee’s VPN to connect to your workloads wherever they are hosted.

Digibee provides an IPSEC-based VPN solution that allows you to extend your private network (a private cloud or an on-premise data center ) to your Digibee SaaS realm. To do this, we create one VPN Linux instance per realm and configure this instance to connect to your VPN Gateway and realm infrastructure simultaneously.

A realm can have multiple VPN instances. A VPN instance can belong to a single realm.

<figure><img src="../.gitbook/assets/Untitled Diagram.png" alt=""><figcaption></figcaption></figure>

## How IPSEC works: Phase 1 and Phase 2

IPSEC, the protocol used by Digibee's VPN solution, establishes secure connections over the internet by employing two phases: Phase 1 and Phase 2.

### Phase 1: Establishing a secure channel

In Phase 1, a secure tunnel is established over which information flows between two VPN gateway devices.During this phase, the devices exchange credentials.They identify each other and negotiate to find a common set of security settings to use.

### Phase 2: Securing data transmission

Once Phase 1 is complete, the parties move on to Phase 2. This phase is about securing the data transmitted between the two devices by establishing encryption and authentication policies.

## Using VPN instances as NAT gateways

You can use a VPN instance as a Network Address Translation (NAT) gateway to reach Internet hosts that require a fixed IP. When you do this, your pipelines use the VPN instance as NAT and all outbound traffic to a specific destination is routed through a single IP address associated with that realm’s VPN instance.

## How to add a VPN connection to a realm

To add a VPN connection to a realm, contact Digibee’s support team or your Customer Success Manager (CSM). Be sure to provide the following information:

* IP of the application you want to connect to.
* Port of the application you want to connect to.
* Phase 2 range if the IP of your application is private.

## VPN deployments

VPN gateway sizes depend on the number of RTUs in your current subscription. To learn more about this, read our documentation on [Capacity and quotas](https://docs.digibee.com/documentation/licensing/usage-limits).

## Known limitations

* Our VPN model does not currently support redundancy. If you prefer this type of connection, we recommend using Zero Trust technology, also available on the Digibee Integration Platform. Read our [documentation](https://docs.digibee.com/documentation/platform/zero-trust-network-access-on-the-digibee-integration-platform) to learn more.
* FTP and FTPS components are not compatible with VPN/NAT.
* Our testing for VPN support for inbound connections has been limited to [REST](https://docs.digibee.com/documentation/components/triggers/rest-trigger) and [HTTP](https://docs.digibee.com/documentation/components/triggers/http-trigger) triggers.
* Digibee Integration Platform supports only route-based IPSEC VPNs.
* You cannot connect to subnets which overlap with Digibee’s internal subnet.
  * Digibee SaaS subnet (Brazil) - 10.0.0.0/14 (10.0.0.1 - 10.3.255.254)
  * Digibee Saas subnet (USA) - 172.19.0.0/16 (172.19.0.1 - 172.19.255.254) and 172.12.0.0/16 (172.12.0.1 - 172.12.255.254)
* You cannot use the same VPN instance for two or more realms.
* The peer used to connect to Phase 1 must be `/32`.
