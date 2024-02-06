---
description: >-
  Descubra mais sobre o componente PGP e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# PGP

O **PGP (Pretty Good Privacy)** é um componente de criptografia que fornece autenticação e privacidade criptográfica para a comunicação de dados.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table><thead><tr><th width="163">Parâmetro</th><th width="310">Descrição</th><th width="140">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Define a conta que será usada pelo conector. A conta deve ser <em>PUBLIC</em> ou <em>PRIVATE-KEY</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Define o tipo de operação (<em>Encrypt Fields, Decrypt Fields, Encrypt Payload, Decrypt Payload, Encrypt File</em> ou <em>Decrypt File</em>).</td><td><em>Encrypt Fields</em></td><td><em>String</em></td></tr><tr><td><strong>Fields</strong></td><td>Nome dos campos a serem criptografados dentro do JSON de entrada (devem estar separados por vírgula, ex.: param1,param2). Este parâmetro fica disponível somente quando <em>Encrypt Fields</em> ou <em>Decrypt Fields</em> estiverem selecionados no parâmetro <em><strong>Operation</strong></em>.</td><td>parameter</td><td><em>String</em></td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Pode ser definido como um valor único ou por <em>Double Braces</em> para obter e definir um <em>payload</em>. Este parâmetro fica disponível somente quando <em>Encrypt Payload</em> ou <em>Decrypt Payload</em> estiverem selecionados no parâmetro <em><strong>Operation</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> do texto.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>File Name</strong> <code>(DB)</code></td><td>Nome do arquivo a ser criptografado/descriptografado. Este parâmetro suporta expressões <em>Double Braces</em> e fica disponível somente quando <em>Encrypt File</em> ou <em>Decrypt File</em> estiverem selecionados no parâmetro <em><strong>Operation</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Output File Name</strong> <code>(DB)</code></td><td>Nome do arquivo criptografado a ser gerado. Este parâmetro suporta expressões <em>Double Braces</em> e fica disponível somente quando <em>Encrypt File</em> ou <em>Decrypt File</em> estiverem selecionados no parâmetro <em><strong>Operation</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Hexadecimal</strong></td><td>Se a opção estiver ativada, o valor a ser verificado ou assinado deve ser fornecido no formato hex; do contrário, será assinada ou verificada como base64.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Armor</strong></td><td>Se a opção estiver ativada, irá encriptar as mensagens em ASCII para que elas sejam enviadas em formato padrão, assim como e-mail.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Zip</strong></td><td>Se a opção estiver ativada, irá zipar a mensagem antes de ser encriptada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Integrity Check</strong></td><td>Se a opção estiver ativada, irá verificar a integridade da mensagem.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Operação Encrypt Fields <a href="#operao-encrypt-fields" id="operao-encrypt-fields"></a>

#### **Entrada**

```
{
"parameter": "TEXT TO BE ENCRYPTED"
}
```

#### **Saída**

```
{
"parameter": "AA01FF" // text encrypted
}
```

### Operação _Decrypt Fields_ <a href="#operao-decrypt-fields" id="operao-decrypt-fields"></a>

#### **Entrada**

```
{
"parameter": "AA01FF" // text encrypted
}
```

#### **Saída**

```
{
"parameter": "TEXT DECRYPTED"
}
```

### **Operação Encrypt Payload** <a href="#operao-encrypt-payload" id="operao-encrypt-payload"></a>

#### **Entrada**

```
{
"parameter": "TEXT TO BE ENCRYPTED"
}
```

#### **Saída**

```
{
"result": "AA01FF" // text encrypted
}
```

### Operação Decrypt Payload <a href="#operao-decrypt-payload" id="operao-decrypt-payload"></a>

#### **Entrada**

```
{
"parameter": "AA01FF" // text encrypted
}
```

#### **Saída**

```
{
"result": "TEXT DECRYPTED"
}
```

### **Operação Encrypt File** <a href="#operao-encrypt-file" id="operao-encrypt-file"></a>

#### **Entrada**

```
{
"fileName": "file.txt"
}
```

#### **Saída**

```
{
"outputFileName": "file.txt.pgp" // file encrypted
}
```

### Operação Decrypt File <a href="#operao-decrypt-file" id="operao-decrypt-file"></a>

#### **Entrada**

```
{
"fileName": "file.txt.pgp" // file encrypted
}
```

#### **Saída**

```
{
"outputFileName": "file.txt.dec" // file decrypted
}
```

### **Saída contendo erro** <a href="#sada-contendo-erro" id="sada-contendo-erro"></a>

```
{
"error": "java.io.FileNotFoundException: data1.csv (No such file or directory)",
"success": false
}
```

* _**success**_**:** “_false_” quando a operação falha.
* _**error**_**:** informação sobre o tipo de erro ocorrido.
