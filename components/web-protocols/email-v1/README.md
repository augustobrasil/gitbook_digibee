---
description: Know the component and how to use it.
---

# Email V1 (Deprecated)

{% hint style="info" %}
The **Email V1** is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [Email V2](https://docs.digibee.com/documentation/components/web-protocols/email-v2).&#x20;
{% endhint %}

**Email V1** invokes the SMTP server in a pipeline. To use **Email V1**, you must create a SMTP-type account. Read the [tutorial](https://docs.digibee.com/documentation/components/web-protocols/email-v1/email-v1-usage-example) on how to use the _**Email V1**_ component.&#x20;

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with (DB).

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td>Account</td><td>account to be used by the component</td><td>None</td><td>Any</td></tr><tr><td>From</td><td>set the sender email to be sent by the component</td><td>None</td><td>String</td></tr><tr><td>Subject</td><td>sets the subject to be sent by the component</td><td>None</td><td>String</td></tr><tr><td>Content Type</td><td>sets the Content Type and encoding</td><td>None</td><td>String</td></tr><tr><td>Template</td><td>template body to be used to prepare email templates</td><td>None</td><td>String</td></tr></tbody></table>

### **Parameters examples**

**From:**

```
example@examplo.com.br
```

**Subject:**

```
Example: ${subject}
```

**Content Type:**

```
text/html; charset=UTF-8
```

**Template:**&#x20;

```
<html><body><strong>${firstname} ${lastname}</strong></body></html>
```

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### Input <a href="#input" id="input"></a>

The component waits for a message in the following format:

```
{
    to  : ["abc1@gmail.com","abc2@gmail.com"]
    cc  : ["abc1@gmail.com","abc2@gmail.com"],
    bcc : ["abc1@gmail.com","abc2@gmail.com"],
	   params: { 
                     // Template body replacement parameters
			"paramA":"valueA",
			"paramB":"valueB",
			...
			"paramN":"valueN"
		}
}
```

### Output <a href="#output" id="output"></a>

When there's an error, this is the message shown in the component output:

```
{
	timestamp: 1503608693745,
	code: 999,
	message:  "error message"
}
```

\
Note that, for some errors, body and header are unavailable.
