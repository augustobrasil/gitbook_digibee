---
description: Learn how to archive a group integration
---

# How to archive a group integration

{% hint style="info" %}
The **Integration of IdP groups with Digibee groups** **feature** is currently in beta phase. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

When you archive a group integration, all permissions granted by those groups are lost.

Once you have archived a group integration, you cannot undo it, but you can create a new group integration with the same settings.

Follow these steps to archive a group integration:

1. Go to the **Administration** page.
2. Click on **Groups.**
3. Click on the **Group Integrations** tab.
4. Search the table for the group integration you want to archive, or use the search bar.
5. Click on the **box icon.**
6. Write a note explaining why you are archiving that group integration.
7. Click on **ARCHIVE.**

If you archive all active group integrations, your realm will be considered a **non-federated realm** again. This means:

* Users in this realm who log in with an Identity Provider (IdP) still have the same permissions as the Digibee groups that correspond to the archived group integrations.
* Users of this realm who log in with Digibee credentials will continue to receive their permissions from the Digibee groups they belong to.
