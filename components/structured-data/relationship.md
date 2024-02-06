---
description: >-
  Discover more about the Relationship component and how to use it on the
  Digibee Integration Platform.
---

# Relationship

**Relationship** component creates relations between 1 or more entities so that searches in different bases can be made.

{% hint style="info" %}
**Important:** the component doesn't support concurrent accesses while trying to update or save new relations.
{% endhint %}

## Parameters

Take a look at the configuration parameters of the component. Parameters supported by [Double Braces expressions](../../build/double-braces/) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="339">Description</th><th width="144.75">Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Operation to be executed (Match, Create, Update, Get By Field And Value, Translate, and Delete Exact).</td><td>Translate</td><td>String</td></tr><tr><td><strong>Relation Name</strong></td><td>Name given to the created relation.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Translate Path</strong></td><td>Path through which the component searches the IDs to be translated.</td><td>relation.obj.id</td><td>String</td></tr><tr><td><strong>From</strong></td><td>Origin of the search.</td><td>teste</td><td>String</td></tr><tr><td><strong>To</strong></td><td>Destination of the search.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is enabled, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>True</td><td>Boolean</td></tr></tbody></table>

## Operations <a href="#operations" id="operations"></a>

* **Match:** searches a match between 2 fields and the declared value.
* **Create:** creates a relation by the field.
* **Update:** update an existing relation by the field.
* **Get by field and value:** searches a relation between the field and its value.
* **Translate:** translates an IDs list based on the path specified in "Translate Path".
* **Delete Exact:** delete an exact relation in all the declared fields.

{% hint style="info" %}
**Important:** it's necessary to declare the query inside the relation object:
{% endhint %}

```
{
    relation : {
        field1: value
        field2: value
    }
}
```
