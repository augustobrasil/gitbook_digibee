---
description: >-
  Discover more about the SAP component and how to use it on the Digibee
  Integration Platform.
---

# SAP

**SAP** enables SAP connection (RFC only) for requirements dispatch.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

| Parameter                                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Default value | Data type |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | --------- |
| **Account**                                                                                       | It's necessary to create a BASIC-type account to use the SAP credentials (user and password).                                                                                                                                                                                                                                                                                                                                                                                                           | N/A           | String    |
| **SAP Operation**                                                                                 | Connection method in SAP - the component supports access via RFC or IDOC.                                                                                                                                                                                                                                                                                                                                                                                                                               | RFC           | String    |
| **IDOC Type**                                                                                     | Specifies the Basic IDOC Type of an IDOC.                                                                                                                                                                                                                                                                                                                                                                                                                                                               | N/A           | String    |
| **IDOC Type Extension**                                                                           | Specifies the IDOC Type Extension of an IDOC.                                                                                                                                                                                                                                                                                                                                                                                                                                                           | N/A           | String    |
| **System Release**                                                                                | Specifies the associated SAP Basis Release of an IDOC.                                                                                                                                                                                                                                                                                                                                                                                                                                                  | N/A           | String    |
| **Application Release**                                                                           | Specifies the associated Application Release of an IDOC.                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A           | String    |
| **Host**                                                                                          | <p>Hostname of the SAP system - for "IP" and "Port" to be supported, it's necessary to have connectivity via VPN (you can define VPN through SAP GUI). <br><br>To resolve the hostname to an IP address, you must add a mapping entry to the host file of the machine on which the agent is installed.</p>                                                                                                                                                                                              | N/A           | String    |
| **RFC**                                                                                           | Name of the RFC used to connect with the SAP system - this field is informed by the client (the import parameters of the SAP funtion must be mapped).                                                                                                                                                                                                                                                                                                                                                   | N/A           | String    |
| **Language**                                                                                      | Language to be used in the connection with the SAP system (ex.: "EN" for English).                                                                                                                                                                                                                                                                                                                                                                                                                      | en            | String    |
| **Client ID**                                                                                     | SAP Client ID, normally with 3 digits, used to connect with SAP.                                                                                                                                                                                                                                                                                                                                                                                                                                        | 400           | String    |
| **System Number**                                                                                 | <p>Normally with 2 digits, used to connect with the SAP system <br><br>(you can find this information in SAP GUI).</p>                                                                                                                                                                                                                                                                                                                                                                                  | 01            | Integer   |
| **Send as File**                                                                                  | If this option is enabled, a file can be defined and sent.                                                                                                                                                                                                                                                                                                                                                                                                                                              | False         | Boolean   |
| **File Name**                                                                                     | <p>File that contains the body to be sent to SAP server. Using this capacity is recommended in situations where the content is too large to be sent via the Template field. <br><br>Use other components such as <a href="https://docs.digibee.com/documentation/components/tools/template-transformer"><strong>Template Transformer</strong></a> and <a href="https://docs.digibee.com/documentation/components/files/file-writer"><strong>File Writer</strong></a> to write the intended content.</p> | N/A           | String    |
| **Template (XML)**                                                                                | Template Apache FreeMarker for the SOAP message sent in the request.                                                                                                                                                                                                                                                                                                                                                                                                                                    | N/A           | String    |
| **Fail On Error**                                                                                 | If the option is enabled, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.                                                                                                                                                                                                                                                                                                  | False         | Boolean   |
| **Use Dynamic Account** [**(Beta)**](https://docs.digibee.com/documentation/general/beta-program) | <p>When the option is active, the component will use the account dynamically. <br><br>When deactivated, it will use the account statically.</p>                                                                                                                                                                                                                                                                                                                                                         | False         | Boolean   |
| **Account Name** [**(Beta)**](https://docs.digibee.com/documentation/general/beta-program)        | Account name to be set. The name of the account is generated dynamically via the [**Store Account**](https://docs.digibee.com/documentation/components/tools/store-account) component.                                                                                                                                                                                                                                                                                                                  | N/A           | String    |
| **Scoped** [**(Beta)**](https://docs.digibee.com/documentation/general/beta-program)              | <p>When the option is active, the stored account is isolated to other sub-process. In that case, sub-processes will see their own version of the stored account data. <br><br>To know more about the <strong>Scoped</strong> feature, check out the <a href="https://docs.digibee.com/documentation/platform/pipeline-engine/support-dynamic-accounts-restricted-beta">Dynamic Accounts documentation</a>.</p>                                                                                          | False         | Boolean   |

{% hint style="info" %}
Pay attention to the maximum file size for each deploy type in a pipeline with the SAP component only. Note that these values can change if the pipeline contains other components:\
\
**Small:** 10 MB

**Medium**: 28 MB

**Large:** 67 MB
{% endhint %}

## Use recommendation <a href="#use-recommendation" id="use-recommendation"></a>

We recommend you to set Globals for the SAP environment, as shown below:

* Globals:
* environment = SAP environment  &#x20;

See the examples of the items listed, that must be replaced according to your need:

* \[rfc] = RFC name
* \[table] = Table related to RFC
* \[columns] = Table columns

Read the [article](https://docs.digibee.com/documentation/build/capsulas/public-capsules/sap-collection#h\_16dfe961b3) for more information about connectivity related to SAP.&#x20;

### Component structure for RFC connections <a href="#component-structure-for-rfc-connections" id="component-structure-for-rfc-connections"></a>

For RFC connections, use the "**SAP Json to RFC**" capsule before the SAP component. That way, the call is transformed in the format expected by SAP. This is an example of RFC call syntax inside SAP:

_**Function call (RFC) BAPI\_BUPA\_ADDRESS\_GETDETAIL inside JSON Generator component**_

```
{
  "sid": "{{sap-test-sid}}", 
  "rfc": "BAPI_BUPA_ADDRESS_GETDETAIL", 
  "importParameters": { 
    "attributes": { 
      "BUSINESSPARTNER": {{ message.BUSINESSPARTNER }}, 
      "VALID_DATE": {{FORMATDATE(NOW(), "timestamp", "yyyy-MM-dd", null , "GMT-3") }} 
    } 
  } 
}
```

For a RFC call, it's important to pay attention to the following points:

* Always inform Sid - field Enviroment/SystemName/System Id previously mentioned.
* RFC field - can be in the JSON file, as well as informed inside the component.&#x20;
* ImportParameters - function call inside SAP. Be specific only with the fields that must be filled out in the call.

### About SAP Intermediate Document (IDOC)             <a href="#about-sap-idoc" id="about-sap-idoc"></a>

* **IDOC Type:** has a specific structure, that put into sequence the data transfered from one system to another.
* **IDOC TYPE EXTENSION (optional):** specifies the IDOC extension, if it exists, of an IDOC produced by this endpoint.
* **SYSTEM RELEASE (optional):** specifies the SAP Basis Release associated, if it exists, to an IDOC produced by this endpoint.
* **APPLICATION RELEASE (optional):** specifies the Application Release associated, if it exists, to an IDOC produced by this endpoint.&#x20;

{% hint style="info" %}
Keep in mind that IDOCs are processed asynchronously via SAP. When an IDOC is sent, it does not indicate whether it was successful or not. In case of failure, the user must process the IDOC again.
{% endhint %}

### **Component structure for the use of the Template XML field**    &#x20;

See an example of template (XML):

```
<?xml version="1.0" encoding="ASCII"?> 
<idoc:Document 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:FLCUSTOMER_CREATEFROMDATA01---="http://sap.fusesource.org/idoc/{_YOUR_ENVIRONMENT_}/FLCUSTOMER_CREATEFROMDATA01///" 
    xmlns:idoc="http://sap.fusesource.org/idoc" 
    creationDate="2015-01-28T12:39:13.980-0500" 
    creationTime="2015-01-28T12:39:13.980-0500" 
    iDocType="FLCUSTOMER_CREATEFROMDATA01" 
    iDocTypeExtension="" 
    messageType="FLCUSTOMER_CREATEFROMDATA" 
    recipientPartnerNumber="QUICKCLNT" 
    recipientPartnerType="LS" 
    senderPartnerNumber="QUICKSTART" 
    senderPartnerType="LS"> 
  <rootSegment xsi:type="FLCUSTOMER_CREATEFROMDATA01---:ROOT" document="/">
    <segmentChildren parent="//@rootSegment"> 
      <E1SCU_CRE parent="//@rootSegment" document="/"> 
        <segmentChildren parent="//@rootSegment/@segmentChildren/@E1SCU_CRE.0"> 
          <E1BPSCUNEW parent="//@rootSegment/@segmentChildren/@E1SCU_CRE.0" 
              document="/" 
              CUSTNAME="Fred Flintstone" FORM="Mr." 
              STREET="123 Rubble Lane" 
              POSTCODE="01234" 
              CITY="Bedrock" 
              COUNTR="US" 
              PHONE="800-555-1212" 
              EMAIL="fred@bedrock.com"
              CUSTTYPE="P" 
              DISCOUNT="005" 
              LANGU="E"/> 
        </segmentChildren> 
      </E1SCU_CRE> 
    </segmentChildren> 
  </rootSegment> 
</idoc:Document>  
```

{% hint style="warning" %}
{_YOUR\_ENVIRONMENT_} must be replaced by your SAP SID.
{% endhint %}

\
If it's a single query, you can use the following syntax:

**Elementary fields/Import Parameters**

```
<?xml version="1.0" encoding="ASCII"?> 
<[rfc]:Request xmlns:[rfc]="http://sap.fusesource.org/rfc/{{global.environment}}/[rfc]" 
  [columns]="20180801" 
  [columns]="20180806" 
  [columns]="050" />
```

**Example:**

```
<?xml version="1.0" encoding="ASCII"?> 
<ABCD_RFC_ORDEM_FATURA:Request 
    xmlns:ABCD_RFC_ORDEM_FATURA="http://sap.fusesource.org/rfc/QAS/ABCD_RFC_ORDEM_FATURA" 
    P_ERDAT_INI="2018-07-01T00:00:00.000" 
    P_ERDAT_FIM="2018-08-01T00:00:00.000" 
    CLIENTE="" 
    VKORG="0010" 
    AUART="" /> 

```

If it's a table query, use this syntax: &#x20;

**Table fields**

```
<?xml version="1.0" encoding="ASCII"?> 
<[rfc]:Request ">xmlns:[rfc]="http://sap.fusesource.org/rfc/{{global.environment}}/[rfc]"> 
 <[table]> 
  <row> 
   <[columns]>${VBELN}</[columns]> 
   <[columns]>${ABDC}</[columns]> 
  </row> 
 </[table]> 
</[rfc]:Request> 
```

**Example:**

```
<?xml version="1.0" encoding="ASCII"?> 
<ABCD_RFC_MATERIAIS:Request ">xmlns:ABCD_RFC_MATERIAIS:Request="http://sap.fusesource.org/rfc/{{global.environment}}/ABCD_RFC_MATERIAIS:Request"> 
 <T_TIPO> 
  <row> 
   <MTART>${type}</MTART> 
  </row> 
 </T_TIPO> 
</ABCD_RFC_MATERIAIS:Request>
```

**Input**

```
{  
    "body":{     
        "type": "S"   
    } 
}
```

* **${type}:** variable that must be provided inside a tag "body"

For the variable _sapRequestTemplate_, it's important to pay attention to these points:

* the variable name can have the following signs: minus (-), period (.) and colon (:) in any position. But these characters need to be escaped with backslash (\\). Otherwise, they'll be interpreted as operators.
* it might be more convenient to use variables and conversion functions:

```
<#assign x=42>
${x}
${x?string} <#-- the same as ${x} -->
${x?string.number}
${x?string.currency}
${x?string.percent}
${x?string.computer}
```

&#x20;  \
**Output**

```
42
42
42
$42.00
4,200%
42
```

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

#### Input <a href="#input" id="input"></a>

The component expects a message under any format. However, it will look for a path inside the "modelPath" configuration property.

#### Output <a href="#output" id="output"></a>

The output message will be the same as the input message, but replacing the model property according to the template definition (as a string). If there's an error, the "property\_error" property will be created on the same level of the original property.
