---
description: >-
  Discover more about the Email V2 component and how to use it on the Digibee
  Integration Platform.
---

# Email V2

**Email V2** allows you to send simple emails, in HTML format or even with attachments.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="222">Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Necessary for the component to make the authentication of the email server to be used in the dispatch, in case this email service is requested in the authentication.</td><td>N/A</td><td>String</td></tr><tr><td><strong>SMTP Host</strong></td><td>SMTP host of the email server. <br><br>Eg.: (Gmail: smtp.gmail.com)</td><td><a href="http://smtp.gmail.com/">smtp.gmail.com</a></td><td>String</td></tr><tr><td><strong>SMTP Port</strong></td><td>SMTP port of the email server. Port 587 is generally used, but it can vary according to the email server.</td><td>587</td><td>Integer</td></tr><tr><td><strong>From</strong></td><td>Email sender.</td><td>N/A</td><td>String</td></tr><tr><td><strong>To</strong></td><td>Email recipient. If there're multiple recipients, they must be separated by comma. <br><br>Eg: a@a.com,b@b.com,....</td><td>N/A</td><td>String</td></tr><tr><td><strong>CC</strong></td><td>Recipients who will receive a copy of the email. If there're multiple recipients, they must be separated by comma. <br><br>Eg: a@a.com,b@b.com,....</td><td>N/A</td><td>String</td></tr><tr><td><strong>BCC</strong></td><td>Recipients who will receive a hidden copy of the email. If there're multiple recipients, they must be separated by comma. <br><br>Eg:a@a.com,b@b.com,...</td><td>N/A</td><td>String</td></tr><tr><td><strong>Content</strong></td><td>Email body. It accepts the use of Freemarker templates to generate dynamic HTML.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Charset</strong></td><td>Charset to be used in the email body dispatch.</td><td>UTF-8</td><td>String</td></tr><tr><td><strong>Subject</strong></td><td>Subject of the email.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Authenticated</strong></td><td>If the option is enabled, it's mandatory to provide an account with email and password for authentication. <br><br>If not needed, keep it disabled.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Is Over SSL</strong></td><td>If enabled, the dispatch is made via SSL.</td><td>True</td><td>Boolean</td></tr><tr><td><strong>Socket Port</strong></td><td>If <strong>Is Over SSL</strong> is enabled, inform the port used to traffic the message via SSL.</td><td>N/A</td><td>Integer</td></tr><tr><td><strong>Is Over TLS</strong></td><td>If enabled, the dispatch is made via TLS.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Force TLSv1.2</strong></td><td>Sets the use of TLS V1.2 as mandatory for connections with email servers.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Attachments Specification</strong></td><td>If enabled, the form to add attachments will be hidden, and the dispatch in RAW mode may be used, through which you inform the attachments array.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Attachments</strong></td><td>Message attachments. <br><br>The specification is made via form.</td><td>N/A</td><td>Options of Custom Attachments Specification / Array of Objects</td></tr><tr><td><strong>Fail On Error</strong></td><td>If enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for "success."</td><td>False</td><td>Boolean</td></tr></tbody></table>

{% hint style="warning" %}
In the **Attachments** parameter, to add images inside the email body, the "cid:" prefix must be informed before the image name. Eg.: \<img src"cid: image.png" />
{% endhint %}

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

This component doesn't expect any specific input message, only if an expression in Double Braces is informed in some of its fields.

### Output <a href="#output" id="output"></a>

When executing an **Email V2** component, the following JSON structure will be generated:

```
{
    "from": "a@a.com",
    "to": "a@a.com,a@a.com.br",
    "cc":"a@a.com,a@a.com.br",
    "bcc": "a@a.com,a@a.com.br",
    "subject": "Subject",
    "content": "<html>Test Email!</html>",
    "charset": "UTF-8",
    "success": true,
    "attachments": [{
        "type": "ATTACHMENT",
        "attachment": "attachment.extension"
    }]
}
```

* **from:** sender.
* **to:** recipients.
* **cc:** recipients in copy.
* **bcc:** recipients in hidden copy.
* **subject:** subject.
* **content:** message body. If the message body exceeds 256 characters, the result will be truncated.
* **charset:** charset.
* **success:** if the message is well succeed.
* **attachments:** array with the sent attachments.

{% hint style="info" %}
The files manipulation inside a pipeline occurs in a protected way. The files can be accessed in a temporary directory that only the pipeline under deployment has access to.
{% endhint %}

To better understand the messages flow in the Digibee Integration Platform, read our article about [Messages processing](../../build/pipelines/messages-processing.md).

## Email V2 in Action <a href="#email-v2-in-action" id="email-v2-in-action"></a>

See below how the component responds to a determined situation and its respective configuration.

### Sending a text file (xpto.txt) as attachment in RAW mode and the email body having images as well <a href="#sending-a-text-file-xptotxt-as-attachment-in-raw-mode-and-the-email-body-having-images-as-well" id="sending-a-text-file-xptotxt-as-attachment-in-raw-mode-and-the-email-body-having-images-as-well"></a>

* **SMTP Host:** smtp.gmail.com
* **SMTP Port:** 587
* **From:** [email@gmail.com](mailto:email@gmail.com) (this email must be the same one set in the account specified in this component)
* **To:** [some\_other\_email@gmail.com](mailto:some\_other\_email@gmail.com),[second\_email@gmail.com](mailto:second\_email@gmail.com)
* **Subject:** Hello
* **Content:**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
 <head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>Demystifying Email Design</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
</head>
<body>
<img src="cid:myImage.png" />
</body>
</html>
```

* **Authenticated:** enabled
* **Is Over TLS:** enabled
* **Attachment As Raw:** enabled
* **Attachments:**

```
[
{"type": "INLINE", "attachment": "myImage.png" },
{"type": "ATTACHMENT", "attachment": "xpto.txt" }
]
```

The result will be:

```
{
    "from": "email@gmail.com",
    "to": "some_other_email@gmail.com,second_email@gmail.com",
    "cc":"",
    "bcc": "",
    "subject": "Hello",
    "content": "<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv ...TRUNCATED",
    "charset": "UTF-8",
    "success": true,
    "attachments": [
        {"type": "INLINE", "attachment": "myImage.png" },
        {"type": "ATTACHMENT", "attachment": "xpto.txt" }
    ]
}

```

See how to pass values in a dynamic way using the connector:

![](<../../.gitbook/assets/ezgif.com-gif-maker (21).gif>)

In this example, we pass a variable indicating the emission of an invoice:

```
<!DOCTYPE html>
<html>
<head>
  </head>
<body>
 
Good afternoon, <br/>
Below is the invoice <a href='${NF}'>(Click here)</a> referring to the monthly license fee for the platform – due for <b> ${M_VENC}</b>. <br/>
Payment will be via <b>bank transfer</b> - given in the body of the invoice. <br/><br/>


Please, confirm the receipt. <br/>
Any questions, we are available. <br/><br/>
  <br/>
  <br/>
Att.,
Customer relationship
</body>
</html>
```

Notice that the connector allows the use of Double Braces:

![](<../../.gitbook/assets/ezgif.com-gif-maker (19).gif>)

#### JSON Data

```
{
    "remetente": "digibee@gmail.com",
    "destinatario" : "digi@gmail.com",
    "destinatario_cc" : "digi1@gmail.com",
    "destinatario_bcc" : "digi2@gmail.com",
    "port" : "587",
    "host": "smtp.gmail.com",
    "NF": "98787979789",
    "M_VENC" : "13/01/2023"
}
```

### Technology <a href="#technology" id="technology"></a>

We use Freemarker to make our conversions and transformations in the email body template. Read the [Freemarker external documentation](https://freemarker.apache.org/docs/dgui\_template\_exp.html) to know how to use it.
