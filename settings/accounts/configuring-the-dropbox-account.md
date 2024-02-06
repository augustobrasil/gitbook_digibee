---
description: >-
  Discover how users can set up the Dropbox Connector and how it is used on the
  Digibee iPaaS with this step-by-step guide.
---

# Configuring the Dropbox account

## **How to get an access token** <a href="#h_2db91903cc" id="h_2db91903cc"></a>

Authentication in Dropbox is via an access token.\
Complete the following steps to obtain an access token that can be used on the Dropbox Connector:

### Create app

1. Go to [https://www.dropbox.com/developers/apps](https://www.dropbox.com/developers/apps).
2. Click on **Create app;**

![](<../../.gitbook/assets/01 (12).png>)

3. Choose one of the API types;
4. Then one of the access types;
5. And last, the name of your app;
6. Then click **Create app** to finish this step.

![](<../../.gitbook/assets/02 (20).png>)

### Generate token

1. After clicking **Create App**, you will be redirected to the settings page of your new app, as shown in the image below:

![](<../../.gitbook/assets/03 (15).png>)

2. Then click **Generate** in the **OAuth 2** section. This will give you your access token:

![](<../../.gitbook/assets/04 (13).png>)

3. Your access token has been generated.

![](<../../.gitbook/assets/05 (6).png>)

### Creating an Account

Now we need to create an Account on the platform of the type **oauth-bearer** and insert the generated access token, as follow:

![](<../../.gitbook/assets/06 (7).png>)

Finally, we have our access token configured and our Account created, ready to be used on the Dropbox Connector:

![](<../../.gitbook/assets/07 (2).png>)
