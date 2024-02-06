---
description: See some examples of use of this component.
---

# Digibee JWT (Generate and Decode) implementation

The most common use of JWT happens during the authorization of a service exposed in the web via HTTP protocol.

With this step-by-step about the use of JWT token, you can also customize the security in your next pipelines. [To know the Digibee JWT (Generate and Decode) component a little bit better, click here.](https://docs.digibee.com/documentation/components/security-components/digibee-jwt)

Now, see the following illustration, that shows the shape and the architecture of the pattern:

![](<../../../.gitbook/assets/implementação jwt.png>)

To access the services, it's necessary to make the login in a pipeline, which will be responsible for the JWT token generation. With this token at hand, you have access to the paths, services and allowed resources.

Did you know you can also use the pattern inside the Platform to reassure the security of the flows? Check out how.

## Building a pipeline to make login and construct JWT <a href="#building-a-pipeline-to-make-login-and-construct-jwt" id="building-a-pipeline-to-make-login-and-construct-jwt"></a>

The first step is to configure the trigger for login:

* go into the trigger configurations and select the option REST;
* activate the options **External API** and **API Key.**

If you have any doubts on how to fill in the fields mentioned above, [click here to read our article about the REST Trigger.](https://docs.digibee.com/documentation/components/triggers/rest-trigger)

With the configured trigger, you can build the flow by using the necessary components for the token creation. But don't worry - there's a specific component that generates the JWT token. This is how you do it:

* drag the **Digibee JWT (Generate and Decode)** icon to your building area;
* select the **Generate** Operation to create the token;
* in Scopes and Expiration fields, apply the rules that better suit your business.

## **Using Assert** <a href="#using-assert" id="using-assert"></a>

To use the **Assert** component to create a validation per user and predefined password in the Platform, insert the following code in the CONDITION field:

```
#{body.user} == #{globals.user} && #{body.password} == #{globals.password}
```

{% hint style="info" %}
**Important:** the JWT token generation isn't made under Execution panel. This is only possible when the pipeline is published in some of the environments (Test or Prod).
{% endhint %}

## Calling the pipeline for login <a href="#calling-the-pipeline-for-login" id="calling-the-pipeline-for-login"></a>

After you get done with the configurations, it's necessary to implement the pipeline in its corresponding test or production environment to test the flow. If you have any other specific doubts on pipelines implantation in the Platform, [click here to read our article about it.](https://docs.digibee.com/documentation/build/pipelines)

Remember that all the implemented flows in Digibee with REST or HTTP triggers (and its derivatives) must use API Key. It's not different for the login.&#x20;

With the configured API Key, you can start the test. See, in the example below, how to do that using postman. But keep in mind: you can use the client you're used to or any other application you might prefer.

This is what you must do:

* provide the API Key in the call header;
* provide the user and the password configured as mandatory in the flow.

![](<../../../.gitbook/assets/jwt implemantation1.png>)

When making this call, the service return the status of success:

![](<../../../.gitbook/assets/jwt implementation2.png>)

Look for the necessary information in the headers of the response, in the Authorization field - this is the authentication, which means, the generated JWT to be used in combination with the API Key for the other flows that use the API REST and HTTP triggers.

## Configuring the trigger for the flows with the new authentication as key <a href="#configuring-the-trigger-for-the-flows-with-the-new-authentication-as-key" id="configuring-the-trigger-for-the-flows-with-the-new-authentication-as-key"></a>

Start making necessary configurations in the trigger. For that, activate the ExternalAPI, API Key and Token JWT options. That way, every time the paths are called, you'll have to inform the generated API Key and JWT token.

If you inform the API Key, but don't inform the token, then an authorization error is returned:

![](<../../../.gitbook/assets/jwt implementation3 (1).png>)
