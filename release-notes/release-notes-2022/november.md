---
description: >-
  November 2022 updates on any recent changes, feature enhancements, or bug
  fixes for the Digibee iPaaS.
---

# November

## Release notes 11-08-2022

### **SUBSCRIPTION PAGE**

Now, customers under the Subscription-based model can easily track the usage of the Pipeline subscriptions and RTUs available in their realm. Go to Settings and access the Subscription side panel to visualize the consumption under My usage.

### **PIPELINE LOGS**

Using the new buttons we’ve added, you can now clear search parameters or copy the pipeline name or pipeline key for each displayed log with a single click. Also, blank spaces are now ignored when searching on this page.\
\\

\\

We’ve also fixed a few bugs:

* **Pipeline Executor:** we’ve fixed a bug that limited Pipeline Executor's thread pool performance to cover all deploy sizes: small, medium and large. It’s important to redeploy the current pipelines that have the Pipeline Executor to implement this fix.
* **Pipeline history:** we’ve fixed the bug that prevented the user from archiving an old version of the pipeline from the pipeline's version history page.
* **New Canvas (restricted beta):** we’ve fixed the bug that displayed an error message and prevented the user from copying and pasting a structure and then saving the pipeline.
* **Capsules on the new Canvas (restricted beta):** we’ve fixed the bug that prevented users from visualizing Capsules information when used within a pipeline on the new Canvas.
* **License terms:** we’ve fixed the bug that prevented the license term from being displayed to the user.
