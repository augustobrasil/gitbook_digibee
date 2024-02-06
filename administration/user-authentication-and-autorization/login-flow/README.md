---
description: Learn more about the login flow on the Digibee Integration Platform.
---

# Login flow

There are two ways to log in to the Digibee Integration Platform:

* [Using Digibee credentials](./#\_3ingd8lvv5ai)
* [Using an identity provider (IdP)](./#\_crldaax16nm3)

## Logins with Digibee credentials <a href="#id-3ingd8lvv5ai" id="id-3ingd8lvv5ai"></a>

### First access <a href="#qkx2jfexd4bk" id="qkx2jfexd4bk"></a>

To access the Digibee Integration Platform for the first time, ask your access manager to **create a user** for you. To learn how to create a user, [read our documentation](https://docs.digibee.com/documentation/administration/new-access-control/basic-concepts-about-users).

Once your access manager has created the user, you will receive **an email asking you to set an access password**. Follow the instructions in the email.

Once you have set up your access password, log in to the Digibee Integration Platform using your credentials and informing the realm you want to access. If two-factor authentication is activated, you will also be asked for a verification code.

#### **Password policy**

Below are the current criteria for the password policy in the Digibee Integration Platform:

* Minimum length of **8 characters**.
* Maximum length of **16 characters**.
* Contains at least **1 uppercase letter**.
* Contains at least **1 lowercase letter**.
* Contains at least **1 special character**.
* Contains at least **1 number**.
* Expiration policy **every 15 days**.
* A policy to reject the **3 previously used passwords**.

![](<../../../.gitbook/assets/image (25) (1).png>)

{% hint style="info" %}
In some cases, Digibee automatically detects your realm. In this case, you only need to enter your email and password.
{% endhint %}

{% hint style="warning" %}
Logins with Digibee credentials can be blocked by the access managers of your realm. In this case you have to [log in with an IdP](./#\_crldaax16nm3). You can read more about this in our article [Authentication rules](https://docs.digibee.com/documentation/administration/identity-provider-integration/idp-accesses).
{% endhint %}

### Expired password <a href="#do8r0fno659h" id="do8r0fno659h"></a>

For security reasons, **Digibee requires its users to change their passwords every 15 days**. If you attempt to log in with an expired password, you will be redirected to the password reset screen.

## Logins using an identity provider (IdP) <a href="#crldaax16nm3" id="crldaax16nm3"></a>

In addition to using Digibee credentials, you can also log in with an IdP. This IdP must be integrated with Digibee beforehand. To learn more about this, read [our article on identity provider integration](../../identity-provider-integration/).

To log in to the Digibee Integration Platform through an IdP, first log in to your IdP. Then, when you log in to the Digibee Integration Platform, click on the button related to the IdP you are using, as shown below.

<figure><img src="../../../.gitbook/assets/Captura de Tela 2023-11-14 às 11.11.51.png" alt=""><figcaption><p>Identity provider login page</p></figcaption></figure>

## Best practices when logging in <a href="#a77cp97ohqcd" id="a77cp97ohqcd"></a>

* Make sure your browser is up to date.
* Deactivate plugins that may conflict with reCAPTCHA.
* Remove or deactivate extensions that perform automations.
* Delete cookies and/or browser history data.
* Enable two-factor verification offered by the Digibee Integration Platform. To learn more, read our documentation on[ how to activate and deactivate two-factor authentication](https://docs.digibee.com/documentation/administration/user-authentication-and-autorization/two-factor-authentication).
