---
description: >-
  Saiba mais sobre a Política de acesso à APIs internas da Digibee Integration
  Platform.
---

# Política de acesso à APIs internas

{% hint style="info" %}
A Política de acesso à APIs internas está atualmente em fase beta. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

As chaves de API internas são padrões de segurança usados para chamadas de API que permitem acesso seguro aos pipelines.

Você pode escolher entre 3 opções para cada ambiente, como descrito abaixo:

* **Usar chave de API:** todos os pipelines que usam um trigger que exponha o seu pipeline a chamadas internas devem utilizar uma chave. Habilite essa opção ao configurar um trigger.
* **Usar Token JWT:** todos os pipelines que usam um trigger que exponha o seu pipeline a chamadas internas devem usar um token JWT. Esse processo se assemelha e tem o mesmo efeito que o anterior.
* **Chave de API, Token JWT ou nenhum:** esta opção permite a escolha entre usar ou não uma das opções acima. Recomendamos a utilização de pelo menos uma delas.

Confira na imagem abaixo como visualizar as alternativas e selecionar uma para cada ambiente. Caso tenha dúvidas, escolha a terceira opção.

<figure><img src="../../../.gitbook/assets/internas pt.png" alt=""><figcaption></figcaption></figure>

## Como funciona

Uma vez configurada a sua política de **Chave de API**, cada novo pipeline deve seguir as regras de acordo com as suas definições. Caso a política não seja aplicada, a pessoa que criou o pipeline será lembrada durante a fase de implantação. Em outras palavras, não é possível implantar o pipeline até a correção do problema.&#x20;

[Para saber mais sobre conceitos, visite o artigo Políticas.](https://docs.digibee.com/documentation/governance/policies)

Para habilitar sua API Key ou seu Token JWT no trigger de seu pipeline, ative o botão conforme imagem abaixo:

<figure><img src="../../../.gitbook/assets/Trigger (1).png" alt=""><figcaption></figcaption></figure>

## Criando sua Chave de API

Agora que você tem sua política e um pipeline configurado para usar uma **Chave de API**, você pode criar uma nova chave ou usar uma já existente ao acessar a página Consumers (Chaves de API) no menu **Configurações**.&#x20;

Depois de criar sua chave de API, lembre-se de associá-la ao seu pipeline em ambos os ambientes.

[Saiba mais na documentação de Consumers (Chaves de API).](https://docs.digibee.com/documentation/v/pt-br/settings/chaves-de-api-consumers)

## Criando seu Token JWT

Ao optar pelo uso de **Tokens JSON Web**, é preciso criar um segundo pipeline que funcionará como seu fluxo de login. O fluxo de login vai gerar o JWT que será utilizado em suas chamadas de API.

[Saiba mais sobre  Implementação na documentação de Digibee JWT (Generate and Decode)](https://docs.digibee.com/documentation/v/pt-br/components/security-components/digibee-jwt/implementacao-do-digibee-jwt).

\
