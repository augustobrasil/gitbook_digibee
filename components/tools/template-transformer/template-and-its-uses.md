---
description: >-
  Users can learn useful validations and treatments which can be done with the
  Freemarker language when you use Template Transformer on the Digibee iPaaS.
---

# Template and its uses

Know some validations and treatments that can be done with the Freemarker language when you use **Template Transformer**. [To know more about this component, click here and read the article about it.](https://docs.digibee.com/documentation/components/tools/template-transformer)

For the examples you'll see next, consider this input JSON:

```
{
  "request": {
    "code": 213,
    "value": 4513423.1322,
    "description": "   test request   ",
    "items": [
      {
        "name": "item 1",
        "quantity": 2
      },
      {
        "name": "item 2",
        "quantity": 1
      }
    ]
  }
}

```

### LIST <a href="#list" id="list"></a>

Enables you to make iterations in an array (list) in JSON. Imagine this function in the creation of a dynamic elements list in the output, that transforms JSON into XML.

**Syntax**

```
<#list YourList of elements>
              block of information to be iterated.
</#list>
```

**Example**

Using the input informed in the beginning of this article, you can create a dynamic elements list using the template.

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">
<soap:Header/>
    <soap:Body>
        <web:request>
            <web:items>
                <#list items as item>
                    <web:item>
                        <web:nome>${item.name}</web:name>
                        <web:quantity>${item.quantity}</web:quantity>
                    </web:item>
                </#list>
            </web:items>
        </web:request>
    </soap:Body>
</soap:Envelope>

```

**XML output**

```xml
<soap:Envelope 	xmlns:soap="http://www.w3.org/2003/05/soap-envelope"	xmlns:web="http://www.webservicex.net/">
 <soap:Header/>    
 <soap:Body>        
  <web:request>            
    <web:items>                                    
     <web:item>                        
     	<web:name>item 1</web:name>                        
     	<web:quantity>2</web:quantity>                    
     </web:item>                    
     <web:item>                        
     	<web:name>item 2</web:name>                        
     	<web:quantity>1</web:quantity>                    
     </web:item>            
    </web:items>        
  </web:request>    
 </soap:Body>
</soap:Envelope>
```

{% hint style="info" %}
Remember that the **Template** output is an XML in a string.
{% endhint %}

### IF/ELSE <a href="#ifelse" id="ifelse"></a>

You can use this function to validate some information. Even when its fields are null or empty, there's no great impact on your data transformation.

**Syntax**

```xml
<#if condition>
             Block of information in case the condition in if is true.
<#elseif Syntax>
              Block of information in case the condition in elseif is true.
<#else>
              Block of information in case none of the conditions are taken.
</#if>

```

There's no limitation for the quantity of _elseif,_ and it's also possible to use just an _if_ without the _else_ - it all depends on your need.

**Example**

Using the input informed at the beginning of this article, you can create a validation in which the "code" field needs to be greater than 0 (zero).

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
    <soap:Header/>  
    <so ap:Body> 
       <web:request> 
           <web:code><#if code &gt; 0 >${code}</#if></web:code>
       </web:request> 
    </soap:Body> 
</soap:Envelope>
```

**XML output**\
If the condition is true:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
   <soap:Header/> 
       <soap:Body>     
          <web:request> 
              <web:code>213</web:code>  
          </web:request> 
       </soap:Body> 
</soap:Envelope>
```

If the conditions is false:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
   <soap:Header/> 
       <soap:Body>     
          <web:request> 
              <web:code></web:code>  
          </web:request> 
       </soap:Body> 
</soap:Envelope>
```

Did you know the use of the function isn't limited to simple conditions? You can also use expressions to validate if the field exists (??) or if it has content (has\_content).

**Syntax**

```xml
<#if yourField?? && yourField?has_content>
             Block of information if the field exists and has content.
<#else>
              Block of information if none of the conditions is taken.
</#if>
```

{% hint style="info" %}
It's possible to use logical operators for a more advanced condition.
{% endhint %}

_**&&**_ - for AND.

_**||**_ - for OR.

**Example**

Now see how to improve the validation so that the _if_ applied in the first case is used only if the "code" field exists and has content.

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
    <soap:Header/>  
    <so ap:Body> 
       <web:request>
          <#if code?? && code?has_content>
              <web:code><#if code gt 0 >${code}</#if></web:code>
          </#if>
       </web:request> 
    </soap:Body> 
</soap:Envelope>
```

**XML output**\
If the condition is true:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
   <soap:Header/> 
       <soap:Body>     
          <web:request> 
              <web:code>213</web:code>  
          </web:request> 
       </soap:Body> 
</soap:Envelope>
```

If the condition is false...

... and the "code" field has a value that is null, empty, or doesn't come in the input:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
   <soap:Header/> 
       <soap:Body>     
          <web:request> 
          </web:request> 
       </soap:Body> 
</soap:Envelope>
```

### TRIM <a href="#trim" id="trim"></a>

This function is used to remove the blank spaces at the beginning and in the end of a string.

**Syntax**

```json
${YourField?trim}
```

**Example**

Using the input informed at the beginning of this article, you can remove the blank spaces at the beginning and in the end of the "description" field".

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
    <soap:Header/>  
    <soap:Body> 
       <web:request> 
           <web:description>${description?trim}</web:description> 
       </web:request> 
    </soap:Body> 
</soap:Envelope>
```

**XML output**

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
    <soap:Header/> 
    <soap:Body>    
       <web:request> 
           <web:description>test request</web:description>    
       </web:request> 
    </soap:Body> 
</soap:Envelope>
```

### REPLACE <a href="#replace" id="replace"></a>

This function is used to replace a pre-established value in the field.

**Syntax**

```
${YourField?replace}

```

**Example**

Using the input informed at the beginning of this article, you can replace the "test" value in the description with "prod".

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/"> 
    <soap:Header/>  
    <soap:Body> 
       <web:request> 
           <web:description>${description?replace("test","prod")}</web:description> 
       </web:request> 
    </soap:Body> 
</soap:Envelope>
```

**XML output**

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">
     <soap:Header/>
     <soap:Body>
	   <web:request>
	       <web:description>   prod request   </web:description>
	   </web:request>
     </soap:Body>
</soap:Envelope>
```

### SLICE (SUBSTRING) <a href="#slice-substring" id="slice-substring"></a>

This function is used when the field must have a determined size.

**Syntax**

```
${YourField[0..9]} 0 = initial value9 = final value
```

**Example**

Using the input informed at the beginning of this article, you can determine for the field to have 10 characters only, even if it has a greater size.

{% hint style="info" %}
A good practice applicable to this function is to use IF/ELSE to validate the desired size for the field. That way, you avoid errors if the field is smaller than the established value.
{% endhint %}

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">
    <soap:Header/>
    <soap:Body>  
        <web:request>
            <#if description?length &lt; 10>       
                <web:description>${description}</web:description>
            <#else>
                <web:description>${description[0..9]}</web:description>
            </#if>
       </web:request>
    </soap:Body>
</soap:Envelope>
```

**XML output**

```xml
<soap:Envelope
    xmlns:soap="http://www.w3.org/2003/05/soap-envelope"
    xmlns:web="http://www.webservicex.net/">   
    <soap:Header/>   
    <soap:Body>         
         <web:request>                           
             <web:description>   request </web:description>      
         </web:request>   
    </soap:Body>
</soap:Envelope>
```

### LOCALE <a href="#locale" id="locale"></a>

This function is used in the template to set the location in a numeric value.

**Syntax**

```xml
<#setting locale="en_US">
${YourField}
<#setting locale="pt_BR">
${YourField}
```

To use it, you must provide the tag before the dynamic field. Check how to do it in the examples below.

**Example**

Using the input informed at the beginning of this article, you can format the value to be in the legacy system standard.

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">     
    <soap:Header/>
    <soap:Body>
        <web:request>
            <#setting locale="en_US">
            <web:value_US>${value}</web:value_US>
            <#setting locale="pt_BR">
            <web:value_BR>${value}</web:value_BR>
        </web:request>
    </soap:Body>
</soap:Envelope>
```

**XML output**

```xml
<soap:Envelope
	xmlns:soap="http://www.w3.org/2003/05/soap-envelope"
	xmlns:web="http://www.webservicex.net/"> 
	<soap:Header/>
	<soap:Body>       
		<web:request>                        
			<web:value_US>4,513,423.13</web:value_US>
			<web:value_BR>4.513.423,13</web:value_BR>   
		</web:request>    
	</soap:Body>
</soap:Envelope>
```

### Custom <a href="#custom" id="custom"></a>

If the desired format isn't accepted by your system, you can define the necessary number for formatting through the _"_number\_format" tag. It allows you to customize the number formatting.

**Syntax**

```xml
<#setting number_format="0.##">
${yourField}
```

{% hint style="info" %}
The hashtags (#) define the quantity of decimal places to be used.
{% endhint %}

**Example**

Using the input informed at the beginning of this article, you can format the value to be in the legacy system standard.

What you must inform in the template is:

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">     
    <soap:Header/>
    <soap:Body>
        <web:request>
            <#setting number_format="0.#">
            <web:custom_value>${value}</web:custom_value>
            <#setting locale="pt_BR">
        </web:request>
    </soap:Body>
</soap:Envelope>

```

**XML output**

```xml
<soap:Envelope  xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:web="http://www.webservicex.net/">  
     <soap:Header/> 
     <soap:Body>     
          <web:request>                     
	       <web:custom_value>4513423.1</web:custom_value>     
	  </web:request> 
     </soap:Body> 
</soap:Envelope>
```

\
