---
description: >-
  Descubra como os usuários podem configurar o Dropbox Connector e como ele é
  usado no Digibee iPaaS com este guia passo a passo.
---

# Configurando Account Dropbox

## Obtendo um _access token_ <a href="#obtendo-um-access-token" id="obtendo-um-access-token"></a>

A autenticação no _Dropbox_ é feita através de _access token._

Conclua as etapas a seguir para obter um _token_ de acesso que possa ser usado no _Dropbox Connector_:

### _Create app_

1. Acesse [https://www.dropbox.com/developers/apps](https://www.dropbox.com/developers/apps).
2. Clique em **Create app;**

![](<../../.gitbook/assets/01 (12).png>)

3. Escolha um dos tipos de API;&#x20;
4. Depois um dos tipos de acesso;&#x20;
5. E por último, o nome do seu _app_;&#x20;
6. Em seguida, clique em _**Create app**_ para finalizar esta etapa.

![](<../../.gitbook/assets/02 (16).png>)

### _Generate token_

1. Após clicar em _**Create app**_, você será redirecionado para a página de configurações do seu novo app, conforme imagem abaixo:

![](<../../.gitbook/assets/03 (2).png>)

2. &#x20;Em seguida, clique em _**Generate**_ na seção **OAuth 2**. Isso lhe dará seu _token_ de acesso:

![](<../../.gitbook/assets/04 (6).png>)

3. Seu _token_ de acesso foi gerado._:_

![](<../../.gitbook/assets/05 (14).png>)

### Criando uma Conta (_Account_)

Agora_,_ na plataforma, precisamos criar um Conta (_Account)_ com o tipo de conta **oauth-bearer** e inserir o _access token_ gerado, como a seguir:

![](<../../.gitbook/assets/06 (3).png>)

Pronto, temos nosso _access token_ configurado e nossa Conta (_Account)_ criada e pronta para uso no _Dropbox Connector_:

![](<../../.gitbook/assets/07 (4).png>)
