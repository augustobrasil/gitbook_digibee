---
description: Saiba mais sobre cada cápsula da coleção Totvs Live.
---

# Totvs Live

{% hint style="info" %}
Para acessar a coleção Totvs Live e usar as funcionalidades presentes nesse artigo, você precisa ter a permissão PIPELINE:CREATE. Aprenda mais na [documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
{% endhint %}

A coleção de cápsulas Totvs Live fornece recursos comumente utilizados em _pipelines_ para tornar sua construção mais produtiva. Abaixo você pode conhecer mais sobre cada cápsula da coleção.

## Consultar Status Ticket

Esta cápsula encapsula a chamada do método ConsultarStatusTicketLC\_Integracao na API do Totvs Live.

### Parâmetros de configuração da cápsula

* **ws-live-url:** url da instância do Totvs Live.

### Entrada

```
{
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "numeroTicket": "0999999999999999",
    "manter":"qualquer valor que queira manter na saída do conector"
}
```

### Saída

#### Sucesso

```
{
    "encontrouRegistros": true|false,
    "status": 200,
    "processStatus": "ERROR|PROCESSING|SUCCESS",
    "items": [],
    "numeroTicket"
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}​
```

Regras de _Process Status_:

* Se algum item está aguardando processamento: PROCESSING
* Se algum item está com erro, ou foi processado mas está com mensagem de erro, e não há nenhum item em processamento: ERROR
* Se algum item foi processado com erro inexistente e não está em processamento: SUCCESS

#### Erro

```
{
    "timestamp": 1559243275088,
    "error": "Não foi possível consultar ticket.",
    "code": 500,
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```

## Recuperar Lojas

Esta cápsula encapsula a chamada do método RecuperarLojasLC\_Integracao\_Xml na API do Totvs Live.

### Parâmetros de configuração da cápsula

* **ws-live-url:** url da instância do Totvs Live.

### Entrada

```
{
    "retornaTodasLojas": "true",
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "manter" "qualquer valor que queira manter na saida do conector"
}
```

### Saída

#### Sucesso

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

#### Erro

```
{
    "timestamp": 1559243275088,
    "error": "Não foi possível recuperar lojas.",
    "code": 500,
    "manter": "qualquer valor que tiver sido passado aqui será mantido"
}
```

## Recuperar Cliente

Esta cápsula encapsula a chamada do método RecuperarClienteLC\_Integracao na API do Totvs Live.

### Parâmetros de configuração da cápsula

* **ws-live-url:** url da instância do Totvs Live.

### Entrada

```
{
    "chaveAcesso":"00000000-00000000-00000000-00000000",
    "codigoSistemaSatelite":"000000000",
    "manter":"qualquer valor que queira manter na saida do conector"
}
```

### Saída

#### Sucesso

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
