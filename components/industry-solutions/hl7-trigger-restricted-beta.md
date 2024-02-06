---
description: Know the trigger and how to use it.
---

# HL7 Trigger (Restricted Beta)

{% hint style="info" %}
This feature is currently in restricted beta phase and is only available to specific customers.
{% endhint %}

**HL7 Trigger** receives messages in HL7 format from healthcare systems to the Digibee Integration Platform. The HL7 ([Health Level 7](https://info.hl7.org/orientation-station)) communications protocol is used in the healthcare industry for exchanging data between different systems and medical devices. You can also [learn more about the **HL7 component** in our documentation](https://docs.digibee.com/documentation/components/industry-solutions/hl7-beta-restricted).

Take a look at the configuration parameters of the trigger:

* **HL7 Pipeline Name:** name of the pipeline.
* **HL7 Message Charset:** charset for the HL7 message received by the trigger.
* **Maximum Timeout (in ms):** time limit before expiration, in milliseconds.&#x20;
* **Filter from Header (MSH-3):** value from a specific header. This field is mandatory and currently only allows MSH-3 headers.

## HL7 Trigger in action

### Output

```
{
  "body": "<CONTEUDO_DA_MSG_HL7>"
}

```

Message example (anonymized):

{% code overflow="wrap" %}
```
{
  "body": "MSH|^~\\&|TESTE|SFCT|RAPP|RFCT|20080312181835||ADT^A01|0D23ACC3-17CD-4FF4-BE66-AD4A6572079E|P|2.4\rEVN|A01|20080312181835\rPID|1||722347^^^^MR||PATIENT^TEST||19581221|F|||HIGH STREET 91^^SAINT PAUL^MN^55175^USA||(123)456-78-90^^PH|(844)955-17-21^^PH\rPV1|1|I|P166^R8^B4|R|||728625^WRIGHT^AMANDA^^MD^DR\rDG1|1|I9|472|CHRONIC PHARYNGITIS AND NASOPHARYNGITIS||A"
}

```
{% endcode %}
