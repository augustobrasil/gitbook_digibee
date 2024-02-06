---
description: >-
  Descubra mais sobre o componente RSA Cryptography e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# RSA Cryptography

O **RSA Cryptography** criptografa e descriptografa com base no algoritmo RSA.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="200">Parâmetro</th><th width="338">Descrição</th><th width="122.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Crypto Operation</strong></td><td>Tipos de operação disponíveis - <em>Encrypt Fields, Decrypt Fields, Encrypt Payload</em> e <em>Decrypt Payload</em>.</td><td><em>Encrypt Fields</em></td><td><em>String</em></td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Campos a serem criptografados/descriptografados utilizando uma notação com pontos (ex.: <em>body.field1, body.field2, body</em>).</td><td>a.test</td><td><em>String</em></td></tr><tr><td><strong>Payload To Encrypt/Decrypt</strong></td><td><em>Payload</em> a ser criptografado/descriptografado utilizando uma notação com pontos.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation Mode</strong></td><td>Modo de operação a ser utilizado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Padding</strong></td><td>Utilizado em um bloco de cifra no qual os blocos são preenchidos com bytes de padding (ex.: AES 128 <em>bits</em> utiliza 16 <em>bytes</em> de <em>padding</em>).</td><td>OAEPWithSHA-512AndMGF1Padding</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> da chave passada do tipo <em>string</em>.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Encrypt Message As Hex</strong></td><td>Se a opção estiver ativada, o retorno da <em>secret key</em> será em hexadecimal; do contrário, será em base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade <em>"success"</em>.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

Para criptografar, você precisa configurar uma conta _Public key_ ou passar a _property key_ via _body_ com a respectiva chave.

Para descriptografar, você precisa configurar uma conta _Private key account_.

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Operação Encrypt Fields <a href="#operao-encrypt-fields" id="operao-encrypt-fields"></a>

#### **Entrada**

{% code overflow="wrap" %}
```
{
"operation": "encrypt_fields",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
"key": "PoeK/VBTcUyRHFkmWYjckbhsRLnZur6S83lKZ78V51EL3KlDNnPJZkdz+m7joRfOxFuEqU=" //Informe o parâmetro Key se o Account não estiver configurado
}
```
{% endcode %}

#### **Payload**

```
{
"data": someData,
"data1": someData1
}
```

#### **Saída**

```
{
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}

```

### Operação Decrypt Fields <a href="#operao-decrypt-fields" id="operao-decrypt-fields"></a>

#### **Entrada**

```
{
"operation": "decrypt_fields",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
}
```

#### **Payload**

```
{
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

#### **Saída**

```
{
"data": someData,
"data1": someData1
}
```
