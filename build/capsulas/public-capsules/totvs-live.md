---
description: Learn more about each capsule of the Totvs Live collection.
---

# Totvs Live

{% hint style="info" %}
To access the Totvs Live collection and use the features presented in this article, you need the permission PIPELINE:CREATE. Learn more in the [documentation about Roles](https://docs.digibee.com/documentation/administration/new-access-control/access-control-roles).
{% endhint %}

The Totvs Live collection of capsules provides resources commonly used in pipelines to make their construction more productive. Below you can learn more about each capsule in the collection.

## Query Ticket Status

This capsule encapsulates the ConsultarStatusTicketLC\_Integracao method call into Totvs Live API.

### Capsule configuration parameters

* **ws-live-url:** Totvs Live instance url.

### Input

```
{
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "numeroTicket": "0999999999999999",
    "manter":"any value you want to keep in the output of the component"
}

```

### Output

#### Success

```
{
    "encontrouRegistros": true|false,
    "status": 200,
    "processStatus": "ERROR|PROCESSING|SUCCESS",
    "items": [],
    "numeroTicket"
    "manter": "any value entered in this field will be retained"
}
```

Process Status rules:

* If an item is waiting to be processed: PROCESSING
* If an item has an error, or has been processed but had an error message, and no item is being processed: ERROR
* If an item has been processed with a non-existent error and is not being processed: SUCCESS

#### Error

```
{
    "timestamp": 1559243275088,
    "error": "Não foi possível consultar ticket.",
    "code": 500,
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}

```

## Retrieve Stores

This capsule encapsulates the RecuperarLojasLC\_Integracao\_Xml method call at Totvs Live API.

### Capsule configuration parameters

* **ws-live-url:** Totvs Live instance url.

### Input

```
{
    "retornaTodasLojas": "true",
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "manter" "qualquer valor que queira manter na saida do conector"
}
```

### Output

#### Success

```
{
    "encontrouRegistros": true,
    "status": 200,
    "data": 30052019,
    "hora": 191120,
    "codigoSistemaSatelite": 999999999,
    "numeroTicketSaida": 999999999999,
    "lojas": [],
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```

#### Error

```
{
"timestamp": 1559243275088,
"error": "Não foi possível recuperar lojas.",
"code": 500,
"manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```

## Retrieve Customer

This capsule encapsulates the RecuperarClienteLC\_Integracao method call at Totvs Live API.

### Capsule configuration parameters

* **ws-live-url:** Totvs Live instance url.

### Input

```
{
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "manter":"qualquer valor que queira manter na saida do conector"
}
```

### Output

#### Success

```
{
    "encontrouRegistros": false,
    "status": 200,
    "data": "5/30/2019",
    "hora": "4:04 PM",
    "numeroTicketSaida": 999999999999,
    "codigoSistemaSatelite": 999999999,
    "clientes": [],
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```

#### Error

```
{
    "timestamp": 1559243275088,
    "error": "Não foi possível recuperar clientes.",
    "code": 500,
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```
