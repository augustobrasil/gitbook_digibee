---
description: Learn how to create a group integration
---

# How to create a group integration

{% hint style="info" %}
The **Integration of IdP groups with Digibee groups** **feature** is currently in beta phase. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

To create a group integration:

1. Go to the **Administration** page.
2. Click on **Groups.**
3. Click on the **Group Integrations** tab.
4. Click on **+CREATE.**

A modal is displayed with a form where you have to enter information about the group integration:

* **Name**: the desired name for the group integration.
* **SAML Scheme**: the rules and format specifications in XML that govern the structure and transmission of SAML messages between IdPs and Digibee. Options are:
  * Microsoft Azure - ADFS
  * Microsoft 2019 - ADFS Classic
  * Custom scheme
* **Xpath**: the XML path to the IdP group IDs. Displayed only when a custom SAML Scheme is selected.
* **IdP group ID code**: unique code identifying the IdP group to be integrated with the Digibee group.
* **Digibee group**: the digibee group to be integrated with the IdP group.

5. Enter the information in the form.
6. Click on **SAVE.**

{% hint style="info" %}
If you want to create multiple group integrations at once, you can do so by clicking on **+INTEGRATION** before saving.
{% endhint %}
