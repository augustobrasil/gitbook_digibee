---
description: >-
  Descubra mais sobre o componente PBE Cryptography e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# PBE Cryptography

O **PBE Cryptography** faz operações de criptografia e descriptografia usando o algoritmo PBE (_Password Based Encryption_).

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="186">Parâmetro</th><th width="340">Descrição</th><th width="134.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong> </td><td>Tipos de operação disponíveis <em>- Encrypt Fields, Decrypt Fields, Encrypt Payload</em> e <em>Decrypt Payload</em>.</td><td><em>Encrypt Fields</em></td><td><em>String</em></td></tr><tr><td><strong>Account</strong> </td><td>Conta a ser utilizada pelo componente. É esperada uma conta tipo <em>Secret Key</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Iteration Count</strong></td><td>Número de iterações com o <em>Salt</em>.</td><td>1000</td><td>Inteiro</td></tr><tr><td><strong>Algorithm</strong></td><td>Tipo de algoritmo a ser utilizado.</td><td>PBEWithMD5AndDES</td><td><em>String</em></td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Campos a serem criptografados/descriptografados utilizando uma notação com pontos (ex.: <em>body.field1, body.field2, body</em>).</td><td>a.test</td><td><em>String</em></td></tr><tr><td><strong>Payload To Encrypt/Decrypt</strong> <code>(DB)</code></td><td><em>Payload</em> a ser criptografado/descriptografado utilizando uma notação com pontos. Expressões <em>Double Braces</em> são permitidas.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Tipo de codificação.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Secret Key Type</strong></td><td>Formato da <em>secret key (String</em>, Hexadecimal ou Base64).</td><td>Base64</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade sucesso.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Configurações avançadas.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Use Key From Payload</strong></td><td>Se ativada, a opção utilizará a <em>secret key</em> do <em>payload</em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Secret Key</strong></td><td>Chave em formato Hex ou Base64.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Use Salt From Payload</strong></td><td>Se ativada, a opção utilizará o <em>Salt</em> do <em>payload</em>; do contrário, um novo <em>Salt</em> será gerado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Salt</strong></td><td>Cadeia aleatória de dados utilizada para modificar um <em>hash</em> de senha.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>Se a opção estiver ativada, o retorno da <em>secret key</em> será em hexadecimal; do contrário, será em Base64 caso a opção "<em>Use Key From Payload</em>" também esteja ativada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Salt As Hex Value</strong></td><td>Se a opção estiver ativada, o retorno do <em>Salt</em> será em hexadecimal; do contrário, será em Base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>Se a opção estiver ativada, o retorno da <em>secret key</em> será em hexadecimal; do contrário, será em Base64.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Criptografar via fields <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

#### **Entrada**

```
{
  "accountLabel": "account",
  "params": {
    "operation": "encrypt_fields",
    "iterationCount": 1000,
    "keyType": "STRING",
    "algorithm": "PBEWithMD5AndDES",
    "encryptedFields": "a.test",
    "failOnError": true
  }
}
```

#### **Payload**

```
{
  "a": {
    "test": "test"
  }
}
```

#### **Saída**

```
{
  "a": {
    "test": "ZmRmcw=="
  },
  "_salt": "ZmRmcwZmRmcw=="
}
```

### Descriptografar via fields

#### **Entrada**

```
{
  "accountLabel": "account",
  "params": {
    "operation": "decrypt_fields",
    "iterationCount": 1000,
    "keyType": "STRING",
    "algorithm": "PBEWithMD5AndDES",
    "encryptedFields": "a.test",
    "useSaltFromPayload": true,
    "salt": "{{ message._salt }}",
    "failOnError": true
  }
}
```

#### **Payload**

```
{
  "a": {
    "test": "ZmRmcw=="
  },
  "_salt": "ZmRmcwZmRmcw=="
}
```

#### **Saída**

```
{
  "a": {
    "test": "test"
  },
  "_salt": "ZmRmcwZmRmcw=="
}

```

### Criptografar via payload <a href="#criptografarvia-payload" id="criptografarvia-payload"></a>

#### **Entrada**

```
{
"accountLabel": "pbe",
    "params": {
        "operation": "encrypt_payload",
        "iterationCount": 1000,
        "payload": "{{ message.a.test }}",
        "keyType": "STRING",
        "algorithm": "PBEWithMD5AndDES",
        "failOnError": true
    }
}
```

#### **Payload**

```
{
  "a": {
    "test": "test"
  }
}
```

#### **Saída**

```
{
  "a": {
    "test": "test"
  },
  "result": "ZmRmcw==",
  "_salt": "ZmRmcwZmRmcw=="
}
```

### Descriptografar via payload <a href="#descriptografar-via-payload" id="descriptografar-via-payload"></a>

#### **Entrada** <a href="#descriptografar-via-payload" id="descriptografar-via-payload"></a>

```
{
"accountLabel": "pbe",
    "params": {
        "operation": "decrypt_payload",
        "iterationCount": 1000,
        "payload": "{{ message.a.test }}",
        "keyType": "STRING",
        "algorithm": "PBEWithMD5AndDES",
        "useSaltFromPayload": true,
"salt": "{{ message._salt }}",
        "failOnError": true
    }
}
```

#### **Payload**

```
{
  "a": {
    "test": "ZmRmcw=="
  }
}
```

#### **Saída**

```
{
  "a": {
    "test": "ZmRmcw=="
  },
  "result": "test",
  "_salt": "ZmRmcwZmRmcw=="
}
```
