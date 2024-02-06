---
description: >-
  Saiba como criptografar ou descriptografar usando o componente Asymmetric
  Cryptography.
---

# Asymmetric Cryptography

O **Asymmetric Cryptography** criptografa e descriptografa com base em _keys_ públicas e privadas.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="183">Parâmetro</th><th width="355">Descrição</th><th width="119.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Conta a ser utilizada pelo componente. Contas suportadas: <em>Public key</em> ou <em>Private key</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Crypto Operation</strong></td><td>Tipos de operação disponíveis (<em>Encrypt</em> e <em>Decrypt</em>).</td><td><em>Encrypt</em></td><td><em>String</em></td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Campos a serem encriptados/decriptados utilizando uma notação com pontos (ex.: body.field1,body.field2,body).</td><td>body.field1,body.field2</td><td><em>String</em></td></tr><tr><td><strong>Algorithm</strong></td><td>Algoritmo a ser utilizado para criptografar/descriptografar dados.</td><td>RSA</td><td><em>String</em></td></tr><tr><td><strong>Operation Mode</strong></td><td>Modo de operação a ser utilizado.</td><td>ECB</td><td><em>String</em></td></tr><tr><td><strong>Padding</strong></td><td>Utilizado em um bloco de cifra no qual os blocos são preenchidos com bytes de padding (ex.: AES 128 <em>bits</em> utiliza 16 <em>bytes</em> de <em>padding</em>).</td><td>OAEPWithSHA1AndMGF1Padding</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do pipeline continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

Para criptografar, você precisa configurar uma conta _Public key_ ou passar a _property key_ via _body_ com a respectiva chave.

Para descriptografar, você precisa configurar uma conta _Private key_ ou passar a _property key_ via _body_ com a respectiva chave.

Se a chave não foi configurada na conta, você precisa especificar na solicitação conforme o modelo abaixo:

```
{"encryptionKey": "-- THE FOLLOWING PUBLIC KEY--"}
```

## Asymmetric Cryptography em Ação <a href="#asymmetric-cryptography-em-ao" id="asymmetric-cryptography-em-ao"></a>

### KEY por ACCOUNT <a href="#key-por-account" id="key-por-account"></a>

**Config**

```
{
"operation": "encrypt",
"algorithm": "RSA",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
}
```

**Payload**

```
{
"data": someData,
"data1": someData1
}
```

**Saída**

```
{
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

**Config**

```
{
"operation": "decrypt",
"algorithm": "RSA",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
}
```

**Payload**

```
{
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

**Saída**

```
{
"data": someData,
"data1": someData1
}
```

### KEY por REQUEST BODY <a href="#key-por-request-body" id="key-por-request-body"></a>

**Config**

```
{
"operation": "encrypt",
"algorithm": "RSA",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
}
```

**Payload**

```
{
"encryptionKey": "-- THE FOLLOWING PUBLIC KEY--"
"data": someData,
"data1": someData1
}
```

**Saída**

```
{
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```

**Config**

```
{
"operation": "decrypt",
"algorithm": "RSA",
"operationMode": "ECB",
"padding": "OAEPWithSHA1AndMGF1Padding",
"encryptedFields": "data,data1",
"failOnError": true
}
```

**Payload**

```
{
"encryptionKey": "-- THE FOLLOWING PRIVATE KEY--"
"data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
"data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="
}
```
