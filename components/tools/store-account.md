---
description: Saiba como armazenar contas de forma dinâmica.
---

# Store Account (Beta Restrito)

{% hint style="info" %}
Essa _feature_ está em fase Beta Restrito e está disponível apenas para clientes específicos.
{% endhint %}

O **Store Account** é um componente exclusivo do [Pipeline Engine v2](https://docs.digibee.com/documentation/v/pt-br/run/pipeline-engine-change/how-to-change-the-version-of-the-pipeline-engine-restricted-beta). Ele opera um papel crítico no armazenamento seguro e dinâmico de contas localmente, e posteriormente em um _Vault_. Para habilitar o uso dinâmico de contas em diferentes componentes, você deve seguir um processo de dois passos:

1. Armazenar a conta desejada usando o componente **Store Account**.
2. Referenciar o nome da conta no componente em que pretende usá-lo.

Isso garante um acesso contínuo e seguro às contas necessárias em diferentes funcionalidades.

Dê uma olhada nos parâmetros de configuração do componente:

* **Account Name:** o nome da conta que será armazenada.
* **Account Type:** o tipo de conta que será armazenada. Contas suportadas: _API Key, AWS V4, Basic, Certificate Chain, Custom Auth Header, Google Key, Oauth Bearer Token, Private Key, Public Key, Secret Key, SMTP Auth_ e _NTLM_.
*   **Scoped:** quando a opção estiver ativada, a conta armazenada é isolada para outro sub-processo. Nesse caso, os sub-processos verão sua própria versão dos dados da conta armazenada.&#x20;

    \
    Para saber mais sobre a funcionalidade **Scoped**, leia a [documentação de Suporte a credenciais dinâmicas](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito).

Para armazenar a conta você deve preencher os campos, que podem variar dependendo do tipo de conta. Veja todos os campos disponíveis para um tipo específico de conta [na documentação de Contas (Accounts).](https://docs.digibee.com/documentation/v/pt-br/configurations/contas-accounts)

{% hint style="info" %}
**Nota:** os tipos de contas Kerberos and Oauth2 ainda não são supportados para uso dinâmico.
{% endhint %}

## Como configurar o Store Account?

**Account Name:** test-db

**Account Type:** Basic

**Username:** \<DB USERNAME>

**Password:** \<DB PASSWORD>

## Exemplos de uso

Por exemplo, vamos supor que seja necessário autenticar em um banco dedados usando uma credencial _Basic_. Siga os passos na sequência abaixo:

1. Configure o **Store Account** para criar essa credencial a ser usada no componente **DB V2**.
2. Conecte o componente **DB V2** e configure os dados corretos do banco de dados a ser acessado.
3. Configure os seguintes parâmetros no **DB V2**:

* ativar o parâmetro **Use Dynamic Account**.
* **Account Name:** test-db.

Após seguir as etapas de configuração, você pode usar dinamicamente o acesso a esse banco de dados.
