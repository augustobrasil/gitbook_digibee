---
description: >-
  Discover more about the Script (JavaScript) component and how to use it on the
  Digibee Integration Platform.
---

# Script (JavaScript)

**Script** **(JavaScript)** allows the execution of JavaScript code excerpts (JavaScript is also known as ECMAScript).

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="303">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Code</strong></td><td>Place to insert the JavaScript code.</td><td>var currentDate = <a href="http://moment.tz/">moment.tz</a>(new Date(), "America/Sao_Paulo");<br>output = {currentDate: currentDate.format()};</td><td>String</td></tr><tr><td><strong>Script Timeout</strong></td><td>Time for the script to expire (in milliseconds).</td><td>10000</td><td>Integer</td></tr></tbody></table>

## Messages flow

### Input

The **Script** **(JavaScript)** component can receive former components parameters from the `"body"` object. In other words, if the component that comes before **Script** **(JavaScript)** has an output that includes an object called `"body"`, it's possible to access it directly in the **Script** **(JavaScript)** code.

* **body:** object imported to the **Script** **(JavaScript)** code scope.

For example, if the input is:

```
{
   "body": {
       "company": "Digibee"
   }
}
```

Then it will be possible to use the **Code** field to do something like this:

```
var x = body.company;
```

### Output

The code executed in the component can produce an output, as long as it's assigned to the global variable named output.

* **success:** `"true"` if the code execution was successful; otherwise `"false"`.
* **output:** custom output of the component.

For example, if you want the **Script (JavaScript)** component output to be `'Hello world'`, assign it to the output variable:

```
output = 'Hello world';
```

The result after the pipeline execution will be:

```
{
   "success": true,
   "output": "Hello world"
}
```

It's also possible to build a JSON object as an output:

```
output = { "company": "Digibee" }
```

The result after the pipeline execution will be:

```
{
   "success": true,
   "output": {
       "company": "Digibee"
   }
}
```

If an error occurs during the script execution, the following output is displayed after the pipeline execution:

```
{
   "success": false,
   "error": "Error message"
}
```

{% hint style="warning" %}
For security reasons, it's not possible to execute a function that makes an external call from the **Script (JavaScript)** component, such as `fetch()` or `XMLHttpRequest()`. It's also not possible to import libraries with `require`.
{% endhint %}

The following libraries are already available and can be used:

* Lodash (global variable to use lodash lib: 'lodash')
* Moment Timezone (global variable to use moment-timezone: 'moment')

\
