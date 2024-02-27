---
description: >-
  Follow these steps in order to obtain and download the proper digibeectl
  configuration file that is encrypted and able to generate authentication
  tokens.
---

# How to obtain digibeectl configuration file

**digibeectl** requires a configuration file that is encrypted and generates an authentication token. This token is exclusive and mandatory to enable your access to digibeectl resources. Follow the next steps to obtain your own file:

1. Click in the Admin icon.&#x20;

![](../../.gitbook/assets/digibeectl\_admin.png)

2. Click in digibeectl in the menu on the left side of the screen.&#x20;

![](../../.gitbook/assets/digibeectl\_seta.png)

3. Click in the CREATE button



<figure><img src="../../.gitbook/assets/digibeectl_create.png" alt=""><figcaption></figcaption></figure>

4. Give your token a title

![](../../.gitbook/assets/digibeectl\_token.png)

5. Add a list of permissions this token will get. Read the [digibeectl documentation](https://docs.digibee.com/documentation/platform/digibeectl) to know more about permissions.&#x20;

![](../../.gitbook/assets/digibeectl\_permissions.png)

6. Set an expiration period for your token. The period ranges from 1 hour to 1 year.

![](../../.gitbook/assets/digibeectl\_expiration.png)

\


7. Save your permissions list and expiration period.
8. Copy the Encryption key using the copy button and save its content somewhere safe. Then, create an encryption passphrase.

{% hint style="warning" %}
Make sure your passphrase and encryption key are saved somewhere else and secure as they can’t be restored.
{% endhint %}

![](../../.gitbook/assets/digibeectl\_encription.png)

9. Save and download your file.
10. After installing digibeectl, use the following command with the configuration data you have just set:

```
digibeectl set config --file "path/file.json" --secret-key "encryption-key" --auth-key "encryption-passphrase"
```

\
Click [here ](./)to read the complete digibeectl Use Guide.
