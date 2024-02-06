---
description: >-
  Learn about Double Braces, an expression language developed by Digibee that
  users can take advantage of in order to reference and manipulate data within a
  pipeline
---

# Double Braces Functions

You can use Double Braces functions to manipulate data in a pipeline.

## Syntax

Double Braces functions are enclosed within two sets of curly braces and a blank space, with the function name followed by a list of parameters enclosed in parentheses, like this:

```
{{ FUNCTIONNAME(param1, param2) }}
```

Double Braces functions are case-insensitive, but we recommend writing them in upper case as a best practice.

### Nesting functions

You can use Double Braces function calls inside other functions, like this:

```
{{ OUTSIDEFUNCTION(INSIDEFUNCTION(param1,param2), param3) }}
```

When you do this, the functions are executed from the inside to the outside. That is, in the example above, `INSIDEFUNCTION` is executed first and its output is used as a parameter for `OUTSIDEFUNCTION`, which is executed last.

Unlike programming languages, Double Braces expressions executes all functions at the same moment, regardless of whether the IF condition is `true` or `false`. This differs from programming languages, which usually execute functions only after checking the IF condition.

#### Example

**Input**

```
{
    "date": "2022-10-26T03:00:00Z"
}
```

**Double Braces expression**

```
{
    "format": {{ IF(EQUALTO(SIZE(message.date),20),FORMATDATE( message.date, "yyyy-MM-dd'T'HH:mm:ss'Z'", "dd/MM/yyyy"),FORMATDATE( message.date, "yyyy-MM-dd'T'HH:mm:ss.SSS'Z'", "dd/MM/yyyy")) }}
}
```

**Output**

```
{
  "success": false,
  "message": "Encountered a configuration error while generating JSON",
  "error": "com.digibee.pipelineengine.exception.PipelineEngineConfigurationException: com.digibee.doublebraces.service.DoubleBracesConfigurationException: Syntax error parsing double braces expression {{ IF(EQUALTO(SIZE(message.date),20),FORMATDATE( message.date, \"yyyy-MM-dd'T'HH:mm:ss'Z'\", \"dd/MM/yyyy\"),FORMATDATE( message.date, \"yyyy-MM-dd'T'HH:mm:ss.SSS'Z'\", \"dd/MM/yyyy\")) }}: Could not parse date/time evaluating function FORMATDATE. Error: Text '2022-10-26T03:00:00Z' could not be parsed at index 19"
}
```

## Function list

Below, we have listed Double Braces functions by groups based on their usage.

### COMPARISON <a href="#comparison" id="comparison"></a>

Used to compare booleans inputs. To learn more, read the article [Comparison Functions](comparison-functions.md):

* AND
* NOT
* OR
* XOR

### NUMERICAL <a href="#numerical" id="numerical"></a>

Used to manipulate numeric values. To learn more, read the article [Numerical Functions](numerical-functions.md):

* FORMATNUMBER
* TODOUBLE
* TOINT
* TOLONG

### CONDITIONAL <a href="#conditional" id="conditional"></a>

The functions in this group return a value according to a specified criteria. To learn more, read the article [Conditional Functions](conditional-functions.md):

* EQUALTO
* GREATERTHAN
* GREATERTHANEQUAL
* IF
* LESSTHAN
* LESSTHANEQUAL
* ISOBJECT
* ISARRAY
* ISBOOLEAN
* ISSTRING
* ISNUMBER
* ISNULL
* SWITCHCASE

### DATE <a href="#date" id="date"></a>

Used to manipulate dates. To learn more, read the article [Date Functions](date-functions.md):

* FORMATDATE
* NOW
* SUMDATE
* TOISODATE
* DIFFDATE

### FILE <a href="#file" id="file"></a>

Used to query metadata and validate files. To learn more, read the article [Comparison Functions](comparison-functions.md):

* FILEEXISTS
* FILESIZE

### JSON <a href="#json" id="json"></a>

Used to manipulate JSON objects. To learn more, read the article [JSON Functions](json-functions.md):

* JSONPATH
* TOJSON
* UNESCAPEJSON
* GETELEMENTAT
* LASTELEMENT
* REMOVEAT
* ARRAYTOOBJECT
* OBJECTTOARRAY
* NEWEMPTYOBJECT
* NEWEMPTYARRAY

### MATH <a href="#math" id="math"></a>

Used to make mathematical operations. To learn more, read the article [Math Functions](math-functions.md):

* ABS
* CEIL
* DIVIDE
* LOG
* MAX
* MIN
* MOD
* MULTIPLY
* POW
* ROUND
* SQRT
* SUBTRACT
* SUM

### STRING <a href="#string" id="string"></a>

Used to manipulate strings. To learn more, read the article [String Functions](broken-reference):

* CAPITALIZE
* CONCAT
* ESCAPE
* INDEXOF
* JOIN
* LASTINDEXOF
* LEFTPAD
* LOWERCASE
* MATCHES
* NORMALIZE
* REPLACE
* RIGHTPAD
* SPLIT
* SUBSTRING
* TOSTRING
* UPPERCASE
* CONTAINS

### UTILITIES <a href="#utilities" id="utilities"></a>

Used to make operations that do not fit the other categories. To learn more, read the article [Utilities Functions](double-braces-utilities-functions.md):

* BASEDECODE
* BASEENCODE
* UUID
* TOBOOLEAN
* SIZE
