---
description: >-
  Discover how you can efficiently manage the integration flow with the
  Transformer (JOLT) component and the "IF-ELSE" logic of JOLT.
---

# IF - ELSE simple with JOLT

Upon performing a TO-FROM to an integration flow, it is very common to need to complete a field on the TO side that does not have its direct correspondent on the FROM side.

However, in some cases, this kind of problem can be solved with a simple "IF-ELSE", from the data coming from the FROM side.

### Example

Let’s suppose that we have a JSON with the client's data:

```
{ 
   "client": {   
       "name": "Sample client",   
       "age": "32",   
       "maritalStatus": "Single",   
       "country": "Brazil" 
   }
}
```

From the above JSON, we need to create a new JSON containing only the client's **Name** and **Citizenship**:

```
{
 "client" : {
   "name" : "Sample client",
   "citizenship" : "Brazilian"
 }
}
```

For the **Citizenship** field, only 2 values are accepted:

* **Brazilian**
* **Foreigner**

However, the first client's JSON doesn’t have a **Citizenship** field; it only tells us the client's country of origin.

In this case, we manage to establish the client's citizenship from his country of origin.

Below, there is a simple way of settling this situation, only using a **Transformer (JOLT)** component.

### Transformation and "IF-ELSE" with JOLT

```
[
 {
   "operation": "shift",
   "spec": {
     "client": {
       "name": "client.name",
       "country": {
         "Brazil": {
           "#Brazilian": "client.citizenship"
         },
         "*": {
           "#Foreigner": "client.citizenship"
         }
       }
     }
   }
 }
]
```

On the above transformation, we use the same **IF-ELSE** principle to check the "country" value.

If it is "Brazil", we complete the "citizenship" field with the "Brazilian" value.

If the "country" value is a country other than "Brazil", we complete the "citizenship" field with the "Foreigner" value.

### Final JSON with client's Name and Citizenship

```
{
 "client" : {
   "name" : "Sample client",
   "citizenship" : "Brazilian"
 }
}
```

\
