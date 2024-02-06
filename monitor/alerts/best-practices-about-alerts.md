---
description: Learn best practices for using alerts, including naming conventions.
---

# Best practices about alerts

## What are the best practices

Best practices are tips to help you organize and understand your alerts. The alert list displays information such as the name of the alert, the pipeline, and the status. However, when alerts are received, only the name is displayed. If you follow the guidelines for naming alerts, you can identify the type of alert more quickly.

## Best practices on naming alerts

When creating alerts, include the following information in the alert name:

* Name of the realm
* Name of the pipeline (as one word)
* Metric type (only the first letters, for example, “MIQ” for “Messages In Queue”)
* Pipeline environment (test or prod)
* Pipeline version&#x20;
* Severity of the alert (low, medium, or high)

{% hint style="info" %}
Separate each item using only hyphens ( - ). No other characters are allowed.
{% endhint %}

See below how the structure should look like and a practical example:

**Structure:** realm-pipeline-metric-environment-version-severity

**Example:** digibee-projectxyz-MIQ-prod-v1-medium
