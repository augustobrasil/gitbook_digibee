---
description: >-
  Discover more about the Assert V1 component and how to use it on the Digibee
  Integration Platform.
---

# Assert V1 (deprecated)

{% hint style="info" %}
The **Assert V1** is deprecated and no longer updated. Please refer to the document with the most recent version of the feature: [Assert V2](assert-v2.md).
{% endhint %}

**Assert V1** allows you to create the interruption of your pipeline execution when a defined condition isn't met. This condition will be evaluated according to the items of the pipeline message, through an Expression Language.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="301">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Condition</strong></td><td>Condition given through the SIMPLE Expression Language. If the condition isn't true, the execution of the pipeline is interrupted.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Error Message</strong></td><td>Defines the error message returned by the pipeline when the given condition isn't true.</td><td>N/A</td><td>String</td></tr><tr><td><strong>HTTP Status Code</strong></td><td>Returns the HTTP status of the component.</td><td>N/A</td><td>Integer</td></tr></tbody></table>

## Messages flow

### Input

The component accepts any input message and can use it through the SIMPLE Expression Language.

#### Output

The component doesn't change any information from the input message when the condition is true. Therefore, it's returned to the following component or it's used as the final output if this component is the last step of the pipeline.

When the condition isn't true, the output of this component will follow the standard pattern:

```
{
 "timestamp": <moment of the interruption in timestamp format>,
 "error": "<message configured in Error Message parameter>",
 "code": <status code configured in HTTP Status Code parameter>
}
```

## SIMPLE Technology

It's an Expression Language intended to be practical and simple to evaluate Expressions and Predicates without demanding new dependencies or JSON Path technology knowledge.

Let’s say you need to validate certain information about city that's manipulated in the pipeline:

```
{
   "city" : "New York"
}
```

Only the messages that contain the field "city" within the value "New York" can be accepted. Otherwise, the pipeline execution should be interrupted.

The **Condition** parameter should be configured as follows:

```
#{city} == 'New York'
```

Know the other options for the SIMPLE expressions declaration:

* **==**: equal to.
* **=\~**: equal to, case-insensitive when comparing strings.
* **>**: greater than.
* **>=**: greater than or equal to.
* **<**: less than.
* **!=**: different.
* **!=\~**: different than, case-insensitive when comparing strings.
* **regex**: validates if a string matches the specified RegEx. Example: #{city} regex 'New.\*'
* **&&**: AND logical operator. Example: #{city} == 'New York' && #{state} == 'NY'
* **||**: OR logical operator. Example: : #{city} == 'New York' || #{state} == 'NY'
* **contains**: validates if a certain value is contained in a string. Example: #{city} contains 'York'
