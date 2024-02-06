---
description: >-
  Aprenda como usar o componente WGet para baixar qualquer arquivo através de
  uma URL.
---

# WGet (Download HTTP)

O **WGet (Download HTTP)** realiza o _download_ de qualquer arquivo através de uma URL.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>URL</strong> <code>(DB)</code></td><td>De onde o arquivo será baixado - expressões em <em>Double Braces</em> são suportadas.</td><td>https://sendgrid.com/docs/API_Reference/Web_API_v3/Mail/index.html</td><td><em>String</em></td></tr><tr><td><strong>Headers</strong></td><td><em>Headers</em> da chamada.</td><td>N/A</td><td><em>Key-value Pairs</em></td></tr><tr><td><strong>Query Params</strong></td><td><em>Query parameters</em> da chamada.</td><td>N/A</td><td><em>Key-value Pairs</em></td></tr><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>ApiKey, Basic, Certificate Chain, Custom Auth Header, Oauth2</em> e <em>Oauth Bearer Token</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Allow Insecure Calls To HTTPS Endpoints</strong></td><td>Quando ativada, a opção permite que chamadas não seguras a <em>endpoints</em> HTTPS sejam feitas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Binary File</strong></td><td>Se ativada, a opção retorna a base64 do arquivo.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Local Save</strong></td><td>Se ativada, a opção permite que o arquivo seja salvo localmente.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo local a passar por <em>download</em> ou <em>upload</em>.</td><td>N/A</td><td><em>String</em></td></tr></tbody></table>

## WGet em ação <a href="#wget-em-ao" id="wget-em-ao"></a>

### Exemplo com Double Braces estáticos <a href="#exemplo-com-double-braces-estticos" id="exemplo-com-double-braces-estticos"></a>

URL

```url
https://sendgrid.com/docs/API_Reference/Web_API_v3/Mail/index.html
```

### Exemplo com Double Braces dinâmicos <a href="#exemplo-com-double-braces-dinmicos" id="exemplo-com-double-braces-dinmicos"></a>

URL

```
{{ message.example.url }}
```

```
https://www.download.com/file/{{ message.id }}/pdf
```

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Você não precisa especificar o formato de entrada se utilizar _Double Braces_ para preencher os parâmetros.

O **File Name** substitui o nome padrão e a **URL** substitui a URL padrão.

### Saída <a href="#sada" id="sada"></a>

Se a opção _**Local Save**_ estiver ativada:

```
{
    "fileName": "",
    "success": ""
}
```

Se as opções **Local Save** e **Binary File** estiverem ativadas:

```
{
    "fileBase64": ""
}
```

Se as opções **Local Save** e **Binary File** não estiverem ativadas:

```
{
    "fileText": ""
}
```

Em caso de erro:

```
{
    "error": {
        "exception": "",
        "message": ""
    }
}
```
