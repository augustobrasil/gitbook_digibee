---
description: Conheça o componente e saiba como utilizá-lo.
---

# DB V1 (Descontinuado)

O **DB V1** efetua operações de SELECT, INSERT, DELETE e UPDATE, retornando os valores para uma estrutura JSON.

{% hint style="info" %}
**Importante:** cuidado com o consumo de memória para _datasets_ grandes. Se preferir, você pode utilizar o Stream DB. [Para acessar o artigo sobre ele, clique aqui.](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stream-db-v3)
{% endhint %}

## Parâmetros

Dê uma olhada nas opções de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="320">Descrição</th><th width="135.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Database URL</strong></td><td><em>String</em> de conexão ao banco de dados no formato JBDC.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>SQL Statement</strong></td><td>Instrução SQL a ser executada.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Coalesce</strong></td><td>Quando ativada, essa opção controla se os objetos de dados são fundidos em uma sequência ou se um erro é gerado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Connection Properties</strong></td><td>Propriedades de conexão específicas definidas pelo usuário.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Keep Connections</strong></td><td>Se estiver ativada, a opção vai manter as conexões com a base de dados por no máximo 30 minutos; do contrário, será por apenas 5 minutos.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced</strong></td><td>Configurações avançadas.</td><td>N/A</td><td>N/A</td></tr><tr><td><strong>Connection Test Query</strong></td><td>Instrução SQL a ser utilizada antes que cada conexão seja estabelecida - esse parâmetro é opcional e deve ser aplicado a bancos de dados que não possuem informações confiáveis sobre o status da conexão.</td><td>N/A</td><td>N/A</td></tr></tbody></table>

## **Exemplo**

```
{     
    "parameters": {         
        "field1": {         
            "a": "b"         
        }    
    }
}
```

* coalesce = true => field1 = "{\\"a\\": \\"b\\"}"
* coalesce = false => exception
* coalesce = true => field1 = "{\\"a\\": \\"b\\"}"
* coalesce = false => exception

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Entrada**

```
{    
    "parameters": {        
        "name": "value"            
        ...    
    }
}        
```

### **Saída**

```
{    
    "data": [        
        {"column1":"data1", "column2":"data2", ... }    
    ],
    "rowCount": number_of_returned_rows,
    "updateCount": number_of_rows_updated
}
```

### Saída com erro <a href="#sada-com-erro" id="sada-com-erro"></a>

```
{    
    "code": error_code,    
    "error": error_message,    
    "cause": cause_of_the_error,    
    "sqlState": the_driver_specific_sql_state,    
    "vendorCode": the_driver_specific_error_code
}
```

[Para conhecer funções e utilidades para bancos de dados, clique aqui.](https://docs.digibee.com/documentation/v/pt-br/tutorials-and-best-practices/funcoes-e-utilidades-para-banco-de-dados)
