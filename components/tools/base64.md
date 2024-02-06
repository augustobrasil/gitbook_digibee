---
description: >-
  Descubra mais sobre o componente Base64 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Base64

O **Base64** realiza a codificação e a decodificação de/para campos, _payloads_ e arquivos no formato base64 _string_.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>Define qual operação será executada: <em><strong>Encode Fields</strong></em>, <em><strong>Encode Payload</strong></em>, <em><strong>Encode File</strong></em>, <em><strong>Decode Fields</strong></em>, <em><strong>Decode Payload</strong></em> e <em><strong>Decode File</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JSON Fields</strong></td><td>Caminho do JSON a ser codificado ou decodificado. Os campos precisam ser separados por vírgula (exemplo: field1,field2). Essa opção é válida somente para as operações <em><strong>Encode Fields</strong></em> e <em><strong>Decode Fields</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva campos originais e modifica prefixos adicionando o caractere <em>underline</em> <code>(_)</code>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Payload</strong></td><td>Campo para informar diretamente o <em>payload</em> que terá o seu conteúdo codificado/decodificado (exemplo: <code>body, data, {{ message.payload }}</code>). Essa opção é válida somente para as operações <em><strong>Encode Payload</strong></em> e <em><strong>Decode Payload</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Result As File</strong></td><td>Se ativada, a opção salva o resultado da codificação ou da decodificação em um arquivo. Essa opção é válida somente para as operações <em><strong>Encode Payload</strong></em> e <em><strong>Decode Payload</strong></em>.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>File Name</strong></td><td>Nome do arquivo a ser comprimido.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Output File Name</strong></td><td>Nome do arquivo de saída após a codificação/decodificação de um arquivo. Essa opção é válida somente para as operações <em><strong>Encode File</strong></em> e <em><strong>Decode File</strong></em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Is Binary</strong></td><td>Se ativada, a opção irá esperar o <em>payload</em> como um arquivo binário. Essa opção é válida somente para a operação <em><strong>Decode Payload</strong></em>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado mostrará um valor falso para a propriedade "success".</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

{% hint style="warning" %}
Os campos **File Name** e **Output File Name** devem receber valores diferentes. Caso os valores sejam iguais, um erro será produzido (uma exceção).
{% endhint %}

## Fluxo de mensagens

### Entrada

Para as operações _**Encode Fields**_ e _**Decode Fields**_, o componente espera receber um JSON contendo os campos configurados na propriedade **JSON Fields**.

**Exemplo:**

Configuração:

```
JSON Field = field1,field2
```

O JSON esperado deve conter pelo menos:

```
{   
   "field1": "SOMETHING",   
   "field2": "SOMETHING"
}
```

Para as operações _**Encode Payload**_ e _**Decode Payload**_, você deve configurar o campo **Payload** para poder codificar/decodificar.

**Exemplo:**

Configuração:

```
Payload = {{ message.field1 }}
```

O JSON esperado deve conter pelo menos:

```
{   
   "field1": "SOMETHING"
}
```

Para as operações _**Encode File**_ e _**Decode File**_, você deve configurar o arquivo que será codificado/decodificado e o arquivo resultante dessa operação.

**Exemplo:**

```
File Name = input.csv
Output File Name = outputfile.csv
```

### Saída

Para as operações _**Encode Fields**_ e _**Decode Fields**_:

```
{   
   "field1": "SOMETHING ENCODED/DECODED",   
   "field2": "SOMETHING ENCODED/DECODED",   
   "_field1": "ORIGINAL VALUE",   
   "_field2": "ORIGINAL VALUE"
}
```

Para as operações _**Encode Fields**_ e _**Decode Fields**_, caso a mensagem de entrada seja preservada:

```
{   
   "field1": "SOMETHING ENCODED/DECODED",   
   "field2": "SOMETHING ENCODED/DECODED",   
   "_field1": "ORIGINAL VALUE",   
   "_field2": "ORIGINAL VALUE",
}
```

Para as operações _**Encode Payload**_ e _**Decode Payload**_, caso a saída seja um arquivo:

```
{   
   "success": "true",   
   "fileName": "file.csv"
}
```

Para as operações _**Encode Payload**_ e _**Decode Payload**_, caso a saída seja uma _string_:

```
{   
   "success": "true",   
   "result": "SOMETHING ENCODED/DECODED"
}
```

Para as operações _**Encode File**_ e _**Decode File**_:

```
{   
   "success": "true",   
   "fileName": "file.csv",   
   "outputFileName": "file.csv"
}
```
