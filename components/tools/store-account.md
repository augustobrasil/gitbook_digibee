---
description: Learn how to store accounts dynamically.
---

# Store Account (Restricted Beta)

{% hint style="info" %}
This feature is in the Restricted Beta phase and is only available to specific customers.
{% endhint %}

**Store Account** is a [Pipeline Engine v2](https://docs.digibee.com/documentation/run/pipeline-engine-change/how-to-change-the-version-of-the-pipeline-engine-restricted-beta) exclusive component. It plays a critical role in the secure and dynamic storage of accounts locally and later, in a Vault. To enable dynamic use of accounts in different components, you must follow a two-step process:

1. Store the desired account using the **Store Account** component.
2. Reference the account name in the component where you intend to use it.

This ensures seamless and secure access to the required accounts across different functionalities.

Take a look at the configuration parameters of the component:

* **Account Name:** the account name that will be stored.
* **Account Type:** the account type of the account that will be stored. Supported accounts: API Key, AWS V4, Basic, Certificate Chain, Custom Auth Header, Google Key, Oauth Bearer Token, Private Key, Public Key, Secret Key, SMTP Auth, and NTLM.
*   **Scoped:** when the option is active, the stored account is isolated to other sub-process. In that case, sub-processes will see their own version of the stored account data.

    \
    To know more about the **Scoped** feature, check out the [Dynamic Accounts documentation](https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta).

To store the account you must fill the fields, which varies depending on the account type. To see all the fields for a specific account type, check out the [account documentation](https://docs.digibee.com/documentation/settings/accounts).

{% hint style="info" %}
**Note:** account types Kerberos and Oauth2 are not yet supported to use dynamically.
{% endhint %}

## How to configure the Store Account?

**Account Name:** test-db

**Account Type:** Basic

**Username:** \<DB USERNAME>

**Password:** \<DB PASSWORD>

## Usage examples

For example, assume it is necessary to authenticate to a database using a Basic credential. Perform the following steps:

1. Configure the **Store Account** to create this credential to be used in the **DB V2** component.
2. Connect the **DB V2** component and configure the correct data of the database to be accessed.
3. Configure the following parameters in the **DB V2**:

* enable the **Use Dynamic Account** parameter.
* **Account Name:** test-db.

After following the configuration steps, you can dynamically use access to this database.
