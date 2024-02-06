---
description: >-
  Saiba como criptografar ou descriptografar usando o componente AES
  Cryptography.
---

# AES Cryptography

O **AES Cryptography** criptografa ou descriptografa com base em criptografia simétrica.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="181">Parâmetro</th><th width="344">Descrição</th><th width="113.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Tipos de operação disponíveis (<em>Encrypt Fields</em>, <em>Decrypt Fields</em>, <em>Encrypt Payload</em>, e <em>Decrypt Payload</em>)</td><td><em>Encrypt Fields</em></td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td><p>Conta a ser utilizada pelo componente. É esperada uma conta tipo <em>Secret key</em>. </p><p></p><p>Se você quiser utilizar uma chave arbitrária, então desfaça a seleção da conta e ative a opção <strong>Provide Key Or Generate Random</strong>, em <strong>Advanced Settings</strong>.</p></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fields To Encrypt/Decrypt</strong></td><td>Campos a serem criptografados/descriptografados utilizando uma notação com pontos (ex.: <em>body.field1</em>, <em>body.field2</em>, <em>body</em>)</td><td>a.test</td><td><em>String</em></td></tr><tr><td><strong>Payload to Encrypt/Decrypt</strong> <code>(DB)</code></td><td><em>Payload</em> a ser criptografado/descriptografado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Algorithm Key Size</strong></td><td>Tamanho da chave do algoritmo, disponível em 256 bits (necessária para usar uma chave de 32 bytes), 192 bits (chave de 24 bytes) e 128 bits (chave de 16 bytes).</td><td>256 bits</td><td>Inteiro (bits)</td></tr><tr><td><strong>Operation Mode</strong></td><td>Modo de operação a ser utilizado (CBC, OFB, CTR, CFB, GCM ou ECB).</td><td>CBC</td><td><em>String</em></td></tr><tr><td><strong>GCM Tag Length</strong></td><td>Define a <em>tag length</em> (<em>128 bits</em>, <em>120 bits</em>, <em>112 bits</em>, <em>104 bits</em> ou <em>96 bits</em>). Este campo está disponível apenas quando GCM estiver selecionado no parâmetro <strong>Operation Mode</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Padding</strong></td><td>utilizado em um bloco de cifra no qual os blocos são preenchidos com bytes de <em>padding</em> (ex.: AES 128 bits utiliza 16 bytes de <em>padding</em>). A opção <em>NoPadding</em> é utilizada somente quando a mensagem a ser criptografada com certeza não necessita de <em>padding</em>. O correto é sempre usar <em>padding</em> para evitar erros na hora de criptografar/descriptografar.</td><td>PKCS5Padding</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> da chave fornecida do tipo <em>string</em>.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Advanced Settings</strong></td><td>Se a opção estiver ativada, você pode acessar as seguintes configurações:</td><td>False</td><td>Booleano</td></tr><tr><td><strong>Concatenate IV</strong></td><td>Uma mensagem encriptada é esperada/produzida com o <em>Concatenate IV</em> (<em>IV+MESSAGE</em>); do contrário, um parâmetro <em>IV</em> será produzido durante a encriptação e <em>IV</em> em <em>IV</em> será esperado no campo "Decryption".</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Provide IV For Encryption</strong></td><td>Se a opção estiver ativada, será esperado um <em>IV</em> como parâmetro para a encriptação; do contrário, será gerado um parâmetro com zeros ou um parâmetro aleatório controlado pelo parâmetro <strong>Empty IV or Random IV?</strong>.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Empty IV or Random IV?</strong></td><td>Se a opção estiver ativada, será gerado um <em>IV</em> vazio (16 bytes de zeros); do contrário, será gerado um <em>IV</em> aleatório.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>IV as Hex Value</strong></td><td>Se a opção estiver ativada, será esperado um <em>IV</em> como hexadecimal; do contrário, espera-se base64. Este parâmetro não fica disponível quando <strong>Concatenate IV</strong> estiver ativado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Update AAD</strong></td><td><em>Additional authenticated data</em> para a operação GCM. Se a opção estiver ativada, é possível informar o <em>AAD</em> para a operação GCM. Esta opção está disponível apenas quando GCM estiver selecionado no parâmetro <strong>Operation Mode</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>AAD</strong></td><td><em>Additional authenticated data</em>. Valor para a chave <em>AAD</em> na operação GCM. Esta opção está disponível apenas quando <strong>Update AAD</strong> estiver ativado e GCM estiver selecionado no parâmetro <strong>Operation Mode.</strong></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>IV</strong></td><td>Vetor de inicialização a ser informado previamente para a realização de criptografia/descriptografia, que deve conter 16 bytes. Este parâmetro fica disponível somente quando <strong>Provide IV For Encryption</strong> estiver ativado e aceita <em>Double Braces</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Provide Key Or Generate Random</strong></td><td>Se a opção estiver ativada, espera-se uma chave; do contrário, uma chave aleatória será gerada.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Secret Key</strong></td><td>Chave em formato Hex ou base64 (controlada pelo parâmetro <strong>Encryption Key As Hex Value</strong>). A chave precisa ter o número de bits de acordo com o parâmetro <strong>Algorithm Key Size</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Encryption Key As Hex Value</strong></td><td>Se a opção estiver ativada, a opção espera/produz uma <em>Encryption Key</em> em formato Hex; do contrário, será esperada/produzida como base64.</td><td>N/A</td><td>Booleano</td></tr><tr><td><strong>Encrypted Message As Hex</strong></td><td>Se a opção estiver ativada, a opção espera/produz uma mensagem encriptada em formato Hex; do contrário, será esperada/produzida como base64.</td><td>N/A</td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Importante:** se você deseja utilizar a sua própria chave por conta, então será necessário configurar uma conta _Secret Key_ ou passar a respectiva propriedade através de _Double Braces_ com a chave.
{% endhint %}

## Fluxo de mensagens <a href="#h_c025db075e" id="h_c025db075e"></a>

### Entrada <a href="#h_b87248fe72" id="h_b87248fe72"></a>

Não se espera um formato específico de entrada.

### Saída <a href="#h_bde3904b70" id="h_bde3904b70"></a>

### **Crypto Operation: Encrypt Fields ou Decrypt Fields**

Será mantida a mesma estrutura de entrada na saída. Caso a opção **Concatenate IV** esteja desativada, será gerada uma nova propriedade "IV" no JSON informado para cada campo configurado.

**Exemplo**

#### **Entrada**

```
{
"array": [
{"text": "text"},
{"text": "text2"}
]
}
```

**Concatenate IV** desativado:

```
{
"array": [
{"text": "ENCRYPTED TEXT", "iv": "SOME BASE64"},
{"text": "ENCRYPTED TEXT", "iv": "SOME BASE64"}
]
}
```

**Concatenate IV** ativado:

```
{
"array": [
{"text": "ENCRYPTED TEXT"},
{"text": "ENCRYPTED TEXT"}
]
}
```

### **Crypto Operation: Encrypt Payload ou Decrypt Payload**

O valor criptografado será retornado dentro da propriedade "result". Caso a opção **Concatenate IV** esteja desativada, será gerada uma nova propriedade "IV" no JSON informado para cada campo configurado.

**Concatenate IV** desativado:

```
{
"result": "ENCRYPTED TEXT",
"iv": "SOME BASE64"
}
```

**Concatenate IV** ativado:

```
{
"result": "ENCRYPTED TEXT
}
```

## AES Cryptography em Ação <a href="#h_1e9cef2074" id="h_1e9cef2074"></a>

### **Criptografia Encrypt Fields** <a href="#h_4171128069" id="h_4171128069"></a>

* **Crypto operation:** Encrypt Fields
* **Fields To Encrypt/Decrypt:** array.text
* **Algorithm key Size:** 256
* **Operation Mode:** CBC
* **Padding:** PKCS5Padding
* **Advanced Settings:** ativado
* **Concatenate IV:** ativado
* **Provide IV for encryption:** ativado
* **IV:** MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random:** ativado
* **Secret Key:** MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (É recomendável armazenar essa chave em uma conta do tipo SECRET-KEY)
* **Encryption Key As Hex Value:** desativado
* **Encrypted Message As Hex:** desativado

#### **Entrada**

```
{
"array": [
{"text": "text"},
{"text": "text2"}
]
}
```

#### **Saída**

```
{
"array": [
{
"text": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="
},
{
"text": "MTIzNDU2Nzg5MDEyMzQ1NijQdN4bFfeBL9Z6vCfzMTw="
}
]
}
```

### Criptografia Encrypt Payload <a href="#h_a409939f67" id="h_a409939f67"></a>

* **Crypto operation:** Encrypt Payload
* **Payload:** text
* **Algorithm key Size:** 256
* **Operation Mode:** CBC
* **Padding:** PKCS5Padding
* **Advanced Settings:** ativado
* **Concatenate IV:** ativado
* **Provide IV for encryption:** ativado
* **IV:** MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random:** ativado
* **Secret Key:** MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (É recomendável armazenar essa chave em uma conta do tipo SECRET-KEY)
* **Encryption Key As Hex Value:** desativado
* **Encrypted Message As Hex:** desativado

#### **Entrada**

```
{}
```

#### **Saída**

```
{
"result": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="
}
```

### Descriptografar Decrypt Fields <a href="#h_130432a1a0" id="h_130432a1a0"></a>

* **Crypto operation:** Decrypt Fields
* **Fields To Encrypt/Decrypt:** array.text
* **Algorithm key Size:** 256
* **Operation Mode:** CBC
* **Padding:** PKCS5Padding
* **Advanced Settings:** ativado
* **Concatenate IV:** ativado
* **Provide IV for encryption:** ativado
* **IV:** MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random:** ativado
* **Secret Key:** MTIzNDU6Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (É recomendável armazenar essa chave em uma conta do tipo SECRET-KEY)
* **Encryption Key As Hex Value:** desativado
* **Encrypted Message As Hex:** desativado

#### **Entrada**

```
{
"array": [
{
"text": "MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU="
},
{
"text": "MTIzNDU2Nzg5MDEyMzQ1NijQdN4bFfeBL9Z6vCfzMTw="
}
]
}
```

#### **Saída**

```
{
"array": [
{"text": "text"},
{"text": "text2"}
]
}
```

### Descriptografar Decrypt Payload <a href="#h_1f737c3cb4" id="h_1f737c3cb4"></a>

* **Crypto operation:** Decrypt Payload
* **Payload:** MTIzNDU2Nzg5MDEyMzQ1Npp1dUf7FzjkLwD9Ezq4FSU=
* **Algorithm key Size:** 256
* **Operation Mode:** CBC
* **Padding:** PKCS5Padding
* **Advanced Settings:** ativado
* **Concatenate IV:** ativado
* **Provide IV for encryption:** ativado
* **IV:** MTIzNDU2Nzg5MDEyMzQ1NjE=
* **Provide Key Or Generate Random:** ativado
* **Secret Key:** MTIzNDU2Nzg5MDEyMzQ1NjEyMzQ1Njc4OTAxMjM0NTY= \
  (É recomendável armazenar essa chave em uma conta do tipo SECRET-KEY)
* **Encryption Key As Hex Value:** desativado
* **Encrypted Message As Hex:** desativado

#### **Entrada**

```
{}
```

#### **Saída**

```
{"result": "text"}
```
