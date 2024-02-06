# Janeiro

## Novidades 18/01/2022

#### PROVEDORES DE AUTENTICAÇÃO OAuth <a href="#h_36a88f7f0d" id="h_36a88f7f0d"></a>

Estamos evoluindo o cadastro de provedores de autenticação OAuth dentro da Plataforma.\
Até então, era possível integrar provedores que seguiam padrões RFC 6749 utilizando a aplicação Digibee através de uma solicitação para o time de desenvolvimento de produtos.

Com esta primeira entrega é possível cadastrar provedores dedicados ao seu _realm_ (que utilizam a aplicação do cliente) através da Plataforma a partir dos provedores pré-cadastrados na Digibee.

Assim, é possível utilizar os recursos de contas corporativas da Microsoft, além de contas homologadas no Mercado Livre e apps validados pelo Google.

[Clique aqui](../../settings/accounts/new-oauth2-architecture/) para saber mais sobre os provedores de autenticação Oauth.\
[Clique aqui](../../settings/accounts/new-oauth2-architecture/registration-of-new-oauth-providers.md) para ler o artigo completo sobre o fluxo de cadastro de provedores Oauth dentro da Plataforma.

#### TRIGGERS <a href="#h_59f05fbf75" id="h_59f05fbf75"></a>

* **HTTP, HTTP File e REST:** agora, os triggers HTTP, HTTP File e REST possibilitam o cadastro de _headers_ na resposta de requisições ao _pipeline_. Isto permite, por exemplo, o cadastro de _headers_ que ampliam a segurança na comunicação dos _pipelines_.\
  \
  Exemplos:\
  `"Strict-Transport-Security" : "max-age=648000; includeSubDomains; preload",`\
  `"Cache-Control" : "no-store",`\
  `"Content-Security-Policy" : "frame-ancestors 'none';",`\
  `"X-Content-Type-Options" : "nosniff",`\
  `"X-Frame-Options" : "DENY"`\
  \
  **IMPORTANTE**: [Clique aqui](../../components/triggers/http-trigger.md) para ler o artigo atualizado do componente

#### COMPONENTES <a href="#h_14193c4b8b" id="h_14193c4b8b"></a>

* **JWT:** atualizamos o componente e adicionamos 3 novos algoritmos para a assinatura de _tokens_ - ES256, ES384 e ES512. [Clique aqui](../../components/security-components/jwt-deprecated.md) para ler o artigo atualizado do componente.

Nós também solucionamos um _bug_:

* **Globals**: corrigimos o erro que permitia cadastrar Globals com letras maiúsculas, apesar dos caracteres invalidarem o uso de tal Global no _pipeline_.\
  **IMPORTANTE**: Globals cadastradas erroneamente (com letras maiúsculas) devem ser deletadas.
