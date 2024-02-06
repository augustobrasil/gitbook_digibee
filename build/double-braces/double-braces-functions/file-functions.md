---
description: >-
  Understand Double Braces functions offered in the Digibee iPaaS and how to use
  them. Learn how File functions make queries to metadata and make validations
  in files.
---

# File Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The file functions make queries to metadata and make validations in files and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

## FILEEXISTS <a href="#fileexists" id="fileexists"></a>

Checks if a file exists in the virtual directory of the pipeline deployment.

### **Syntax**

```
FILEEXISTS(file)
```

* **file:** name of the file in the virtual directory of the pipeline

The function returns `true` when the file is found and `false` when it's not found.

## FILESIZE <a href="#filesize" id="filesize"></a>

Returns the size of a file in the virtual directory of the pipeline deployment.

### **Syntax**

```
FILESIZE(file)
```

* **file:** name of the file in the virtual directory of the pipeline

Let's say you need to obtain the size of the file created one step before the use of the _**File Writer**_ component. If its file name configuration in _**File Writer**_ was `file.txt`, then use the following extract in the _**JSON Generator**_ component:

```
{
"fileSize": {{ FILESIZE("arquivo.txt") }}
}
```

The result would be:

```
{"fileSize": 1000}
```

* **fileSize:** the size of the file (in bytes).

You can also read about these functions:

* [comparison](comparison-functions.md)
* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [date](date-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
* [math](math-functions.md)
