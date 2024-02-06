---
description: >-
  Discover more about the Throw Error component and how to use it on the Digibee
  Integration Platform.
---

# Throw Error

**Throw Error** throws an error inside a pipeline or subpipeline. It can be used to:

* interrupt a pipeline with an error.
* interrupt a component that uses subpipelines for processing.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Error Message</strong></td><td>Defines the error message that goes with the error code.</td><td>N/A</td><td>String</td></tr><tr><td><strong>HTTP Status Code</strong></td><td>Defines the code of the error (we use it based on HTTP errors code).</td><td>500-Internal Server Error</td><td>Integer</td></tr><tr><td><strong>Enable Custom Error</strong></td><td>Defines that the user wants to use a custom error.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Custom Error (JSON)</strong></td><td>Can be used to define a custom error message (in this case, <strong>HTTP Status Code</strong> and <strong>Error Message</strong> are ignored).</td><td>N/A</td><td>String</td></tr></tbody></table>

## Throw Error in Action <a href="#throw-error-in-action" id="throw-error-in-action"></a>

### Treating standard errors (customErrorEnabled) <a href="#treating-standard-errors-customerrorenabled" id="treating-standard-errors-customerrorenabled"></a>

**Throw Error** can be used to treat standard errors. Standard errors are those that follow the definitions of the Digibee Integration Platform and that contain a code and a message.

When this type of error results in the pipeline interruption, then the following output is produced:

```
{
  "timestamp": <a long number informing the timestamp when the error was generated>,
  "error": <the configured message>,
  "exception": "PipelineEngineRuntimeException",
  "code": <the configured code>
}
```

### Treating custom errors <a href="#treating-custom-errors" id="treating-custom-errors"></a>

_**Throw Error**_ can also be used to treat custom errors. In this case, a complete JSON object is informed in the component configuration and lately informed in the output of the error-resulting pipeline.

{% hint style="info" %}
Some triggers, such as [**REST**](../triggers/rest-trigger.md), [**HTTP**](../triggers/http-trigger.md)**,** and [**HTTP File**](../triggers/http-file-trigger/), need to receive a code and an error property in the pipeline output to prepare the return code of the HTTP call.
{% endhint %}

### Components that use subpipelines <a href="#components-that-use-subpipelines" id="components-that-use-subpipelines"></a>

When **Throw Error** is used in a component that uses the **onProcess** subpipeline, the configured error is informed as the input of the **onException** subpipeline. If the **Custom Error (JSON)** option is filled, then the content of the JSON object is the same as the one described in the [Treating standard errors](throw-error.md#treating-standard-errors-customerrorenabled) or [Treating custom errors](throw-error.md#treating-custom-errors) sections.

To better understand the concept, [read the article Subpipelines](https://docs.digibee.com/documentation/build/pipelines/subpipelines).
