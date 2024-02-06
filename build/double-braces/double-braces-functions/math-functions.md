---
description: >-
  View Double Braces functions in the Digibee iPaaS and how to use them. This
  pages discusses Math functions and how they help users utilize math operations
  with ease.
---

# Math Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The math functions make math operations and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

### ABS <a href="#abs" id="abs"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the absolute value of a number.

**Syntax**

ABS(number)

Let's say you need the absolute value of the number in the example below:

```
{

“a”: -34

}

{

“abs”: {{ ABS( message.a ) }}

}
```

The return of this function will be 34.0.

### CEIL <a href="#ceil" id="ceil"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the smallest (closer to the negative infinite), greater or equal number to the argument value and equal to a whole math number.

**Syntax**

CEIL(number)

```
{

“a”: 12.885

}

{

"ceil": {{ CEIL( message.a ) }}

}
```

The return of this function will be 13.0.

### DIVIDE <a href="#divide" id="divide"></a>

By using Double Braces, you can combine the function with the ss to the input JSON element of a component.

The function is applied to divide a number by the other.

**Syntax**

DIVIDE(numerator, denominator)

```
{

“a”: 10

}

{

"divide": {{ DIVIDE( message.a, 2 ) }}

}
```

The return of this function will be 5.0.

### LOG <a href="#log" id="log"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to divide a number by the other.

**Syntax**

LOG(value, base)

```
{

“a”: 8

}

{

"log": {{ LOG( message.a, 2 ) }}

}
```

The return of this function will be 3.0.

### MAX <a href="#max" id="max"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to declare the greater value between two provided numbers.

**Syntax**

MAX(num1, num2)

```
{

“a”: 8

}

{

"max": {{ MAX( message.a, 2 ) }}

}
```

The return of this function will be 8.0.

### MIN <a href="#min" id="min"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to declare the smallest value between two provided numbers.

**Syntax**

MIN(num1, num2)

```
{

“a”: 8

}

{

"min": {{ MIN( message.a, 2 ) }}

}
```

The return of this function will be 2.0.

### MOD <a href="#mod" id="mod"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the rest of the division operation.

**Syntax**

MOD(numerator, denominator)

```
{

“a”: 8

}

{

"mod": {{ MOD( message.a, 2 ) }}

}
```

The return of this function will be 0.0.

### MULTIPLY <a href="#multiply" id="multiply"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to multiply n values.

**Syntax**

MULTIPLY(num1, num2, ..., num)

```
{

“a”: 8

}

{

"mult": {{ MULTIPLY( message.a, 2 ) }}

}
```

The return of this function will be 16.0.

### POW <a href="#pow" id="pow"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to bring the exponential.

**Syntax**

POW(num1, exp)

```
{

“a”: 2

}

{

"pow": {{ POW( message.a, 2 ) }}

}
```

The return of this function will be 4.0.

### ROUND <a href="#round" id="round"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return the closest number to the argument, with the ties rounded to the positive infinite.

**Syntax**

ROUND(num1)

```
{

“a”: 12.345

}

{

"round": {{ ROUND( message.a ) }}

}
```

The return of this function will be 12.0.

### SQRT <a href="#sqrt" id="sqrt"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to extract the square root of the number.

**Syntax**

SQRT(num1)

```
{

“a”: 4

}

{

"sqrt": {{ SQRT( message.a ) }}

}
```

The return of this function will be 2.0.

### SUBTRACT <a href="#subtract" id="subtract"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to subtract a number from another.

**Syntax**

SUBTRACT(num1, num2)

```
{

“a”: 10

}

{

"sub": {{ SUBTRACT( message.a, 2 ) }}

}
```

The return of this function will be 8.0

### SUM <a href="#sum" id="sum"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to sum n values.

**Syntax**

SUM(num1, num2, ..., num)

```
{

“a”: 8

}

{

"sum": {{ SUM( message.a, 2 ) }}

}
```

The return of this function will be 10.0.

### Other functions

You can also read about these functions:

* [comparison](comparison-functions.md)
* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [file](file-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
