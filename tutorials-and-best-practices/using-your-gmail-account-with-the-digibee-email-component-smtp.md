---
description: >-
  Learn how to configure the use of a personal Gmail account when using the
  Digibee Integration Platform.
---

# How to use your Gmail account with the Digibee email component (SMTP)

It's highly useful to have your own Gmail account to make dispatches through the Digibee email component, SMTP.

{% hint style="info" %}
The described approach isn't recommended for productive environments. Take into consideration that this article handles a deprecated type of account. Read the article about the [Email V2 component](https://docs.digibee.com/documentation/components/web-protocols/email-v2) and understand the new email dispatch model.
{% endhint %}

## Configuring the account <a href="#h_31e208a18d" id="h_31e208a18d"></a>

To configure your Google Account in the component SMTP, access the Digibee Integration Platform and follow the steps below:

1. Click on the **Administration** icon, on the top right side of the Platform.

<figure><img src="../.gitbook/assets/Administration screen shot.png" alt=""><figcaption></figcaption></figure>

2. Click **Accounts** in the menu on the left side of the screen.

<figure><img src="../.gitbook/assets/Accounts Acreen.png" alt=""><figcaption></figcaption></figure>



3. Insert your Gmail account configurations as shown in the image below:

<figure><img src="../.gitbook/assets/accounts (1).png" alt=""><figcaption></figcaption></figure>

4. Observe the configuration of the Account name (Label) and of the Type.\

5. Define a name for the account that will be later used by the email component.\

6. Choose the smtp-auth-and-properties type.\

7. Click **CONFIRM**.&#x20;

## Authorizing Gmail

Dispatches will be made through SMTP, considered by Gmail a less safe channel. Therefore, it's necessary to authorize Gmail to support non-safe applications.\
\
Read the [official Google documentation](https://support.google.com/accounts/answer/6010255?hl=en) to know how to authorize Gmail to support non-safe applications.

### Getting the authorization link

Gmail might send you an authorization link in the first execution of the email component. If it happens, you'll receive an error in the first execution of your pipeline.

### Account with two-factor authentication

It's recommended for you to use the two-factor authentication in your account. For that, you have to create an application password.

Read [Google documentatio](https://support.google.com/accounts/answer/185833)n to know how to create an application password.

\
