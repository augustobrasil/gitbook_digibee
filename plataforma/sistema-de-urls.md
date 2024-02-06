---
description: >-
  Saiba como a Digibee Integration Platform usa um conjunto de URLs para criar,
  publicar e monitorar pipelines de integração.
---

# Sistema de URLs

Um Uniform Resource Locator (URL) funciona como um endereço para um recurso da Internet. A Digibee Integration Platform utiliza um conjunto de URLs para identificar seus recursos e pode ser utilizada por _pipelines_ para receber solicitações.

URLs são usados pelo portal da web para criar, publicar e monitorar _pipelines_ para o terminal de transação das APIs.

#### **Sistema de URL Atual** <a href="#h_dfbf424bac" id="h_dfbf424bac"></a>

Todos os domínios acessíveis a partir do domínio godigibee.io seguem o modelo de URL:&#x20;

*   **Portal Web:** [www.godigibee.io](http://www.godigibee.io/)

    URL do Portal Web que pode ser acessado por usuários para criar, publicar e monitorar _pipelines_.\

*   **Back-end:** core.godigibee.io

    _Endpoint_ voltado para o uso interno, ou seja, pelo _backend_ da Plataforma, para se fazer requisições de componentes internos.\

*   **Transacional:** api.godigibee.io

    _Endpoint_ utilizado para realizar requisições aos _pipelines_ no ambiente de produção.\

*   **Static content:** static.godigibee.io

    _Endpoint_ utilizado que fornece imagens estáticas. Ex.: Miniaturas dos _pipelines_ e as imagens dos componentes (_Triggers_, _Capsules_ and Components).\

*   **Test: test.godigibee.io**

    _Endpoint_ utilizado para identificar o endereço dos _pipelines_ que estão configurados como APIs, ou seja, REST, HTTP e HTTP-File.

#### **Novo sistema de URLs** <a href="#h_32f30180cf" id="h_32f30180cf"></a>

Os domínios criados no Cluster dos EUA usarão um novo sistema de URL, conforme descrito abaixo:

* **Portal Web:** \<realm>.portal.digibee.io
* **Back-end:** \<realm>.core.digibee.io
* **Static content:** \<realm>.static.digibee.io
* **Test:** \<realm>.test.digibee.io
* **Prod (Transacional): .**\<realm>.api.digibee.io

{% hint style="info" %}
Num futuro próximo, haverá coexistência entre o novo modelo de URL e o antigo modelo para realms no Cluster Brasil (godigibee.io).
{% endhint %}
