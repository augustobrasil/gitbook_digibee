---
description: >-
  Understand Double Braces functions offered in the Digibee iPaaS and how to use
  them. Conditional functions return a value according to the criteria you
  establish.
---

# Conditional Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The conditional functions return a value according to the criteria you establish and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

## EQUALTO <a href="#equalto" id="equalto"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function compares two objects (that can be numbers, strings, arrays, etc.) and verifies if they're the same.

### **Syntax**

```
EQUALTO(obj1, obj2 )
```

Let's say you need to validate if this object

```
{
"body1":{
"zip code": “72716”
}
}
```

is the same as this one:

```
{
"body2":{
"zip code": “73736”
}
}
```

In the example below the `false` value will be returned, because the objects are different:

```
{
"valid": {{ EQUALTO( message.body1, message.body2 ) }}
}
```

{% hint style="info" %}
The return of this function will be `true` or `false`.
{% endhint %}

## GREATERTHAN <a href="#greaterthan" id="greaterthan"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function compares if the first number is greater than the second.

### **Syntax**

```
GREATERTHAN(num1, num2 )
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

In the example below the "false" value will be returned:

```
{
"valid": {{ GREATERTHAN( message.num1, message.num2 ) }}
}
```

The `null` value is considered as the smallest possible value for comparison.

`GREATERTHAN(null, null)` will return `false`.

{% hint style="info" %}
The return of this function will be `true` or `false`.
{% endhint %}

## GREATERTHANEQUAL <a href="#greaterthanequal" id="greaterthanequal"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function compares if the first number is greater than or equal to the second.

### **Syntax**

```
GREATERTHANEQUAL(num1, num2)
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

In the example below the `false` value will be returned:

```
{
"valid": {{ GREATERTHANEQUAL( message.num1, message.num2 ) }}
}
```

The _null_ value is considered as the smallest possible value for comparison.

`GREATERTHANEQUAL(null, null)` will return `true`.

{% hint style="info" %}
The return of this function will be `true` or `false`.
{% endhint %}

## IF <a href="#if" id="if"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to make logical comparisons between a value and what you wait for.

Therefore, an IF instruction can have 2 results. The first result happens when the comparison is true and the second when it's false.

### **Syntax**

```
IF(comparison, value-if-true, value-if-false)
```

Let's say you need to make decisions depending if the received value is `true` or `false`:

```
{
"boolean": false
}
```

In the example below the condition value (value-if-false) will be assigned to JSON:

```
{
"zip code": {{ IF( message.boolean, "zip-code-ok", "zip-code-not-ok" ) }}
}
```

{% hint style="info" %}
The return of this function will be any value provided in the messages of the `true`/`false` conditional.
{% endhint %}

## LESSTHAN <a href="#lessthan" id="lessthan"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function compares if the first number is smaller than the second.

### **Syntax**

```
LESSTHAN(num1, num2)
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

In the example below the `true` value will be returned:

```
{
"valid": {{ LESSTHAN( message.num1, message.num2 ) }}
}
```

The `null` value is considered as the smallest possible value for comparison.

`LESSTHAN(null, null)` will return `false`.

{% hint style="info" %}
The return of this function will be `true` or `false`.
{% endhint %}

## LESSTHANEQUAL <a href="#lessthanequal" id="lessthanequal"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function compares if the first number is smaller than or equal to the second.

### **Syntax**

```
LESSTHANEQUAL(num1, num2)
```

### **Payload**

```
{
"num1": 1,
"num2": 2
}
```

In the example below the "true" value will be returned:

```
{
"valid": {{ LESSTHANEQUAL( message.num1, message.num2 ) }}
}
```

The `null` value is considered as the smallest possible value for comparison.

`LESSTHANEQUAL(null, null)` will return `true`.

{% hint style="info" %}
The return of this function will be "true" or "false".
{% endhint %}

## ISOBJECT <a href="#isobject" id="isobject"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is an object.

### **Syntax**

```
ISOBJECT(object)
```

Let's say you need to verify if the received argument is an object:

```
{
"argument": false
}
```

Validating the argument:

```
{
"isObject": {{ ISOBJECT( message.argument) }}
}
```

The response will be `false`, because the value isn't an object.

Now passing an object to the function:

```
{
"argument": {
"test": "xpto"
}
}
```

Validating the argument:

```
{
"isObject": {{ ISOBJECT( message.argument) }}
}
```

The response will be `true`.

## ISARRAY <a href="#isarray" id="isarray"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is an array.

### **Syntax**

```
ISARRAY(object)
```

Let's say you need to verify if the received argument is an array:

```
{
"argument": false
}
```

Validating the argument:

```
{
"isObject": {{ ISARRAY( message.argument) }}
}
```

The response will be `false`, because the value isn't an array.

Now passing an object to the function:

```
{
"argument": [{
"test": "xpto"
}]
}
```

Validating the argument:

```
{
"isArray": {{ ISARRAY( message.argument) }}
}
```

The response will be `true`.

## ISBOOLEAN <a href="#isboolean" id="isboolean"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is a boolean value.

### **Syntax**

```
ISBOOLEAN(objeto)
```

Let's say you need to verify if the received argument is a boolean value:

```
{
"argument": false
}
```

Validating the argument:

```
{
"isObject": {{ ISBOOLEAN( message.argument) }}
}
```

The response will be "true", because the value is boolean.

Now passing an object to the function:

```
{
"argument": {
"test": "xpto"
}
}
```

Validating the argument:

```
{
"isBoolean": {{ ISBOOLEAN( message.argument) }}
}
```

The response will be “false”.

## ISSTRING <a href="#isstring" id="isstring"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is a string.

### **Syntax**

```
ISSTRING(object)
```

Let's say you need to verify if the received argument is a string:

```
{
"argument": "test"
}
```

Validating the argument:

```
{
"isString": {{ ISSTRING( message.argument) }}
}
```

The response will be `true`, because the value is a string.

## ISNUMBER <a href="#isnumber" id="isnumber"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is a number.

### **Syntax**

```
ISNUMBER(object)
```

Let's say you need to verify if the received argument is a number:

```
{
"argument": 123
}
```

Validating the argument:

```
{
"isNumber": {{ ISNUMBER( message.argument) }}
}
```

The response will be "true", because the value is a number.

## ISNULL <a href="#isnull" id="isnull"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to verify if the provided argument is `null`.

### **Syntax**

```
ISNULL(object)
```

Let's say you need to verify if the received argument is a null value:

```
{
"argument": null
}
```

Validating the argument:

```
{
"isNull": {{ ISNULL( message.argument) }}
}
```

The response will be `true`, because the value is a null value.

## SWITCHCASE <a href="#switchcase" id="switchcase"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function allows you to provide multiple comparisons and the due parameters that must be returned if one of these validations returns `true`. If no validation returns `true`, the defined pattern will be used.

### **Syntax**

```
SWITCHCASE(defaultValue, condition1, result1, condition2, result2, …., conditionN, resultN)
```

Let's say you need to validate some conditions to make a decision:

```
{
"argument": null
}
```

Validating the argument:

```
{
"result": {{ SWITCHCASE("failed", ISNULL(message.argument), "ok", ISNUMBER(message.argument), "nok" ) }}
}
```

Therefore, the function configuration will be:

**Valor default:** "failed"

**Condition 1:** ISNULL(message.argument)

**Result If Condition 1 Matches:** "ok"

**Condition 2:** ISNUMBER(message.argument)

**Result If Condition 2 Matches:** "nok"

The response will be "ok", because the first condition was met.

You can also read about these functions:

* [math](math-functions.md)
* [utilities](double-braces-utilities-functions.md)
* [string](broken-reference)
* [JSON](json-functions.md)
* [file](file-functions.md)
* [date](date-functions.md)
* [numerical](numerical-functions.md)
* [comparison](comparison-functions.md)

\
