---
description: >-
  Learn the supported usage scenarios when using File Reader and File Writer in
  the Digibee Integration Platform.
---

# How to read and write files inside a folder

Take a look at the supported usage scenarios below. For more information about each component, its parameters and operations, see the [**File Reader**](file-reader.md) and [**File Writer**](file-writer.md) documentation.

### Scenario 1: reading a file inside a folder

Let's say you have a file named "file.txt" inside "folder", available in your pipeline.\
To read this file inside a folder, you may use a **File Reader** that indicates the path "folder/file.txt". That way, you can access the file 'file.txt'.

Follow the steps below to learn how to do it:



<figure><img src="../../.gitbook/assets/How to file reader 31 oct.png" alt=""><figcaption></figcaption></figure>

1. Create a pipeline and add a **File Reader**.
2. Open the configuration form of the component.
3. Define the **File Name** parameter as "folder/file.txt".
4. Click on **Confirm** to save the component settings.
5. Connect the trigger with **File Reader**_._
6. Run a test in the pipeline (CTRL + ENTER).

The result will be shown:

```
{
  "data": [
    "my sample content"
  ],
  "fileName": "folder/file.txt",
  "lineCount": 1
}
```

* **data:** array with the content of the file read by **File Reader**_._
* **fileName:** shows the complete path of the read file.
* **lineCount:** identifies the amount of lines within the file read by **File Reader**_._

### &#x20;**Scenario 2: Writing a file inside a folder**

Let's say you have a file named "file.txt" inside "folder", available in your pipeline. To write this file inside a folder, you may use a **File Writer** that indicates the path "folder/file.txt". That way, you can access the file "file.txt".

Check how to do that:



<figure><img src="../../.gitbook/assets/How to file writer 31 oct.png" alt=""><figcaption></figcaption></figure>

1. Create a pipeline and add a **File Writer**.
2. Open the configuration form of the component.
3. Define the **File Name** parameter as "folder/file.txt".
4. Define the **Data** parameter as `{{ message.data }}`_._\
   Mind we're using the Double Braces expression_:_ `{{ message.data }}` to access the result of the last component. In this case, we access `data` with the content of the file to be written.
5. Click on **Confirm** to save the component settings.
6. Connect the trigger with the **File Writer**.
7. Run a test in the pipeline (CTRL + ENTER).

The result will be shown:

```
{
 "fileName": "folder/file.txt",
 "success": true
}
```

* **fileName:** shows the complete path of the written file.
* **success:** when the result is "true", it indicates that the execution was successful.
