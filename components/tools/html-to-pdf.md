---
description: >-
  Discover more about the HTML to PDF component and how to use it on the Digibee
  Integration Platform.
---

# HTML to PDF

**HTML to PDF** allows the creation of files in PDF format from a HTML. The component uses Apache FreeMaker templates to generate the HTML through the pipeline JSON message.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="322">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Name of the PDF file to be generated in the output of the component execution.</td><td>file.pdf</td><td>String</td></tr><tr><td><strong>Template (HTML)</strong> <code>(DB)</code></td><td>HTML template to be interpreted to generate the PDF file. This field supports the FreeMarker template.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Secured PDF</strong></td><td>If the option is activated, the insertion of a password in the PDF file is allowed to generate a protected document.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Password</strong> <code>(DB)</code></td><td>Password to protect the PDF file.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Custom permissions</strong></td><td>If the option is activated, custom permission options for the PDF file become available; otherwise, none of the following parameters will be available, and the PDF file will be generated with all the permissions.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Read only</strong></td><td>Access permission that defines the PDF file as "read-only". If the option is activated, all other access permissions will be deactivated.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Assemble document</strong></td><td>Allows pages to be added, rotated, or deleted from the file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Modify</strong></td><td>Allows the file to be modified.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Modify annotations</strong></td><td>Allows text notes to be added or modified in the file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Extract content</strong></td><td>Allows texts and images to be extracted from the file.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Extract for accessibility</strong></td><td>Allows texts and images to be extracted from the file for accessibility matters.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Print</strong></td><td>Allows the file to be printed.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Print degraded</strong></td><td>Allows the file to have degraded printing.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Fill in Form</strong></td><td>Allows forms to be filled with interactive fields.</td><td>False</td><td>Boolean</td></tr></tbody></table>

## Messages flow <a href="#h_7c1f8e27b4" id="h_7c1f8e27b4"></a>

### Input <a href="#h_14458ca32a" id="h_14458ca32a"></a>

The component accepts any input message, being able to use it through Double Braces.

### Output <a href="#h_d511c8c797" id="h_d511c8c797"></a>

* **Successful**

```
{  
    "success": true,  
    "fileName": "pdf_gerado.pdf" 
}
```

* **Unsuccessful**

```
{  
    "success": false,"message": "Could not generate the pdf file", 
    "error": "java.net.IOException"
}
```

### Example of request response with error <a href="#h_7760f928a2" id="h_7760f928a2"></a>

```
{  
    "success": false,  "message": "Could not generate the pdf file",  
    "error": "java.net.IOException:"
}
```

* **success:** `“false”` when the operation fails.
* **message:** message about the error.
* **exception:** information about the occurred error.

**Example:**

* **Body**

```html
<p>We have these animals:<table border=1>  
<#list animals as animal>    
<tr><td>${animal.name}<td>${animal.price} Euros  
</#list></table>
```

Therefore, in the input message an object array is received and it has the properties `“name”` and `“price”`:

```
[
    { "name": "Dog", "price": 100},
    { "name": "Cat", "price": 100},
    { "name": "Bird", "price": 30}
]
```

The template will make the iteration in this received array and fill the HTML:

```html
<p>We have these animals:<table border=1>
<tr><td>Dog<td>$100 Euros<tr><td>Cat<td>$100 Euros
<tr><td>Bird<td>$30 Euros 
</table>
```

## Other applications

### **SVG**

To use the SVG as HTML tag, apply the following property inside the SVG tag `xmlns="`[`http://www.w3.org/2000/svg`](http://www.w3.org/2000/svg)`"`:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="400" height="180">  
    <rect x="50" y="20" rx="20" ry="20" width="150" height="150" style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />  
    Sorry, your browser does not support inline SVG.
</svg>
```

### **CSS**

Versions after 2.1 aren't supported.

### **Images**

The use of images in base64 format inside HTML tags isn't supported.&#x20;

**Example:**

`<img src="data:image/png;base64, iVBORw0KGgoAAAANSUhEUgAA…>`

You can use images with local and remote reference:

#### **Local Image**

```html
<img src="image.jpg" alt="IMAGE2" >
```

In the example above, there must be a image file with the exact same name specified inside the src tag (image.jpg)

#### **Remote Image**

```html
<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" alt="IMAGE2" >
```

\
