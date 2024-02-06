---
description: >-
  Learn the two pipeline versions used, major versioning (main version), and
  minor versioning (secondary version).
---

# Pipeline versioning

A pipeline uses a two-level versioning system. **Example:** v.1.2, Major = 1, Minor = 2. The first number in a version refers to its Major versioning - informally knowns as "main version". The second number refers to its Minor versioning - informally known as "secondary version''.

### Majors

Major versions are the main versions of a pipeline. The versioning system makes it possible to create new Major versions without modifying previously generated Major versions. Each Major version has its own history, including all Minor versions associated with it.

For a new Major version to be created, you must perform the procedure manually from an existing Major version. To do this, click on “New version” → “New Major version” on the pipeline card.

{% hint style="info" %}
**Note:** Major versions allow simultaneous deployments.
{% endhint %}

### Minors

Minor versions are secondary versions of a pipeline. These versions contain changes made to the same Major version.

By default, whenever a pipeline is modified and saved, Digibee Integration Platform automatically creates a new Minor version.

**Example:** If you deploy the last Minor version of a pipeline and change it later, another Minor version is created so that the deployed version is preserved.

{% hint style="info" %}
**Note:** Minor versions do not allow simultaneous deployments.
{% endhint %}
