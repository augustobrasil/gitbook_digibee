---
description: Component usage example.
---

# Email V1: Usage example (Deprecated)

Let's say you can't seem to add values to the email template when using the _**Email V1**_ component.

First of all, it's necessary to understand that the email template accepts the use of the input JSON attributes in the **${atrribute}** format. Therefore, the "attribute" must be inside "params", resulting in the following input JSON:

```
{
    "attribute": "valueOfAttribute"
}
```

Afterwards, this is the transformation that must occur:

```
{
    "params": {
        "attribute": "valueOfAttribute"
    }
}
```

This would be the email template preview:

_**Hello ${attribute}!**_

It's also possible to add HTML tag to the template:

```
<div>Hello ${atrribute}!</div>
```

That way, the variable replaced in the sent email would be seen like this:\
_**Hello valueOfAttribute!**_\


Click [here](./) to read the full article about the _**Email V1**_ component.
