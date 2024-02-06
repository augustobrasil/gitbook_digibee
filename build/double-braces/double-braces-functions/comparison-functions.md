---
description: >-
  Understand Double Braces functions offered in the Digibee iPaaS and how to use
  them. Learn how Comparison functions let users make comparisons of boolean
  inputs.
---

# Comparison Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The comparison functions make comparisons of boolean inputs and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

## AND <a href="#and" id="and"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

In the AND comparison function, both provided values must be "true" to return "true".

### **Syntax**

```
AND( boolean1, boolean2, …, booleanN )
```

In the example below, the "false" value will be returned:

```
{
"and": {{ AND( true, false ) }}
}
```

{% hint style="info" %}
the `null` value is considered as `false`. The return of this function will be `true` or `false`.
{% endhint %}

## NOT <a href="#not" id="not"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The NOT comparison function returns the opposite received value.

### **Syntax**

```
NOT( boolean )
```

In the example below the "true" value will be returned:

```
{"not": {{ NOT( true ) }}}
```

{% hint style="info" %}
the `null` value is considered as `false`. The return of this function will be `true` or `false`.
{% endhint %}

## OR <a href="#or" id="or"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

In the OR comparison function, at least one of the provided values must be "true" to return "true".

### **Syntax**

```
OR(boolean1, boolean2, …, booleanN )
```

On the example below, the "true" value will be returned:

```
{
"or": {{ OR( true, false ) }}
}
```

{% hint style="info" %}
the `null` value is considered as `false`. The return of this function will be `true` or `false`.
{% endhint %}

## XOR <a href="#xor" id="xor"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The XOR comparison function will only return "true" if the provided values are opposite. Example: TRUE and FALSE or FALSE and TRUE.

With the support to multiple boolean values, the strategic function resolution is made in pairs, from the left to the right. Example: (TRUE and FALSE and TRUE) = FALSE or (FALSE and TRUE and FALSE and FALSE) = TRUE .

### **Syntax**

```
XOR(boolean1, boolean2, …, booleanN )
```

In the example below, the "true" value will be returned:

```
{
"xor": {{ XOR( true, false, true, true ) }}
}
```

{% hint style="info" %}
the `null` value is considered as `false`. The return of this function will be `true` or `false`.
{% endhint %}

You can also read about these functions:

* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [file](file-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
* [math](math-functions.md)
