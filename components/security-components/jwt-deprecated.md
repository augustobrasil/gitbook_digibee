---
description: >-
  Descubra mais sobre o componente JWT e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# JWT (Descontinuado)

{% hint style="info" %}
O componente JWT foi descontinuado e não recebe mais atualizações. Por favor, acesse o documento com a versão mais recente da funcionalidade: [JWT V2](jwt-v2.md).
{% endhint %}

O **JWT** realiza criação de JWS e JWE assim como a verificação de JWS e decodificação de JWE.

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="393">Descrição</th><th width="134.75">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td><em>Generate JWS</em> realiza a criação de <em>tokens</em> JWS. <em>Generate JWE</em> realiza a criação de <em>tokens</em> JWE. <em>Verify JWS</em> verifica a assinatura de um <em>token</em> JWS e <em>Decode JWE</em> descriptografa o <em>token</em> JWE e retorna o <em>payload</em> desse <em>token</em>.</td><td><em>Generate JWS</em></td><td><em>String</em></td></tr><tr><td><strong>Public Key</strong></td><td>Conta do tipo <em>PUBLIC-KEY</em> utilizada para assinar <em>tokens JWS</em> com os seguintes algoritmos: <em>RS256, RS384, RS512, PS256, PS384</em> e <em>PS512</em>. Utilizada também para criptografar <em>tokens JWE</em> com os seguintes algoritmos: R<em>SA1_5, RSA-OAEP</em> e <em>RSA-OAEP-256</em>. A chave pública deverá ser do tipo <em>RS</em>A e derivada de uma chave privada de no mínimo 2048 <em>bits</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Private Key</strong></td><td>Conta do tipo <em>PRIVATE-KEY</em> utilizada para verificar <em>tokens JWS</em> com os seguintes algoritmos: <em>RS256, RS384, RS512, PS256, PS384</em> e <em>PS512</em>. Utilizada também para descriptografar <em>tokens JWE</em> com os seguintes algoritmos: <em>RSA1_5, RSA-OAEP</em> e <em>RSA-OAEP-256</em>. A chave privada deverá ser do tipo RSA e de no mínimo 2048 <em>bits</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Secret Key</strong></td><td>Conta do tipo <em>SECRET-KEY</em> utilizada para assinar <em>tokens JWS</em> com os seguintes algoritmos: <em>HS256, HS384</em> e <em>HS512</em>. Utilizada também para criptografar e descriptografar <em>tokens JWE</em> com os seguintes algoritmos: <em>A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW</em> e <em>A256GCMKW</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Key as Base64</strong></td><td>Se habilitada, a conta <em>Secret Key</em> deverá estar no formato base64; do contrário, deverá conter o valor da chave a ser utilizada.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Key Charset</strong></td><td>Se a propriedade <em>Key as Base64</em> estiver habilitada, o <em>charset</em> da chave deve ser informado.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>JWS Algorithm</strong></td><td>Algoritmos utilizados para assinar e verificar <em>tokens JWS</em>, sendo eles: <em>HS256, HS384, HS512, RS256, RS384, RS512, PS256, PS384</em> e <em>PS512</em>.</td><td>HS256</td><td>N/A</td></tr><tr><td><strong>JWE Algorithm</strong></td><td>Algoritmos utilizados para criptografar e descriptografar <em>tokens JWE,</em> sendo eles: <em>A128KW, A192KW, A256KW, A128GCMKW, A192GCMKW, A256GCMKW, RSA1_5, RSA-OAEP</em> e <em>RSA-OAEP-256.</em></td><td>RSA-OAEP</td><td>N/A</td></tr><tr><td><strong>Encrypted Payload Algorithm</strong></td><td>Algoritmos utilizados para criptografar e descriptografar o <em>payload</em> dos <em>tokens JWE</em>, sendo eles: <em>A128KW, A192KW, A256KW e A256GCM</em>.</td><td>A128KW</td><td>N/A</td></tr><tr><td><strong>Issuer (iss)</strong></td><td>A <em>claim iss (issuer</em>) identifica o principal que emitiu o JWT. O processamento dessa <em>claim</em> é geralmente específico da aplicação. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Expiration Time (exp)</strong></td><td>A <em>claim exp (expiration time</em>) identifica o tempo de expiração no qual ou após o qual o JWT não deve ser aceito para processamento. O processamento da solicitação <em>exp</em> exige que a data / hora atual devem ser anteriores à data / hora de vencimento listada na solicitação <em>exp</em>. O uso dessa claim é opcional.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Issued at (iat)</strong></td><td>A <em>claim iat (Issued at</em>) identifica a hora em que o JWT foi emitido. Essa declaração pode ser utilizada para determinar a idade do JWT. O seu valor deve ser um número. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Subject (sub)</strong></td><td>A <em>claim sub (subject)</em> identifica o assunto do JWT. As afirmações em um JWT são normalmente afirmações sobre o assunto. O valor do assunto deve ter como escopo ser exclusivo localmente no contexto do emissor ou ser globalmente exclusivo. O processamento dessa <em>claim</em> é geralmente específico da aplicação. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Token Id (jti)</strong></td><td>A <em>claim jti (JWT ID)</em> fornece um identificador exclusivo para o JWT. O valor do identificador deve ser atribuído de maneira a diminuir ao máximo as chances de que o mesmo valor seja acidentalmente atribuído a um objeto de dados diferentes. Se o aplicativo utilizar vários emissores, as colisões devem ser evitadas também entre os valores produzidos por diferentes emissores. A <em>claim jti</em> pode ser utilizada para evitar que o JWT seja repetido. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Audience (aud)</strong></td><td>Valor único. A <em>claim aud</em> (público) identifica os destinatários do JWT. Cada principal que pretende processar o JWT deve se identificar com um valor dentro da reivindicação dentro da <em>claim</em>. Se o responsável pelo processamento da claim não se identificar com um valor na <em>claim</em> <em>aud</em> quando essa <em>claim</em> estiver presente, o JWT DEVE ser rejeitado. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Not Before (nbf)</strong></td><td>A <em>claim nbf</em> (não antes) identifica o tempo antes do qual o JWT não deve ser aceito para processamento. O processamento da reclamação <em>nbf</em> requer que a data / hora atual SEJA posterior ou igual à data / hora não anterior listada na reclamação <em>nbf</em>. Os implementadores PODEM prever uma pequena margem de segurança - geralmente não mais do que alguns minutos - para compensar a distorção do relógio. O seu valor DEVE ser um número. O uso dessa <em>claim</em> é opcional.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Custom Claims</strong></td><td>Para especificar <em>claims</em> customizadas basta informar a chave (nome da <em>claim</em>) e o valor da <em>claim</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Custom Headers</strong></td><td>Para especificar headers customizados, basta informar a chave e o valor do <em>header</em> nos respectivos campos.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JWE</strong></td><td>Campo para informar o <em>token JWE</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>JWS</strong></td><td>Campo para informar o <em>token JWS</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Payload Charset</strong></td><td>Charset do <em>payload</em> utilizado na criação de <em>tokens JWE</em>. Valor padrão: <em>UTF-8</em></td><td><em>UTF-8</em></td><td><em>String</em></td></tr><tr><td><strong>Payload</strong></td><td><em>Payload</em> que será utilizado na criação do <em>token JWE.</em></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Use JWK</strong></td><td>Se a opção estiver habilitada, um JWK é esperado para verificar o token JWT. Esta opção está disponível apenas se <em>Verify JWS</em> estiver selecionada no parâmetro <strong>Operation</strong>. O <strong>Use JWK</strong> também desabilita todas as opções de conta (parâmetros <strong>Secret Key,</strong> <strong>Private Key</strong> e <strong>Public Key</strong>), além dos parâmetros <strong>Key Charset</strong>, <strong>Key as Base64</strong> e <strong>JWS Algorithm</strong>.</td><td>False</td><td>Booleano</td></tr><tr><td><strong>JWK</strong></td><td>JWK que será utilizado para verificar o <em>token JWS.</em></td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado mostrará um valor falso para a propriedade <em>success</em>.</td><td>False</td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens <a href="#h_a232432467" id="h_a232432467"></a>

### **Entrada** <a href="#h_eec5380fa4" id="h_eec5380fa4"></a>

Não é esperado uma mensagem de entrada específica, bastando apenas preencher os campos necessários de cada operação.

### Saída <a href="#h_cd13e15440" id="h_cd13e15440"></a>

Para as operações “_Generate JWS_”:

```
{
"success": true,
"jws": "<JWS TOKEN>",
}
```

Para as operações “_Generate JWE_":

```
{
"success": true,
"jwe": "<JWE TOKEN>",
}
```

Para as operações “_Verify JWS_":

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

Para as operações “_Decode JWE_":

```
{
"success": true,
"payload": "<PAYLOAD DESCRIPTOGRAFADO>"
}
```

