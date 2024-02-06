---
description: Learn how to test a group integration
---

# How to test a group integration

{% hint style="info" %}
The **Integration of IdP groups with Digibee groups** **feature** is currently in beta phase. Learn more about the [Beta Program](https://docs.digibee.com/documentation/general/beta-program).
{% endhint %}

Follow these steps to test a group integration:

1. Go to the **Administration** page.
2. Click on **Groups**.
3. Click on the **Group Integrations** tab.
4. Search the table for the group integration you want to test, or use the search bar.
5. Click on the **Test integration** icon.
6. Enter an email from a user who belongs to the IdP group you want to test.
7. Click on **TEST**.

A URL will be displayed on your screen.

1. Open a new anonymous window.
2. On the anonoymous window, paste the URL to be redirected to your realm’s login page.
3. Using the anonymous window, log in to the Digibee Integration Platform with your IdP, using the email you entered in step 6.

The **test status** column will change according to the results of this test. You can learn more about group integrations and test statuses by reading the article Integration of IdP groups with Digibee groups.
