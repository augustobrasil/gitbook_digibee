---
description: >-
  Discover more about the Choice component and how to use it on the Digibee
  Integration Platform.
---

# Choice

**Choice** allows flows to take different paths inside a pipeline. It's part of a components set that helps with the integrations organization.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th width="158">Parameter</th><th width="261">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Label</strong></td><td>Defines the path name. It must be a unique name that can be repeated in the pipeline.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Type</strong></td><td>Defines the structure of the different path your flow should take (<strong>When</strong> or <strong>Otherwise</strong>). Read the <a href="choice.md#type">Type</a> section to learn more.</td><td>When</td><td>String</td></tr><tr><td><strong>Type Rule</strong></td><td>Defines the language type (<strong>Simple</strong> or <strong>JSON Path</strong>), which will be used for the condition declaration (every time <strong>When</strong> gets chosen in the <strong>Type</strong> parameter). Read the <a href="choice.md#type-rules">Type Rule</a> section to learn more.</td><td>JSON Path</td><td>String</td></tr><tr><td><strong>Condition</strong></td><td>Declares the condition used to define if the path must be executed. When the previously defined conditions generate conflict or cause an overlap, only one of them will be executed (every time <strong>When</strong> gets chosen in the <strong>Type</strong> parameter).</td><td>$</td><td>String</td></tr></tbody></table>

{% hint style="warning" %}
The configuration parameters will not be available if the component is not connected to other components in the pipeline. Once you connect it properly, just click at the connection point and then in the gear icon to access the parameters as shown in the image detail below:
{% endhint %}



<figure><img src="../../.gitbook/assets/choice detail example nov 23.png" alt=""><figcaption></figcaption></figure>

## Type&#x20;

To work with this component, you must know two structure types of _**Choice**_. They're used to create the paths:&#x20;

* **When:** defines a condition that allows the flow to take a different path towards a specific execution line. You must declare at least one condition.&#x20;
* **Otherwise:** the structure is executed when none of the **When** conditions is attended. You must declare at least one condition.

## Type Rule <a href="#type-rules" id="type-rules"></a>

### **JSON Path**

Defines expressions that go through a JSON component to reach a subset. Whenever you use **Choice**, a match will be made for the path execution.          &#x20;

Imagine that, in the path that comes before **Choice**, your data flow has the following output:

```
{
    "city" : "New York"
}
```

The following condition declared as **When** validates the path your flow should take:

```
$.[?(@.city == 'New York')]
```

Know the other options for the **JSON Path** declaration:

<table data-full-width="true"><thead><tr><th width="201">JSON Path</th><th>Description</th></tr></thead><tbody><tr><td><strong>$</strong></td><td>The object root or array.</td></tr><tr><td><strong>.property</strong></td><td>Selects a specific object in the related object.</td></tr><tr><td><strong>['property']</strong></td><td>Selects a specific property in the related object. Be sure to put only single quotes around the property name. Tip: consider this instruction if the property name has specific characters, such as spaces, or begins with a character other than A..Za..z_.</td></tr><tr><td><strong>[n]</strong></td><td>Selects the n-th element of an array. The indexes start with 0.</td></tr><tr><td><strong>[index1,index2,…]</strong></td><td>Selects array elements with specific indexes and returns a list.</td></tr><tr><td><strong>..property</strong></td><td>Recursive descent: searches for a specific property name recursively and returns an array with all the values with this property name. It always returns a list even if only 1 property is found.</td></tr><tr><td><strong>*</strong></td><td>Wildcard selects all the elements in an object or array, no matter that their names or indexes are. For example, <code>address.*</code> means all the properties of the address object and <code>book[*]</code> means all the items inside a book array.</td></tr><tr><td><strong>[start:end] / [start:]</strong></td><td>Selects elements of a start array and even, although not necessarily, an end array. If the end is omitted, select all the arrays until the end of the array. A list is returned.</td></tr><tr><td><strong>[:n]</strong></td><td>Selects the first n elements of the array. A list is returned.</td></tr><tr><td><strong>[-n:]</strong></td><td>Selects the last n elements of the array. A list is returned.</td></tr><tr><td><strong>[?(expression)]</strong></td><td>Filter expression. It selects all the elements in an object or array that match the specified filter. A list is returned.</td></tr><tr><td><strong>[(expression)]</strong></td><td>Script expressions can be used instead of explicit property names or indexes. For example, <code>[(@.length-1)]</code>, that selects the last item of an array. Here, the length refers to the current array length more than a JSON file named "length".</td></tr><tr><td><strong>@</strong></td><td>Used for filter expressions to make reference to the current node that is being processed.</td></tr><tr><td><strong>==</strong></td><td>Equal to. 1 and '1' are considered the same result. String values must be attached in single quotes (and not in double quotes): <code>[?(@.color=='red')]</code>.</td></tr><tr><td><strong>!=</strong></td><td>Different than. String values must be attached in single quotes.</td></tr><tr><td><strong>></strong></td><td>Greater than.</td></tr><tr><td><strong>>=</strong></td><td>Greater than or equal to.</td></tr><tr><td><strong>&#x3C;</strong></td><td>Less than.</td></tr><tr><td><strong>&#x3C;=</strong></td><td>Less than or equal to.</td></tr><tr><td><strong>=~</strong></td><td>Compatible with a JavaScript RegEx. For example, <code>[?(@.description =~ /cat.*/i)]</code> matches items whose descriptions start with "cat" (case-insensitive).</td></tr><tr><td><strong>!</strong></td><td>Used to deny a filter. For example, <code>[?(!@.isbn)]</code> matches items that don't have the "isbn" property.</td></tr><tr><td><strong>&#x26;&#x26;</strong></td><td>Logical AND operator. Example: <code>[?(@.category=='fiction' &#x26;&#x26; @.price &#x3C; 10)]</code></td></tr><tr><td><strong>||</strong></td><td>Logical OR operator. Example: <code>[?(@.category=='fiction' || @.price &#x3C; 10)]</code></td></tr></tbody></table>

Read this [JSON Path article](https://goessner.net/articles/JsonPath/) to learn more about the topic.

### Simple <a href="#simple" id="simple"></a>

It's basically a small and simple language to evaluate expressions and predicates without demanding new dependences or JSON path knowledge.\
&#x20;                &#x20;

Imagine that, in the path that comes before **Choice**, your data flow has the following output:

```
{
    "city" : "New York"
}
```

&#x20;                      \
The condition declared as **When** validates the path your flow should take:

```
#{city} == 'New York'
```

&#x20;       &#x20;

Know the other options for the **Simple** declaration:

<table><thead><tr><th width="194">Simple</th><th>Description</th></tr></thead><tbody><tr><td><strong>==</strong></td><td>Equal to.</td></tr><tr><td><strong>=~</strong></td><td>Equal to, case-insensitive when comparing strings.</td></tr><tr><td><strong>></strong></td><td>Greater than.</td></tr><tr><td><strong>>=</strong></td><td>Greater than or equal to.</td></tr><tr><td><strong>&#x3C;</strong></td><td>Less than.</td></tr><tr><td><strong>!=</strong></td><td>Different.</td></tr><tr><td><strong>!=~</strong></td><td>Different than, case-insensitive when comparing strings.</td></tr><tr><td><strong>regex</strong></td><td>Validates if a string matches the specified RegEx. Example: <code>#{city} regex 'New.*'</code></td></tr><tr><td><strong>&#x26;&#x26;</strong></td><td>Logical AND operator. Example: <code>#{city} == 'New York' &#x26;&#x26; #{state} == 'NY'</code></td></tr><tr><td><strong>||</strong></td><td>Logical OR operator. Example: <code>#{city} == 'New York' || #{state} == 'CA'</code></td></tr></tbody></table>

&#x20;

**Example:**

<figure><img src="../../.gitbook/assets/choice example nov 23.png" alt=""><figcaption></figcaption></figure>
