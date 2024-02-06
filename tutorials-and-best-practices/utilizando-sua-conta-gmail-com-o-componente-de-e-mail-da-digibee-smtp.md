---
description: >-
  Aprenda como configurar o uso de uma conta pessoal do Gmail ao usar a Digibee
  Integration Platform.
---

# Como usar sua conta do Gmail com o componente de e-mail Digibee (SMTP)

É bastante útil ter sua própria conta Gmail para fazer envios através do componente de e-mail da Digibee, SMTP.

{% hint style="info" %}
A abordagem descrita não é recomendada para ambientes produtivos. Leve em consideração que este artigo trata de um tipo de conta obsoleta. Leia o artigo sobre o [componente Email V2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/email-v2) e entenda o novo modelo de envio de email.
{% endhint %}

## Configurando a conta (_account_) <a href="#h_fc54f2134b" id="h_fc54f2134b"></a>

Para configurar sua Conta Google com o componente SMTP, acesse a Digibee Integration Platform e siga os passos abaixo:

1. Clique no ícone de **Administration**, no canto superior direito da Plataforma.

<figure><img src="../.gitbook/assets/Administration screen shot.png" alt=""><figcaption></figcaption></figure>

2. Clique em **Accounts** no menu ao lado esquerdo da tela.

<figure><img src="../.gitbook/assets/Accounts Acreen.png" alt=""><figcaption></figcaption></figure>

3. Insira as configurações da sua conta do Gmail conforme imagem abaixo:

<figure><img src="../.gitbook/assets/accounts.png" alt=""><figcaption></figcaption></figure>

4. Observe a configuração do nome da Conta (Label) e do tipo (Type).
5. Defina um nome para a conta que depois será utilizada pelo componente de e-mail.
6. Escolha o tipo _smtp-auth-and-properties_.
7. Clique em **CONFIRM**.

### Autorizando o Gmail <a href="#h_74cf14b45a" id="h_74cf14b45a"></a>

Os envios serão feitos através de SMTP, considerado pelo Gmail um canal menos seguro. Portanto, é necessário autorizar o Gmail a oferecer suporte a aplicativos não seguros.

Leia a [documentação oficial do Google](https://support.google.com/accounts/answer/6010255?hl=pt-BR) para saber como autorizar o Gmail a suportar aplicações não seguras.

### Obtendo o link de autorização <a href="#h_a08765b7d7" id="h_a08765b7d7"></a>

É possível que o Gmail envie um link de autorização na primeira execução do componente de e-mail. Se isso acontecer, você receberá um erro na primeira execução do seu _pipeline_.

### Conta com duplo fator de autenticação <a href="#h_2100257aae" id="h_2100257aae"></a>

É recomendável que você utilize o duplo fator de autenticação na sua conta. Para isso, é necessário criar uma senha de aplicativo.

Leia a [documentação do Google ](https://support.google.com/accounts/answer/185833?hl=pt-BR)para saber como criar uma senha de aplicativo.
