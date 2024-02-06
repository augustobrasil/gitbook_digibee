---
description: >-
  Understand Double Braces functions offered in the Digibee iPaaS. This page
  covers Numerical functions and how they help users provide information to
  components.
---

# Numerical Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The numerical functions treat numbers and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

### FORMATNUMBER <a href="#formatnumber" id="formatnumber"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function can be applied to convert a string element type into a numerical format (including the possibility of treating your _locale_).

**Syntax**

FORMATNUMBER(value, "formatDestination", "localeDest"?)

The items indicated with "?" can be defined with the _null_ value.

* _**asInteger:**_ is optional and BOOLEAN. If "true", the result will be as _Integer_; otherwise, it will be considered _BigDecimal_. The default value is "false".
* _**localeDest:**_ representing _locale_ must be considered for the number generation. If the _localeDest_ isn't defined, _en-us_ will be considered.

**Input value:**

```
{"number": 123456.9123,"negative": -987.123}
```

**Conversion examples:**

```
{
"number-US":{{ FORMATNUMBER( message.number, "###,###.###", "us-EN") }},

"number-BR":{{ FORMATNUMBER( message.number, "###,###.###", "pt-BR") }},

"number-BR-1":{{ FORMATNUMBER( message.number, "###,###.#", "pt-BR") }},

"number-positive-BR-a": {{ FORMATNUMBER( message.number, "'+'###,###.###;'-'###,###.###", "pt-BR") }},

"number-negative-BR": {{ FORMATNUMBER( message.negative, "###,###.###'C';###,###.###'D'", "pt-BR") }},

"number-negative-BR-a": {{ FORMATNUMBER( message.negative, "'+'###,###.###;'-'###,###.###", "pt-BR") }}
}
```

Other _**formatDestination**_ examples:

| Pattern    | Number     | Formatted String |
| ---------- | ---------- | ---------------- |
| ###.###    | 123.456    | 123.456          |
| ###.#      | 123.456    | 123.5            |
| ###,###.## | 123456.789 | 123,456.79000    |
| ###        | 9.95       | 009.95           |
| ##0.###    | 0.95       | 0.95             |

### TODOUBLE <a href="#todouble" id="todouble"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the double value of a whole number.

**Syntax**

TODOUBLE(num1)

```
{

“a”: 12

}

{

"doub": {{ TODOUBLE( message.a ) }}

}
```

The return of this function will be 12.0.

### TOINT <a href="#toint" id="toint"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the whole number of a double number.

**Syntax**

TOINT(num1)

```
{

“a”: 12.345

}

{

"int": {{ TOINT( message.a ) }}

}
```

The return of this function will be 12.

### TOLONG <a href="#tolong" id="tolong"></a>

By using Double Braces, you can have a LONG-type value returned from a number. It's possible to receive not only a string, but also a number as input parameter.

**Syntax**

TOLONG(num1)

```
{

“a”: 12.345

}

{

"long": {{ TOLONG( message.a ) }}

}
```

The return of this function will be 12.

### TONUMBER

This function allows you to convert a string value to a numeric value based on its source format and locale.

**Syntax**&#x20;

TONUMBER(string, formatSource, localeSource?, asInteger?)

The parameters indicated with "?" are optionals.

* **string:** the string to be converted
* **formatSource:** source format of the string. Eg.: "###.###", "###.#", "###,###.##"
* **localeSource:** the string locale, which if not informed, will be considered "en-us"
* **asInteger:** boolean value that indicates if the string must be converted to an integer numeric value. In case it is not defined, the default value is false.

Let's say you need to convert two strings referring to a generic numeric value and a monetary value:

```
{
	"generic": "150.33",
	"currency": "R$ 300.754,15"
}
```

Applying the conversion:

```
{
	"generic": {{ TONUMBER(message.generic, "###.##") }},
	"currency": {{ TONUMBER(message.currency, "'R$ '###,###.##", "pt-br") }}
}
```

The result will be:

```
{
  	"generic": 150.33,
  	"currency": 300754.15
}
```

Other formatting examples:

| String    | Formato | Numérico |
| --------- | ------- | -------- |
| "123.456" |  ###.#  | 123.5    |
| "009.95"  | 000.### | 9.95     |
| "0.95"    | ##0.### | 0.95     |
| "-300"    | '-'###  | -300     |

### RANDOMNUMBERS <a href="#h_732358b7eb" id="h_732358b7eb"></a>

This function allows you to generate random integer numbers based on a range of values.

**Syntax**

RANDOMNUMBERS(_minValue_, _maxValue_)

Let's say you need to generate a random number between 0 and 50000.

Generate the number:

```
{
"randomNumber": {{ RANDOMNUMBERS(0, 50000) }}
}
```

The result will be:

```
{
"randomNumber": 37122
}
```

The values that define the range are inclusive.

{% hint style="info" %}
**IMPORTANT:** the function has a numerical limitation and only accepts values between the range of -9223372036854775808 to 9223372036854775807. Any other value out of those limits will result in an unpredictable execution of the function.
{% endhint %}

### Other functions

You can also read about these functions:

* [comparison](comparison-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [file](file-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
* [math](math-functions.md)
