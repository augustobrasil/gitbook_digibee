---
description: >-
  Saiba como criptografar ou descriptografar usando o componente Symmetric
  Cryptography.
---

# Symmetric Cryptography

O **Symmetric Cryptography** criptografa e descriptografa com base em criptografia simétrica.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="194">Parâmetro</th><th width="344">Descrição</th><th width="110.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Tipos de operação disponíveis - <em>Encrypt</em> e <em>Decrypt</em>.</td><td><em>Encrypt</em></td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td>Conta que será utilizada pelo componente. É esperada uma conta <em>Private key</em>. O tamanho configurado no parâmetro <strong>Algorithm Key Size</strong> deve corresponder ao tamanho do algoritmo <em>Private key</em>. Do contrário, uma mensagem de erro será retornada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Campos a serem encriptados/decriptados utilizando uma notação com pontos (ex.: <em>body.field1, body.field2, body</em>).</td><td>body.field1,body.field2</td><td><em>String</em></td></tr><tr><td><strong>Algorithm</strong></td><td>Algoritmo a ser utilizado para criptografar/descriptografar dados.</td><td>AES</td><td><em>String</em></td></tr><tr><td><strong>Algorithm Key Size</strong></td><td>Tamanho da chave do algoritmo. Como citado anteriormente, o tamanho configurado neste parâmetro deve corresponder ao tamanho do algoritmo <em>Private key</em>.</td><td>256 bits</td><td>Inteiro</td></tr><tr><td><strong>Operation Mode</strong></td><td>Modo de operação a ser utilizado.</td><td>CBC</td><td><em>String</em></td></tr><tr><td><strong>Padding</strong></td><td>Utilizado em um bloco de cifra no qual os blocos são preenchidos com <em>bytes</em> de <em>padding</em> (ex.: AES 128 <em>bits</em> utiliza 16 <em>bytes</em> de <em>padding</em>).</td><td>PKCS5Padding</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Configurações avançadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Use IV</strong></td><td>Essa opção é válida somente para a operação <em>Encrypt</em>. Se selecionada, a opção determina o IV (vetor de inicialização) para o modo CBC.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Use Your Own Key</strong></td><td>Se selecionada, a opção utilizará a sua própria chave gerada para criptografar e descriptografar dados.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>Se selecionada, a opção espera/produz uma <em>Encryption Key as Hex</em>; do contrário, será esperada/produzida como base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Concatenate IV</strong></td><td>Uma mensagem encriptada é esperada/produzida com o <em>Concatenate IV</em> (IV+MESSAGE); do contrário, um parâmetro IV será produzido durante a encriptação e IV em IV será esperado no campo "<em>Decryption</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>IV as Hex Value</strong></td><td>Esta opção não é disponível se <strong>Concatenate IV</strong> estiver habilitado. Se for selecionada, a opção espera/produz um parâmetro IV em formato Hex; do contrário, será esperada/produzida como base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>Se selecionada, a opção espera/produz uma mensagem encriptada em formato Hex; do contrário, será esperada/produzida como base64.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Key por Account - Operação Encrypt**

#### **Entrada**

```
{
    "operation": "encrypt",
    "useOwnKey": true,
    "useIV": true,
    "algorithm": "AES",
    "operationMode": "CBC",
    "padding": "PKCS5Padding",
    "failOnError": true,
    "encryptedMessageAsHex": false,
    "iVAsHex": false,
    "encryptedFields": "data,data1"
}
```

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

#### **Entrada**

```
{
    "operation": "encrypt",
    "useOwnKey": true,
    "useIV": true,
    "algorithm": "AES",
    "operationMode": "CBC",
    "padding": "PKCS5Padding",
    "failOnError": true,
    "encryptedMessageAsHex": false,
    "iVAsHex": false,
    "encryptedFields": "data,data1"    
}
```

#### **Payload**

```
{
    "encryptionKey": "-- THE FOLLOWING PUBLIC KEY--",
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="    
}
```

#### **Saída**

```
{
    "ivParameterSpec": "RXZlbiBpZiBwZXJmZWN0IGNy==",
    "data": someData,
    "data1": someData1
}
```

### **Key por Request Body - Operação Encrypt**

#### **Entrada**

```
{
    "operation": "encrypt",
    "useOwnKey": true,
    "useIV": true,
    "algorithm": "AES",
    "operationMode": "CBC",
    "padding": "PKCS5Padding",
    "failOnError": true,
    "encryptedMessageAsHex": false,
    "iVAsHex": false,
    "encryptedFields": "data,data1"    
}
```

#### **Payload**

```
{
    "encryptionKey": "-- THE FOLLOWING PUBLIC KEY--"
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

#### **Entrada**

```
{
    "operation": "decrypt",
    "useOwnKey": true,
    "useIV": true,
    "algorithm": "AES",
    "operationMode": "CBC",
    "padding": "PKCS5Padding",
    "failOnError": true,
    "encryptedMessageAsHex": false,
    "iVAsHex": false,
    "encryptedFields": "data,data1"    
}
```

#### **Payload**

```
{
    "ivParameterSpec": "RXZlbiBpZiBwZXJmZWN0IGNy==",
    "encryptionKey": "-- THE FOLLOWING PRIVATE KEY--"
    "data": "RXZlbiBpZiBwZXJmZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH=",
    "data1": "RXZlbiBpZifd441mZWN0IGNyeXB0b2dyYXBoaWMgcm91dGluZXMgYXJlIH="    
}
```
