---
description: Learn how to create a Service Principal in Microsoft Azure
---

# How to create a Service Principal on Azure

This document provides a step-by-step guide on how to create a Service Principal in Azure, assign the necessary permissions, and share the relevant information with the team.

Follow the instructions below:

1. **Log in** to the [Azure portal.](https://portal.azure.com/)
2. Click **Azure Active Directory** in the left panel.
3. Click **App Registrations** on the Azure Active Directory dashboard.
4. Click **New registration** at the top of the screen to register a new application.
5. Fill in the details of the new application:
   1. **Name:** name for the Service Principal (for example, digibee-aks-service-principal).
   2. **Supported account types**: select the option **Accounts in this organizational directory only.**&#x20;
   3. **Redirect URI (optional):** leave this field blank.

<figure><img src="../../../.gitbook/assets/Untitled (21).png" alt=""><figcaption></figcaption></figure>

6. Click **Register** to create the Service Principal.
7. Copy the **Application (client) ID** and **Directory (tenant) ID** displayed on the Overview screen of the created Service Principal. You will need to share them with the Digibee team.

{% hint style="info" %}
If the customer has a multitenant, that is, manages several subscriptions, it is necessary to select the multitenant according to its organizational structure.
{% endhint %}
