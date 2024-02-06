---
description: Saiba mais sobre o fluxo de login da Digibee Integration Platform.
---

# Fluxo de login

Existem duas maneiras de fazer login na Digibee Integration Platform:

* [Usando credenciais Digibee](./#\_3ingd8lvv5ai)
* [Usando um provedor de identidade (IdP)](./#\_crldaax16nm3)

## Logins com credenciais Digibee <a href="#id-3ingd8lvv5ai" id="id-3ingd8lvv5ai"></a>

### Primeiro acesso <a href="#qkx2jfexd4bk" id="qkx2jfexd4bk"></a>

Para acessar a Digibee Integration Platform pela primeira vez, peça ao seu gestor de acesso para **criar um usuário** para você. Para saber como criar um usuário, [leia nossa documentação](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/basic-concepts-about-users).

Depois que seu gestor de acesso criar o usuário, você receberá **um email solicitando que você defina uma senha de acesso**. Siga as instruções no email.

Depois de configurar sua senha de acesso, faça o login na Digibee Integration Platform usando suas credenciais e informando o _realm_ que deseja acessar. Se a autenticação em duas etapas estiver ativada, também será solicitado a você fornecer um código de verificação.

#### **Política de senhas**

Abaixo você encontra os critérios da política de senhas vigente da Digibee Integration Platform:

* Tamanho mínimo de **8 caracteres**.
* Tamanho máximo de **16 caracteres**.
* Conter pelo menos **1 letra maiúscula**.
* Conter pelo menos **1 letra minúscula**.
* Conter pelo menos **1 caractere especial**.
* Conter pelo menos **1 número**.
* Política de **expiração a cada** **15 dias**.
* Política de **não aceitar as 3 últimas senhas usadas**.

![](<../../../.gitbook/assets/image (24) (1).png>)

{% hint style="info" %}
Em alguns casos, a Digibee detecta seu _realm_ automaticamente. Neste caso, você só precisa inserir seu email e senha.
{% endhint %}

{% hint style="warning" %}
Logins com credenciais Digibee podem ser bloqueados pelos gestores de acesso do seu _realm_. Nesse caso, você deve [fazer login com um IdP](./#\_crldaax16nm3). Você pode ler mais sobre isso em nosso [artigo Regras de autenticação](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/idp-accesses).
{% endhint %}

### Senha expirada <a href="#do8r0fno659h" id="do8r0fno659h"></a>

Por razões de segurança, **a Digibee exige que seus usuários alterem suas senhas a cada 15 dias**. Se você tentar fazer login usando uma senha expirada, você será redirecionado para a tela de redefinição de senha.

## Logins usando um provedor de identidade (IdP) <a href="#crldaax16nm3" id="crldaax16nm3"></a>

Além de usar as credenciais Digibee, você também pode fazer login com IdP. Este IdP deve ser previamente integrado à Digibee. Para saber mais sobre isso, leia nosso artigo sobre [integração do provedor de identidade](../../identity-provider-integration/).

Para fazer login na Digibee Integration Platform usando um IdP, primeiro faça login no seu IdP. Em seguida, ao efetuar login na Digibee Integration Platform, clique no botão referente ao IdP que você está utilizando, conforme a imagem abaixo.

<figure><img src="../../../.gitbook/assets/image (26) (1).png" alt=""><figcaption><p>Página de login com provedor de identidade</p></figcaption></figure>

### Melhores práticas ao fazer login <a href="#a77cp97ohqcd" id="a77cp97ohqcd"></a>

* Certifique-se de que seu navegador esteja atualizado.
* Desative _plugins_ que possam entrar em conflito com o reCAPTCHA.
* Remova ou desative extensões que executam automações.
* Exclua _cookies_ e/ou dados do histórico do navegador.
* Habilite a autenticação de dois fatores da Digibee Integration Platform. Para saber mais, leia a nossa documentação sobre[ como habilitar e desabilitar a autenticação de dois fatores.](https://docs.digibee.com/documentation/v/pt-br/administration/user-authentication-and-autorization/verificacao-em-duas-etapas)
