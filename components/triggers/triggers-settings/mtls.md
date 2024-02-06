---
description: >-
  Learn why mTLS authentication is used in security structures to verify users,
  devices, and servers within an organization. It also helps maintain APIs
  security.
---

# mTLS

## **What is mutual TLS (mTLS)?**

Mutual TLS, or mTLS, is a bilateral authentication protocol. By validating that both parties (server and client) have the correct private key, mTLS assures that the persons or systems at both ends are who they claim to be. Additional verification is provided by the information in their separate TLS certificates. \_\_ The mTLS authentication is often used in security structures Zero Trust to verify users, devices, and servers within a given organization. It can also help us to maintain APIs more secure.

{% hint style="info" %}
**Important**: Zero Trust means that no user, device, or network traffic is trusted by default, an approach that helps eliminate many recurrent security vulnerabilities.
{% endhint %}

## **What is TLS?**

TLS (Transport Layer Security) is a commonly used encryption system on the Internet. TLS, formerly known as SSL, authenticates the server in a client-server connection and encrypts the communication between the client and the server, preventing eavesdropping. There are three key points to remember about how TLS works:

### **1. Public key and private key**

TLS employs a method known as public-key encryption, which is based on a pair of keys – a public and a private one.

* Anything encrypted with the public key can be decrypted only with the private key
* Anything encrypted with the private key, by its turn, can be decrypted only with the public key

As a result, a server that decrypts a message encrypted with the public key demonstrates that it also has the private key. Anyone can see the public key by looking at the TLS certificate for the domain or server.

### **2. TLS certificate**

A TLS certificate is a data file that includes the aforementioned public key, a statement of who issued the certificate (TLS certificates are always issued by a certificate authority), and the certificate's expiration date, as well as other important information that allows it to verify both a server's or device's identity.

### **3. TLS handshake**

The TLS handshake is the procedure for verifying the TLS certificate as well as the server's possession of the private key (or lack thereof). The TLS handshake also aims to determine how encryption will be carried out once the handshake is complete.

## **How to use mTLS on the Digibee Integration Platform?**

The Digibee Integration Platform allows consuming and publishing APIs with mTLS protocol in order to identify clients and servers (through TLS certificates).&#x20;

This article deals with the publication of mTLS enabled APIs. In order to set up and use mTLS in your APIs, follow the steps below:

### mTLS configuration

The mTLS feature requires the installation of a certificate validation infrastructure. Therefore, it is not available for all realms by default, since the client needs to register a certificate using an **Account** created so that the Digibee Operations team can proceed with its installation.

Digibee doesn’t issue certificates, for total security, the certificates must be issued, provided, and managed by the client.&#x20;

Digibee will create new endpoints, other than the regular ones. During the configuration, information regarding the newly created endpoints will be released. MTLS endpoints are exclusive for internet access and are not accessible via VPN.

### **mTLS usage**

In order to publish APIs that use mTLS as a bidirectional authentication protocol, you should use Triggers Rest, HTTP, or HTTP-File.There is a configuration within these triggers to enable the use of mTLS (which will work only after an mTLS configuration is done on the realm).

## **Why use mTLS?**

mTLS allows us to assure that traffic between a client and a server is secure and trusted in both ways. For users who are continually logging into an organization's network or apps, this adds an extra degree of protection. It also checks connections with client devices that don't require a login, such as Internet of Things (IoT) devices.

Basically, mTLS prevents various kinds of attacks, including on-path attacks, spoofing attacks, credential stuffing, brute force attacks, phishing attacks, and malicious API requests.
