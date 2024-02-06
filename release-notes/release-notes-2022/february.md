---
description: >-
  February 2022 updates on any recent changes, feature enhancements, or bug
  fixes for the Digibee iPaaS.
---

# February

## Release Notes 02-17-2022

#### **COMPONENTS**

* **JWT:** We’ve added a parameter to the JWS component. By activating the Custom Claim Specification toggle it will be possible to create claims in JWS using dynamic JSONs.

Read the full article about [JWT component configuration parameters here](../../components/security-components/jwt-deprecated.md).

* **FTP**: Now, it will be possible to enable or disable the verification in which the remote host (that is part of a data connection) is the same host is the same host the control connection is connected to when FTP Security is active.

Read the full article about [FTP component configuration parameters here](../../components/file-storage/ftp.md).

We’ve also fixed a few bugs:

* **Parallel component:** We’ve fixed the bug that occurred when trying to run a pipeline containing Parallel components inside another Parallel (several nested levels) resulting in the executionId labels being displayed incorrectly to all executions, even if this didn’t affect each and every one of them.
* **JWT component:** We’ve fixed the problem that prevented the use of metacharacters such as \n, \r e \t in the specification of claims.
* **HTTP-File trigger:** We’ve fixed the problem in which the HTTP-Trigger would ignore request-size-limit values above 5 MB.
* **User roles:** We’ve fixed how the description of specific permissions is shown in User Roles.
* **Projects**: We’ve fixed the error that allowed a user to select a pipeline and move it from one project to another even without permissions.

## Release Notes 02-01-2022

#### **PIPELINES' HISTORY VERSION (BETA)**

Now, when opening a pipeline’s minor version, it’s possible to see the Trigger’s settings that were deployed in that version.

Read the full article [about the pipelines' history version here](../../build/pipelines/pipelines-version-history.md).

IMPORTANT: the feature is in its Beta phase and your feedback is very important to us.

Learn more [about the Beta program here](../../general/beta-program.md).

#### **\{{ DOUBLE BRACES \}} FUNCTIONS**

* FORMATNUMBER: we’ve improved the precision points of fluctuation by adding the string format at the function’s input.\
  It’s also possible to choose between different types of number rounders. They are: Rounding Mode: UP, DOWN, CEILING, FLOOR, HALF\_UP, HALF\_DOWN and HALF\_EVEN.\
  \
  Read the full [article about Double Braces - Numeric Functions here](../../build/double-braces/double-braces-functions/numerical-functions.md).\


We’ve also fixed a few bugs:

* **Globals:** we’ve fixed the error that occurred when creating or editing a new Global and the form would display information about the last edited or created Global.\

* **Projects:** we’ve fixed the bug that occurred when creating a new major version of a pipeline, causing it to be created at the default project instead of at the project where the original pipeline was located.\

* **REST V2 component:** we’ve fixed the error that prevented the component from invoking AWS Lambda type services.

