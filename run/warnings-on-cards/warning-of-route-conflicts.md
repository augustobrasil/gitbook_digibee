---
description: >-
  Learn how to proceed if these warnings are displayed in Run when a deployment
  needs to be made.
---

# Warning of route conflicts

When a pipeline is ready to be deployed, you need to take a number of actions, i.e., select the size, concurrent executions, and replicas. However, it is important to pay attention to the routes specified in the **API Routes** in **Build**.

This is because if a route is specified that already exists, conflicts will occur and deployment of the same routes will not be possible.

## Parameter route warning <a href="#h_60c3a95e2e" id="h_60c3a95e2e"></a>

After you have made the configurations for the deployment, the last step is to click on **Deploy**. But if the **Additional API Routes** selected in the **Build** phase start with a parameter, this results in an error because a route has not yet been created and must not start with a parameter.

As you can see, when you use **/:product**, the original path to access the pipeline will be substituted.

<figure><img src="../../.gitbook/assets/01 - Rotas.jpg" alt=""><figcaption></figcaption></figure>

So, in Run, if the parameters for a route are not established, the message below will appear informing you of this and the deployment will not be able to proceed.

<figure><img src="../../.gitbook/assets/02 - Mensagem.jpg" alt=""><figcaption></figcaption></figure>

The correct way is to add a new route that gets a parameter - for example, **/product/:id** to solve this error. [Learn more about customizing URLs here.](https://docs.digibee.com/documentation/platform/urls-system)

## Same route warning <a href="#h_d1cff5dbb2" id="h_d1cff5dbb2"></a>

Another warning that appears when a deployment is to be made but an error is found is when a route is used that already exists in a different pipeline.

As we can see in the example below, the **/conflict/route** has already been used in a pipeline called **123-run-routes-2**.

<figure><img src="../../.gitbook/assets/03 - API Routes.jpg" alt=""><figcaption></figcaption></figure>

But if we set the same route, **/conflict/route**, in another pipeline as shown below, the different pipelines will have identical URLs, so only one of them will be executed.

<figure><img src="../../.gitbook/assets/04 - Routes.jpg" alt=""><figcaption></figcaption></figure>

In Run, a warning before deployment informs that the route is already being used in another pipeline. So, you need to change the route in the **API Routes** in **Build** and then deploy it in Run.

<figure><img src="../../.gitbook/assets/05 - final Routes.jpg" alt=""><figcaption></figcaption></figure>

To avoid this, we suggest using a naming pattern, for requests as well. This also brings some advantages, that is, greater control and security for these types of triggers (REST, HTTP and HTTP File), additional routes give more flexibility to pipelines and the user avoids double work when using legacies with less flexibility in terms of URL.

