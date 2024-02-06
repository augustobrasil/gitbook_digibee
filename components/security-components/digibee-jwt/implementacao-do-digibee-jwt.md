---
description: Veja alguns exemplos de uso do componente.
---

# Implementação do Digibee JWT (Generate and Decode)

A utilização mais comum do JWT acontece durante a autorização de um serviço exposto na rede via protocolo HTTP.

Com esse passo-a-passo sobre o uso do _token_ JWT, você pode aproveitar para customizar a segurança nos seus próximos _pipelines_. [Para conhecer o componente _Digibee JWT (Generate and Decode)_ mais a fundo, clique aqui.](https://docs.digibee.com/documentation/v/pt-br/components/security-components/digibee-jwt)

Agora, veja a ilustração a seguir, que mostra a forma e a arquitetura do padrão:

![](<../../../.gitbook/assets/implementação jwt (1).png>)

Para acessar os serviços, é necessário realizar o _login_ em um _pipeline_, que ficará responsável pela geração do _token_ JWT. Com esse _token_ em mãos, você tem acesso às rotas, aos serviços e aos recursos permitidos.

Sabia que você também pode utilizar o padrão dentro da Plataforma para garantir a segurança dos fluxos? Veja como.

## Montando um _pipeline_ para fazer _login_ e construir o JWT <a href="#montando-um-pipeline-para-fazer-login-e-construir-o-jwt" id="montando-um-pipeline-para-fazer-login-e-construir-o-jwt"></a>

O primeiro passo é configurar o _trigger_ para _login_:

* entre nas configurações do _trigger_ e selecione a opção REST;
* ative as opções _**External API**_ e _**API Key.**_

Se você tiver alguma dúvida sobre como preencher os campos mencionados acima, [clique aqui para consultar o nosso artigo sobre REST Trigger.](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger)

Com o _trigger_ configurado, você pode construir o fluxo utilizando os componentes necessários para a criação do _token_. Mas não se preocupe - existe um componente específico que gera o _token_ JWT. Acompanhe como fazer:

* arraste o ícone do _**Digibee JWT (Generate and Decode)**_ para a sua área de construção;
* selecione a _Operation_ _**Generate**_ para a criação do _token_;
* nos campos _Scopes_ e _Expiration_, aplique as regras que melhor atendem o seu negócio.

## **Utilizando o Assert** <a href="#utilizando-o-assert" id="utilizando-o-assert"></a>

Para utilizar o componente _**Assert**_ para criar uma validação por usuário e senha pré-cadastrados na Plataforma, insira o seguinte código no campo CONDITION:

```
#{body.user} == #{globals.user} && #{body.password} == #{globals.password}
```

{% hint style="info" %}
**Importante :** a geração do _token_ JWT não é feita no Painel de execução. Isso só é possível quando o _pipeline_ é publicado em algum dos ambientes (Test ou Prod).
{% endhint %}

## Chamando o _pipeline_ para o _login_ <a href="#chamando-o-pipeline-para-o-login" id="chamando-o-pipeline-para-o-login"></a>

Depois que você terminar as configurações, é necessário implantar o _pipeline_ no seu devido ambiente de teste ou produção para poder testar o fluxo. Se você tiver alguma dúvida mais específica sobre implantação de _pipelines_ na Plataforma, [clique aqui para ler o nosso artigo sobre o assunto.](https://docs.digibee.com/documentation/v/pt-br/build/pipelines)

Lembre-se que todos os fluxos implantados na Digibee com _trigger_ tipo REST ou HTTP (e seus derivados) precisam fazer uso de _API Key_. Com o _login_ não é diferente.&#x20;

Com a API Key configurada, você pode dar início ao teste. Veja, no exemplo a seguir, como fazer isso utilizando o _postman_. Mas lembre-se: você pode usar o _client_ que está acostumado ou qualquer outra aplicação que preferir.

O que você deve fazer é:

* passar a API Key no _header_ da chamada;
* passar o _user_ e a _password_ configurados como obrigatórios no fluxo.

![](<../../../.gitbook/assets/image (1).png>)

Ao realizar essa chamada, o serviço retorna o _status_ de sucesso:

![](<../../../.gitbook/assets/image (1) (1).png>)

Busque a informação necessária nos _headers_ da resposta, no campo _Authorization_ - essa é a autenticação, ou seja, o JWT gerado que será utilizado em combinação com a API Key para outros fluxos que utilizam os _triggers_ de API REST e HTTP.

## Configurando o _trigger_ para os fluxos com a nova autenticação como chave <a href="#configurando-o-trigger-para-os-fluxos-com-a-nova-autenticao-como-chave" id="configurando-o-trigger-para-os-fluxos-com-a-nova-autenticao-como-chave"></a>

Comece fazendo configurações necessárias no _trigger_. Para isso, ative as opções _ExternalAPI_, _API Key_ e _Token JWT._ Dessa maneira, sempre que as rotas forem chamadas, será preciso informar a _API Key_ e o _token_ JWT gerados.

Se você informar a _API Key_ e não informar o _token_, então um erro de autorização é retornado:

![](<../../../.gitbook/assets/image (2) (1).png>)

