---
description: >-
  Descubra mais sobre o componente Digital Signature e saiba como utilizá-lo na
  Digibee Integration Platform.
---

# Digital Signature

O **Digital Signature** assina e verifica mensagens com base em chaves públicas e privadas.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="350">Descrição</th><th width="137.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Use este parâmetro para definir a conta a ser usada pelo conector.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Tipos de operação do componente (<em>Sign Fields, Sign Payload</em> ou <em>Verify</em>).</td><td><em>Sign Fields</em></td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Nome da codificação que faz a leitura do valor.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Hash Algorithm</strong></td><td>Algoritmo a ser utilizado para assinar/verificar os dados (ex.: SHA256WithRSA).</td><td>SHA256WithRSA</td><td><em>String</em></td></tr><tr><td><strong>Public Key Algorithm</strong></td><td>Tipo do algoritmo de chave pública (ex.: RSA). Este campo fica disponível apenas quando <em>Verify</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>RSA</td><td><em>String</em></td></tr><tr><td><strong>Hash</strong> <code>(DB)</code></td><td>Base do tipo base64 ou hex a ser verificada em relação ao <em>payload</em>. Este campo fica disponível apenas quando <em>Verify</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Sign Fields</strong></td><td>Campos a serem assinados/verificados (devem ser separados por vírgula). Este campo fica disponível apenas quando <em>Sign Fields</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>parameter</td><td><em>String</em></td></tr><tr><td><strong>Hash in Hexadecimal</strong></td><td>Se a opção estiver ativada, o valor a ser verificado ou assinado deve ser fornecido no formato hex; do contrário, será assinada ou verificada como base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Definido através de um valor único ou <em>Double Braces.</em> Este campo fica disponível apenas quando <em>Sign Payload</em> ou <em>Verify</em> estiverem selecionados no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="info" %}
**Importante:** para assinar, você precisa configurar uma _account_ PRIVATE\_KEY ou enviar a propriedade da chave via _body_. Para verificar, você precisa configurar uma _account_ PUBLIC\_KEY ou enviar a propriedade da chave via _body_.
{% endhint %}

## _Digital Signature_ em Ação <a href="#digital-signature-em-ao" id="digital-signature-em-ao"></a>

### Operação _Sign Fields_ <a href="#operao-sign-fields" id="operao-sign-fields"></a>

1\. Na sua paleta de componentes, selecione o _**Digital Signature**_.

2\. Abra as configurações do componente.

3\. No campo _**Operation**_, selecione _Sign Fields_.

4\. Insira as seguintes especificações nos campos indicados:

* _**Sign Fields**_**:** parameter
* _**Hash Algorithm**_**:** SHA256WithRSA

5\. Mantenha as opções _**Hash in Hexadecimal**_ e _**Fail On Error**_ ativadas.

6\. Clique em Confirmar.

7\. Faça o _deploy_ do _pipeline_.

8\. O _pipeline_ vai receber um _payload_ como este:

```
{"parameter": "Test for encryption"}
```

9\. O resultado do teste executado vai aparecer conforme demonstrado abaixo:

```
{
"parameter": "....032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E88ADD188A0B80311E672EDE5F8B......"
}
```

### Operação _Sign Payload_ <a href="#operao-sign-payload" id="operao-sign-payload"></a>

1\. Na sua paleta de componentes, selecione o _**Digital Signature**_.

2\. Abra as configurações do componente.

3\. No campo _**Operation**_, selecione _Sign Payload_.

4\. Insira as seguintes especificações nos campos indicados:

* _**Payload**_**:** \[{ \\"result\\": \\"\{{ message.$.parameter \}}\\"}]
* _**Hash Algorithm**_**:** SHA256WithRSA

5\. Mantenha as opções _**Hash in Hexadecimal**_ e _**Fail On Error**_ ativadas.

6\. Clique em Confirmar.

7\. Faça o _deploy_ do _pipeline_.

8\. O resultado do teste executado vai aparecer conforme demonstrado abaixo:

```
{
"result": "....032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E88ADD188A0B80311E672EDE5F8B......"
}
```

### Operação _Verify_ <a href="#operao-verify" id="operao-verify"></a>

1\. Na sua paleta de componentes, selecione o _**Digital Signature**_.

2\. Abra as configurações do componente.

3\. No campo _**Operation**_, selecione _Verify_.

4\. Insira as seguintes especificações nos campos indicados:

* _**Sign Fields:**_ \{{ message.$.signed \}}
* _**Parameter**_**:** \{{ message.$.rawData \}}
* _**Hash Algorithm**_**:** SHA256WithRSA
* _**Public Key Algorithm**_**:** RSA

5\. Mantenha as opções _**Hash in Hexadecimal**_ e _**Fail On Error**_ ativadas.

6\. Clique em Confirmar.

7\. Faça o _deploy_ do _pipeline_.

8\. O _pipeline_ vai receber um _payload_ como este:

```
{
"rawData": "Test for encryption",
"signed": "...032281762E01B6C50C1DE825A2FD5A177CCFD5C1DB54E...."
}
```

\
9\. O resultado do teste executado vai aparecer conforme demonstrado abaixo:

```
{
"success": true
}
```
