---
description: >-
  Descubra mais sobre o componente Hash e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Hash

O **Hash** gera um _hash_ a partir de uma _string._&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="137">Parâmetro</th><th width="408">Descrição</th><th width="142.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Crypto Operation</strong></td><td>Tipos de operação disponíveis (<em>Hash Fields, Hash Payload</em> e <em>Hash File</em>).</td><td><em>Hash Fields</em></td><td><em>String</em></td></tr><tr><td><strong>File name</strong></td><td>Nome ou caminho completo do arquivo (i.e. tmp/processed/file.txt). Este campo fica disponível somente quando <em>Hash File</em> estiver selecionado no parâmetro <em><strong>Crypto Operation</strong></em> e suporta somente <em>MD5 Crypto Algorithm</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Crypto Algorithm</strong></td><td>Tipo de algoritmo utilizado para gerar o <em>hash</em>. Os possíveis valores para esse parâmetro são <em>MD5, SHA-1, SHA-256, SHA-384, SHA-512, HmacSHA1, HmacSHA256, HmacSHA384, HmacSHA512</em> e <em>BCrypt.</em></td><td>SHA-512</td><td><em>String</em></td></tr><tr><td><strong>Account</strong></td><td>Só será exibida caso o algoritmo selecionado no campo <em><strong>Crypto Algorithm</strong></em> seja <em>HmacSHA1, HmacSHA256, HmacSHA384</em> ou <em>HmacSHA512</em>. A conta deve ser do tipo SECRET_KEY e a chave para fazer o <em>hash</em> deve ser informada.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Secret Key</strong> <code>(DB)</code></td><td>Só será exibida se nenhuma conta estiver selecionada e caso o algoritmo selecionado no campo <em><strong>Crypto Algorithm</strong></em> seja <em>HmacSHA1, HmacSHA256, HmacSHA384</em> ou <em>HmacSHA512</em>. Essa é uma alternativa para o componente receber a chave para a geração do <em>hash</em> de forma dinâmica.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Secret Key Type</strong></td><td>Só será exibido caso o algoritmo selecionado no campo <em><strong>Crypto Algorithm</strong></em> seja <em>HmacSHA1, HmacSHA256, HmacSHA384</em> ou <em>HmacSHA512</em>. Esse campo também informa para o componente qual é o tipo da chave informada, que pode ser do tipo <em>String</em>, Hexadecimal ou base64.</td><td>Hexadecimal</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> do tipo da chave informada. Este campo fica disponível somente quando o valor do parâmetro <em><strong>Secret Key Type</strong> for String</em>.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>BCrypt Version</strong></td><td>Versão do algoritmo <em>BCrypt</em> a ser considerada na geração do <em>hash</em>. Essa opção será disponibilizada apenas quando o valor do parâmetro <em><strong>Crypto Algorithm</strong> for BCrypt</em>.</td><td>2y</td><td>N/A</td></tr><tr><td><strong>Salt</strong></td><td><em>String</em> de 16 <em>bytes</em> adicionada ao valor do <em>hash</em>. Caso não seja informado, será assumido um valor aleatório. Essa opção será disponibilizada apenas quando o valor do parâmetro <em><strong>Crypto Algorithm</strong> for BCrypt.</em></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Cost Factor</strong></td><td>Determina a quantidade de rodadas para o <em>hash</em> ser executado. O fator de custo será elevado à potência de 2 e os possíveis valores estão entre 4 e 20. Ex: se o valor do parâmetro for 10, então a quantidade de rodadas para o <em>hash</em> será 2ˆ10 = 1024 rodadas. Essa opção será disponibilizada apenas quando o valor do parâmetro <em><strong>Crypto Algorithm</strong> for BCrypt</em>. Veja mais na <a href="hash.md#fator-de-custo">seção</a> abaixo.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>JSON Field Path</strong></td><td>JSON como caminho do campo <em>string</em> em notação com pontos (<em>dotted notation</em>).</td><td>xml.text</td><td><em>String</em></td></tr><tr><td><strong>Payload</strong></td><td>Campo para informar diretamente o <em>payload</em> que terá o <em>hash</em> feito. Ele será exibido apenas se a operação selecionada for <em>Hash Payload</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Preserve Original</strong></td><td>Se ativada, a opção preserva o campo original como propriedade "<em>Field"</em> no mesmo nível do original.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Result As Hexadecimal</strong></td><td>Se ativada, a opção mantém o <em>hash</em> em formato hexadecimal; do contrário, o formato será base64.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Importante:** o componente gera um _hash_ a partir de uma _string_ passada no campo _**Payload**_ caso a operação selecionada seja _Hash Payload_. No entanto, se a operação selecionada for _Hash Fields_, então o componente gera um _hash_ a partir de uma _string_ passada nos campos especificados do JSON de entrada.
{% endhint %}

## Fator de custo

O fator de custo no algoritmo _BCrypt_ afeta exponencialmente o tempo e os recursos de processamento, pois o algoritmo será executado consecutivamente de acordo com o número de rodadas obtidas através do resultado do cálculo 2^n, no qual "n" é o fator de custo.

Veja alguns exemplos de execução para servir de parâmetro de duração do cálculo do _hash_. Como premissa para aplicar o _hash_ do algoritmo _BCrypt_ estão sendo utilizados um _payload_ de 1MB e um fator de custo com o mínimo e o máximo permitido. Os resultados obtidos são:

**Cost Factor 4**

* **Pipeline Small:** média de 0.98s
* **Pipeline Medium:** média de 0.64s
* **Pipeline Large:** média de 0.07s

**Cost Factor 20**

* **Pipeline Small:** média de 8m 7s
* **Pipeline Medium:** média de 3m 56s
* **Pipeline Large:** média de 1m 53s

Os resultados acima podem variar de acordo com o fluxo de integração construído, com o tamanho da mensagem a ter o _hash_ aplicado e com o fator de custo.

Outro ponto importante a ser destacado diz respeito aos limites do fator de custo. O fator de custo do algoritmo _BCrypt_ permite uma faixa entre 4 e 31. No entanto, fatores acima de 20 acabam consumindo carga de processamento e tempo muito alto, inviabilizando os parâmetros de _timeout_ de execução de um _pipeline_.&#x20;

Com isso, o componente Hash foi limitado a aceitar no máximo 20 como valor de fator de custo. Partindo dessa premissa, quando for realizado o _hash_ de um valor por meio do componente Hash e com a utilização do algoritmo _BCrypt_, atente-se ao limite de 20 como fator de custo. Dessa forma são evitados problemas de validação ou checagem no seu fluxo de integração.

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

## Entrada <a href="#entrada" id="entrada"></a>

Se você selecionar a operação _Hash Fields_, o componente recebe qualquer mensagem de entrada, mas você deve configurar o caminho para o _hash_ da mensagem na propriedade **JSON Field Path**. Por exemplo:

**JSON Field Path:** data.test

```
{
"data": [
{"test":"xpto"},
{"test":"xpto1"},
{"test":"xpto2"},
{"test":"xpto3"}
]
}
```

Portanto, o componente faz uma busca na propriedade “test”, dentro da propriedade “data”.

Por outro lado, se você selecionar a operação _Hash Payload,_ então a mensagem de entrada deve ser informada dentro do campo **Payload**.

## Saída <a href="#sada" id="sada"></a>

### **Operação Hash Fields**

Se você selecionar a operação _Hash Fields_, a saída contém a mesma estrutura de entrada, porém exibindo o _hash_ da mensagem. Se a propriedade **Preserve Original** estiver habilitada, então a saída preserva o campo original no mesmo nível, adicionando o prefixo `'_'` na frente do campo:

```
{
"data": [
{
"test": "3851b1ae73ca0ca6e3c24a0256a80ace",
"_test": "xpto"
},
{
"test": "ca9e9bf198149d78f4aad334c838a263",
"_test": "xpto1"
},
{
"test": "83709b4f9067a83bbdfb0c358dc23a5e",
"_test": "xpto2"
},
{
"test": "e427f7e6f1bd29d91ea0cc53e40fba12",
"_test": "xpto3"
}
]
}
```

### **Operação Hash Payload**

Se você selecionar a operação _Hash Payload_, a saída exibe a propriedade "result" com o _hash_ da mensagem passada:

```
{
"result": "3851b1ae73ca0ca6e3c24a0256a80ace"
}
```

#### **Erro**

```
{
"success": false,
"message": "Something went wrong while trying to use the HashConnector. Error: java.lang.StringIndexOutOfBoundsException: String index out of range: 1",
"error": "java.lang.StringIndexOutOfBoundsException: String index out of range: 1"
}
```

* **success:** “false”, pois ocorreu um erro na execução.
* **message:** mensagem de erro do componente.
* **error:** mensagem de erro recebida do algoritmo de _hash._

## Hash em Ação <a href="#hash-connector-em-ao" id="hash-connector-em-ao"></a>

### Operação Hash Fields <a href="#operao-hash-fields" id="operao-hash-fields"></a>

#### **Exemplo 1**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** SHA-256
* **JSON Field Path:** data.test
* **Preserve Original:** ativado
* **Result As Hexadecimal:** ativado

#### **Entrada**

```
{
"data": [
{"test":"xpto"},
{"test":"xpto1"},
{"test":"xpto2"},
{"test":"xpto3"}
]
}
```

#### **Saída**

```
{
"data": [
{
"test": "2e954593b0b51547656f7f06ec3818a2b42fed46307b81bd493133aa1ce45173",
"_test": "xpto"
},
{
"test": "8b948d95169f851545f8161fb4dc8e1d37a4c79014ac1d02186fa8946a91aab9",
"_test": "xpto1"
},
{
"test": "4c9e0d7ca22d9ab7cc675de59226f9477fd847ede13894b835d0ae204139f63a",
"_test": "xpto2"
},
{
"test": "b5bd5abe3eb5958153af6615df06ccbdfe5857a13da2601f49e4de9fbb102f9a",
"_test": "xpto3"
}
]
}
```

#### **Exemplo 2**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** HmacSHA256
* **Account:** vazio
* **Secret Key:** 001def0209
* **Secret Key Type:** Hexadecimal (a chave passada na propriedade **Secret Key** deve estar em hexadecimal)
* **JSON Field Path:** data.test
* **Preserve Original:** ativado
* **Result As Hexadecimal:** ativado

#### **Entrada**

```
{
"data": [
{"test":"xpto"},
{"test":"xpto1"},
{"test":"xpto2"},
{"test":"xpto3"}
]
}
```

#### **Saída**

```
{
"data": [
{
"test": "257966929b29a6e0618d47a152e2856a888072400a5cb458fa1d40ff3cedc734",
"_test": "xpto"
},
{
"test": "ce0e754ab2f57f1fca1a00fce3e834a6940bea8013ae59b6641a4911e349b480",
"_test": "xpto1"
},
{
"test": "ff0cd9c0df219f99567aeb25d7d5ab9acff3c29728b0f4f71f50e750750a26d5",
"_test": "xpto2"
},
{
"test": "04a11cbc118ea455c0072e6c70607f68324e5444c8a4795443d25933d9dfa9c6",
"_test": "xpto3"
}
]
}
```

#### **Exemplo 3**

* **Crypto Operation:** Hash Fields
* **Crypto Algorithm:** BCrypt
* **Bcrypt Version:** 2y
* **Salt:** N9qo8uLOickgx2ZM
* **Cost:** 6
* **JSON Field Path:** data.test
* **Preserve Original:** ativado

#### **Entrada**

```
{
"data": [
{"test":"xpto"},
{"test":"xpto1"},
{"test":"xpto2"},
{"test":"xpto3"}
]
}
```

#### **Saída**

```
{
"data": [
{
"test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROhJmATBMG6eXfkYkffexdfdFHzzp27Iu",
"_test": "xpto"
},
{
"test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROm9TaJZ6QQUstIomnJG/Qgc7fPU5x8S.",
"_test": "xpto1"
},
{
"test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROHAP1dIbNu3SenuQ6B.W9OkJ0/NzYF6e",
"_test": "xpto2"
},
{
"test": "$2y$06$RhjvZxfzRC7nW0rlcBHYROPsXkmxUVt8Suo8d3GuOl9q0pryw6iJy",
"_test": "xpto3"
}
]
}
```

### Operação Hash Payload <a href="#operao-hash-payload" id="operao-hash-payload"></a>

#### **Exemplo 1**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** SHA-256
* **Payload:** xpto
* **Result As Hexadecimal:** ativado

#### **Saída**

```
{
"result": "2e954593b0b51547656f7f06ec3818a2b42fed46307b81bd493133aa1ce45173"
}
```

#### **Exemplo 2**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** HmacSHA512
* **Account:** vazio
* **Secret Key:** 001def0209
* **Secret Key Type:** Hexadecimal (a chave passada na propriedade **Secret Key** deve estar em hexadecimal)
* **Payload:** xpto
* **Result As Hexadecimal:** ativado

#### **Saída**

```
{
"result": "517da9449385a43478309459adf9304bd3c8f63cd1d388abd5cbc02b81d8ccb39d303f877019aebfed073166e6c410197e10077f6df3f7a3b3f50adb8cd09580"
}
```

#### **Exemplo 3**

* **Crypto Operation:** Hash Payload
* **Crypto Algorithm:** BCrypt
* **Bcrypt Version:** 2b
* **Salt:** N9qo8uLOickgx2ZM
* **Cost:** 10
* **Payload:** \{{ message.data \}}

#### **Entrada**

```
{
"data": [
{"test":"xpto"},
{"test":"xpto1"},
{"test":"xpto2"},
{"test":"xpto3"}
]
}
```

#### **Saída**

```
{
"result": "$2b$10$RhjvZxfzRC7nW0rlcBHYROa3UXROXVeKZ3oK4DSc1mV6iJ/pBqBm6"
}
```
