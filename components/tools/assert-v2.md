---
description: >-
  Assert V2 allows users to create the interruption of a pipeline execution when
  a defined condition isn't met. Learn configuration parameters of this
  component.
---

# Assert V2

**Assert V2** allows you to create the interruption of your pipeline execution when a defined condition isn't met. This condition will be evaluated according to the items of the pipeline message, given that the Double Braces are used for it.

{% hint style="info" %}
Use the **Assert V2** component to guarantee a condition or interrupt the flow.
{% endhint %}

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Condition</strong> <code>(DB)</code></td><td>When the condition isn't true, the pipeline execution is interrupted.</td><td>{{ EQUALTO( message.number, 1 ) }}</td><td>String</td></tr><tr><td><strong>Error Message</strong></td><td>Defines the error message returned by the pipeline when the condition isn't true.</td><td>Error</td><td>String</td></tr><tr><td><strong>Internal Error Message</strong></td><td>Field where you define the internal error message when the condition isn't true.</td><td>Internal Error</td><td>String</td></tr><tr><td><strong>HTTP Status Code</strong></td><td>Return status of the component.</td><td>500-Internal server error</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the "success" property.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Messages flow

### Input

The component accepts any input message and can use it through Double Braces.

### Output

The component doesn't change any information of the input message when the condition is true. However, it's returned to the following component or it's used as the final answer if **Assert V2** is the last step of the pipeline.

When the condition is false and the property **Fail On Error** is "true", the output of the component follows the standard structure:

```
{ 
   "timestamp": 1587151050249, 
   "error": "<message declares in the config errorMessage>", 
   "code": <errorCode>
}
```

If **Fail On Error** is "false":

```
{ 
   "error": "<message declares in the config errorMessage>", 
   "internalErrorMessage": "<message declares in the config internalErrorMessage>", 
   "code": <errorCode>, 
   "success": false
}
```

As previously seen, you must use Double Braces expressions in the **Condition** field. Learn more in our[ documentation about Double Braces](https://docs.digibee.com/documentation/build/double-braces-functions).

## Assert V2 in action

* `{{ AND( EQUALTO(message.name, "Arthur"), LESSTHAN( message.number, 40)) }}`

Receiving a message:

```
{ 
   "name": "Jimmy", 
   "number": 39
}
```

The condition will result as "false".

* `{{ AND( EQUALTO(message.name, "Arthur"), LESSTHAN( message.number, 40)) }}`

Receiving a message:

```
{ 
   "name": "Arthur", 
   "number": 39
}
```

The condition will result as "true".
