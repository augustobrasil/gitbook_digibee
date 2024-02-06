---
description: Conheça o componente e saiba como utilizá-lo.
---

# JWT V2

O _**JWT V2**_ permite a criação de _tokens_ JWS e JWE. O componente também realiza a verificação de _tokens_ JWS e decodificação de _tokens_ JWE.

Dê uma olhada nos parâmetros de configuração deste componente:

* **Operation:** a operação que será realizada pelo componente. As opções são:
  * **Generate JWS:** realiza a criação de _tokens_ JWS.
  * **Generate JWE:** realiza a criação de _tokens_ JWE.
  * **Verify JWS:** verifica a assinatura de um _token_ JWS.
  * **Decode JWE:** descriptografa o _token_ JWE e retorna o _payload_ desse _token_.
* **Public Key:** conta do tipo _public key_ utilizada para verificar _tokens_ JWS e criptografar _tokens_ JWE. Para algoritmos baseados em RSA, é esperada uma _public key_ do tipo RSA (derivada de uma _secret key_ de no mínimo 2048 bits). Para algoritmos baseados em EC, é esperada uma _public key_ do tipo EC com a respectiva configuração de Curva (_Curve_). Veja a seguir a lista de algoritmos disponíveis para este parâmetro:

| Public Key          | RSA                                                                      | EC                                                                               |
| ------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| Algoritmos para JWS | <p>RS256</p><p>RS384</p><p>RS512</p><p>PS256</p><p>PS384</p><p>PS512</p> | <p>ES256</p><p>ES384</p><p>ES512</p><p>ES256K</p>                                |
| Algoritmos para JWE | <p>RSA1_5</p><p>RSA-OAEP </p><p>RSA-OAEP-256</p>                         | <p>ECDH-ES </p><p>ECDH-ES+A128KW </p><p>ECDH-ES+A192KW </p><p>ECDH-ES+A256KW</p> |

* **Private Key:** conta do tipo _private key_ utilizada para assinar _tokens_ JWS e descriptografar _tokens_ JWE. Para algoritmos baseados em RSA, é esperado uma _private key_ do tipo RSA de no mínimo 2048 bits. Para algoritmos baseados em EC, é esperado uma _private key_ do tipo EC com a respectiva configuração de Curva (_Curve_). Veja a seguir a lista de algoritmos disponíveis para este parâmetro:

| Private Key         | RSA                                                                      | EC                                                                               |
| ------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| Algoritmos para JWS | <p>RS256</p><p>RS384</p><p>RS512</p><p>PS256</p><p>PS384</p><p>PS512</p> | <p>ES256</p><p>ES384</p><p>ES512</p><p>ES256K</p>                                |
| Algoritmos para JWE | <p>RSA1_5</p><p>RSA-OAEP </p><p>RSA-OAEP-256</p>                         | <p>ECDH-ES </p><p>ECDH-ES+A128KW </p><p>ECDH-ES+A192KW </p><p>ECDH-ES+A256KW</p> |

* **Secret Key:** conta do tipo _secret key_ utilizada para assinar/verificar tokens JWS e criptografar/descriptografar tokens JWE. Veja a seguir a lista de algoritmos disponíveis para este parâmetro:

| Secret Key          | HMAC                                 | AES                                       | AES GCM                       |
| ------------------- | ------------------------------------ | ----------------------------------------- | ----------------------------- |
| Algoritmos para JWS | <p>HS256</p><p>HS384</p><p>RS512</p> |                                           |                               |
| Algoritmos para JWE |                                      | <p>A128KW </p><p>A192KW </p><p>A256KW</p> | A128GCMKW A192GCMKW A256GCMKW |

* **Key as Base64:** se esta opção estiver ativada, a conta _secret key_ deverá estar no formato base64; do contrário, deverá conter o valor da chave a ser utilizada. Esse parâmetro será visível apenas se uma conta _secret key_ for utilizada.
* **Key Charset:** o _charset_ da chave. Disponível se **Key as Base64** estiver ativada.
* **JWS Algorithm (JWA):** o algoritmo utilizado para assinar e verificar _tokens_ JWS. As opções são: HS256, HS384, HS512, RS256, RS384, RS512, PS256, PS384, PS512, ES256, ES384, ES512, ES256K e EdDSA (_JWK only_). Esse parâmetro não fica disponível se **Verify JWS** estiver configurado no parâmetro **Operation** e se **Use JWK** estiver ativado.

{% hint style="info" %}
**IMPORTANTE:** o algoritmo EdDSA funciona apenas quando um _token_ JWK é utilizado.
{% endhint %}

* **JWE Algorithm (JWA):** o algoritmo utilizado para criptografar e descriptografar _tokens_ JWE. As opções são: A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW, A256GCMKW, RSA1\_5, RSA-OAEP, RSA-OAEP-256, ECDH-ES, ECDH-ES+A128KW, ECDH-ES+A192KW e ECDH-ES+A256KW. Esse parâmetro não fica disponível se **Decode JWE** estiver configurado no parâmetro **Operation** e se **Use JWK** estiver ativado.
* **Set algorithm from JWK:** se esta opção estiver ativada, o componente utilizará o algoritmo configurado no JWK para manipular os tokens JWT. Esse parâmetro será visível apenas se **Use JWK** for ativado.
* **Content Encryption Algorithm:** o algoritmo utilizado para criptografar e descriptografar o _payload_ dos _tokens_ JWE. As opções são: A128CBC-HS256, A192CBC-HS384, A256CBC-HS512, A128GCM, A192GCM e A256GCM.
* **Issuer (iss):** a _claim_ "iss" (_issuer_) identifica o emissor do JWT. O processamento dessa _claim_ é geralmente específico da aplicação. O uso dessa _claim_ é opcional.
* **Expiration Time (exp):** a _claim_ "exp" (_expiration time_) identifica o tempo de expiração no qual ou após o qual o JWT não deve ser aceito para processamento. O processamento da solicitação "exp" exige que a data/hora atual sejam anteriores à data/hora de vencimento listada na solicitação "exp". O uso dessa _claim_ é opcional.
* **Issued at (iat)**: a _claim_ "iat" (_Issued at_) identifica a hora em que o JWT foi emitido (formato _timestamp_). Essa declaração pode ser utilizada para determinar a idade do JWT. O seu valor deve ser um número. O uso dessa _claim_ é opcional.
* **Subject (sub):** a _claim_ "sub" (_subject_) identifica o assunto do JWT. As afirmações em um JWT são normalmente afirmações sobre o assunto. O valor do assunto deve ter como escopo ser exclusivo localmente no contexto do emissor ou ser globalmente exclusivo. O processamento dessa _claim_ é geralmente específico da aplicação. O uso dessa _claim_ é opcional.
* **Token Id (jti):** a _claim_ "jti" (JWT ID) fornece um identificador exclusivo para o JWT. O valor do identificador deve ser atribuído para diminuir as chances de que o mesmo valor seja acidentalmente atribuído a um objeto de dados diferentes. Se o aplicativo utilizar vários emissores, você também pode evitar colisões entre os valores produzidos por diferentes emissores. Use a _claim_ "jti" para evitar que o JWT seja repetido. O uso dessa _claim_ é opcional.
* **Audience (aud):** valor único. A _claim_ "aud" (_audience_) identifica os destinatários do JWT. Cada destinatário que pretende processar o JWT deve se identificar com um valor dentro da _claim_. Se destinatário não se identificar com um valor na _claim_ "aud" quando essa _claim_ estiver presente, o JWT deve ser rejeitado. O uso dessa _claim_ é opcional.
* **Not Before (nbf):** a _claim_ "nbf" (_not before_) identifica o tempo antes do qual o JWT não deve ser aceito para processamento. O processamento da reclamação "nbf" requer que a data/hora atual (formato _timestamp_) seja posterior ou igual à data/hora listada na reclamação "nbf". Os implementadores podem prever uma pequena margem de segurança - geralmente não mais do que alguns minutos - para compensar a distorção do relógio. O seu valor deve ser um número. O uso dessa _claim_ é opcional.

{% hint style="info" %}
**IMPORTANTE:** para os parâmetros **Expiration Time, Issued at** e **Not Before**, você sempre deve inserir os dados em milissegundos. Embora este formato seja obrigatório nesses casos, o conteúdo JWT contém o valor em segundos com base nos padrões JWT (_JSON Web Token_).
{% endhint %}

* **Custom Claims:** para especificar _claims_ customizadas, informe a chave (nome da _claim_) e o valor da _claim_.
* **Custom Headers:** para especificar _headers_ customizados, informe a chave e o valor do _header_ nos respectivos campos.
* **JWE:** o _token_ JWE.
* **JWS:** o _token_ JWS.
* **Payload Charset**: _charset_ do _payload_ utilizado na criação de _tokens_ JWE. Valor padrão: UTF-8.
* **Payload**: _payload_ que será utilizado na criação do _token_ JWE.
* **Use JWK:** se a opção estiver ativada, um JWK é esperado para assinar/verificar o _token_ JWS ou criptografar/descriptografar o _token_ JWE. O **Use JWK** também desabilita todas as opções de conta (parâmetros **Secret Key, Private Key** e **Public Key**), além dos parâmetros **Key Charset e Key as Base64**. Caso **Decode JWE** seja selecionada em **Operation**, o parâmetro **Encrypted Payload Algorithm** também será desativado.
* **JWK:** JWK que será utilizado na assinatura ou verificação do _token_ JWS e na criptografia ou descriptografia do _token_ JWE.
* **Fail On Error:** se a opção estiver habilitada, a execução do _pipeline_ com erro será interrompida; do contrário, a execução do _pipeline_ continua, mas o resultado vai mostrar um valor falso para a propriedade "success".

{% hint style="info" %}
**IMPORTANTE:** alguns algoritmos exigem chaves com configurações específicas (_public, private_ ou _secret key_), como é o caso dos algoritmos HMAC e EC para _tokens_ JWS. O algoritmo HS256, por exemplo, exige uma _secret key_ de 256+ bits, enquanto o algoritmo ES384 espera uma _public key_ configurada com Curva (_Curve)_ P-384. Fique atento ao fazer esse tipo de configuração para garantir que os _tokens_ JWT sejam manipulados de maneira correta.

O componente **JWT V2** segue as especificações e padrões JWT (_JSON Web Token_) e JOSE (_Javascript Object Signing and Encryption_). Configurações fora dessas especificações e padrões não são suportadas pelo componente.
{% endhint %}

Alguns dos parâmetros acima aceitam _Double Braces_. Para entender melhor como funciona essa linguagem, [leia a documentação sobre Double Braces](../../build/double-braces/).

## **Fluxo de mensagens**

### **Entrada**

Não é esperado uma mensagem de entrada específica, bastando apenas preencher os campos necessários de cada operação.

### **Saída**

### **Operação **_**Generate JWS**_

```
{
"success": true,
"jws": "<JWS TOKEN>",
}
```

### **Operação **_**Generate JWE**_

```
{
"success": true,
"jwe": "<JWE TOKEN>",
}
```

### **Operação **_**Verify JWS**_

```
{
"success": true,
"verified": true,
"claims": [
"subject": ".....",
"issuedAt": 11111111
]
}
```

### **Operação **_**Decode JWE**_

```
{
"success": true,
"payload": "<PAYLOAD DESCRIPTOGRAFADO>"
}
```
