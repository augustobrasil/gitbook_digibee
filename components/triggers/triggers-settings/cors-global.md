---
description: Saiba mais sobre CORS para triggers HTTP, HTTP File e REST.
---

# CORS - Configuração Global

O Cross-Origin Resource Sharing (CORS) é um mecanismo que permite informar ao navegador quais origens tem a permissão para fazer requisições ao servidor. Na Digibee Integration Platform, temos a opção de configurar os parâmetros do CORS de forma global. Ao configurar CORS globalmente, todas as _triggers_ que conversam utilizando o protocolo HTTP vão utilizar essas configurações e retornar os _headers_ de resposta conforme a especificação do CORS. Abaixo são exemplos da configuração de CORS.

```
"Access-Control-Allow-origin":"meudominio1.com,meudominio2.com",
        "Access-Control-Allow-Methods": "GET,POST,DELETE",
        "Access-Control-Allow-Headers": "Authorization,x-digibe-custom-header ",
        "Access-Control-Expose-Headers": "x-digibe-custom-header",
        "Access-Control-Allow-Credentials": "true"
 
```

### **Como Configurar**

Para configurar os parâmetros no seu _realm_, entre em contato com o suporte da Digibee via chat.

{% hint style="info" %}
**IMPORTANTE:** Esta funcionalidade faz parte do [programa Beta.](../../../general/programa-beta.md)
{% endhint %}
