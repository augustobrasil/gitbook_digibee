---
description: Know the component and how to use it.
---

# HL7 (Restricted Beta)

{% hint style="info" %}
Currently, this feature is in [restricted beta](../../general/beta-program.md) phase and is only available to specific customers.
{% endhint %}

**HL7** component sends information to healthcare systems via the HL7 ([Health Level 7](https://info.hl7.org/orientation-station)) communications protocol, a healthcare industry standard for exchanging data between different systems and medical devices.

Take a look at the configuration parameters of the component:

* **Host:** HL7 server host.
* **Port:** HL7 server port. MLLP protocol usually runs under port 2575.
* **Connect Timeout (ms):** time limit for the connection of the platform to the server (in milliseconds).
* **HL7 Message:** message field that contains the data to be used. This field supports Double Braces expressions.
* **HL7 Message Charset:** charset for the HL7 message.
* **Advanced Settings:** if the option is active, you can access the following configurations:
  * **Connection Pool:** number of available connection pools.
  * **Enable Retries:** if the option is active, it will allow retries if the execution fails.
  * **Number of Retries:** defines the number of retries if the execution fails.
  * **Time to Wait Between Retries (in ms):** defines the time interval between retries (in milliseconds).
* **Fail on Error:** if the option is active, the execution of the pipeline with error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.

## Messages flow

### Output

When executing a HL7 component, the following JSON structure will be generated:

```
{
	"success":true,
	"exitCode":200
}
```

* **success:** if “true”, the operation has been successfully executed; if “false”, the operation failed.
* **exitcode:** exit code.
