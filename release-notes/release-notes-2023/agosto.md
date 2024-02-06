# Agosto

<figure><img src="../../.gitbook/assets/header_realeasenews_august.gif" alt=""><figcaption><p>Image do header de novidades ou release notes de agosto</p></figcaption></figure>

## Novidades 22/08/2023

### Componentes <a href="#h_9160d451ff" id="h_9160d451ff"></a>

**Componente JSLT (Beta):** criamos um novo componente que permite manipular conteúdo JSON através da tecnologia JSLT. [Para mais informações, veja a documentação do JSLT](https://docs.digibee.com/documentation/v/pt-br/components/tools/jslt). Essa funcionalidade está atualmente na fase Beta.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FsKKEV50sWu4Cu9S0v5C4%2FJSLT%20Component.mp4?alt=media&token=a63c82ec-46ba-4d37-b741-26faf91a5339" fullWidth="false" %}
Vídeo do componente JSLT
{% endembed %}

**Atualizações do Basic Auth para triggers HTTP, HTTP File e REST (Beta):** atualizamos os seguintes detalhes de configuração, como mostrado nas documentações de [Consumers (Chaves de API)](https://docs.digibee.com/documentation/v/pt-br/configurations/chaves-de-api-consumers), [HTTP trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger), [HTTP File trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger) e [REST trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger):

* Ao configurar uma credencial _Basic Auth_, o nome de usuário recebe o prefixo {_realm_}, como em: {realm}-{username}.
* O parâmetro Rate Limit fica visível somente se os parâmetros API Key ou Basic Auth estiverem ativados.
* O parâmetro Aggregate By exibe as seguintes opções: _Consumer_ ou _Credential_ (_API Key_, _Basic Auth_).

O [Store Account ](https://docs.digibee.com/documentation/v/pt-br/components/tools/store-account)(Beta Restrito) e todos os componentes que suportam credenciais dinâmicas agora possuem a _flag_ Scoped. Isso permite que esses componentes possam ser executados dentro de blocos _stream_ em paralelo, sem ocorrer sobreposição de dados e condições de corrida.

Nós recomendamos validar as expressões ao configurar os parâmetros JSON Path nos componentes [For Each](https://docs.digibee.com/documentation/v/pt-br/components/logic/for-each), [Stream JSON File Reader ](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-json-file-reader)e [JSON Path Transformer](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-path-transformer). Essa precaução garante que os _pipelines_ funcionem com maior precisão e ajuda a prevenir erros.\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FvqZVIY8apxVId0AkE3gA%2FScoped-Flag.mp4?alt=media&token=4f8742e7-0ef7-4e91-8e26-d06359cf4c9d" %}
Vídeo Scooped flag
{% endembed %}

### &#x20;<a href="#h_72d78df2f5" id="h_72d78df2f5"></a>

### Restauração de grupos _(General Availability)_ <a href="#h_72d78df2f5" id="h_72d78df2f5"></a>

Lançamos a nova _feature_ de Restauração de grupos na página de Grupos, que permite que você restaure grupos que podem ter sido arquivados por engano ou intencionalmente a qualquer momento.

Ao restaurar um grupo, as pessoas usuárias que pertencem a ele terão novamente as permissões concedidas por esse grupo desde que estejam ativas.

Saiba mais na [documentação sobre Grupos](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/grupos-do-controle-de-acesso).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FWiPLL9qLo4kjFs2AXXGk%2FGroup%20restoration.mp4?alt=media&token=bd7b6478-ed02-4dc5-89b9-096284754349" %}
Vídeo de restauração de grupos
{% endembed %}



### Monitor - Visão Geral _(General Availability)_ <a href="#undefined" id="undefined"></a>

Quando a pessoa usuária clicava na lupa da coluna Ações, ela era direcionada para Execuções concluídas dentro da página Visão geral, perdendo algumas informações como as inseridas nos filtros.

Agora, ao clicar na lupa, ela ainda é direcionada para a mesma página de Execuções concluídas, porém em uma nova aba, mantendo assim todas as informações preenchidas anteriormente.

Saiba mais na [documentação sobre Execuções concluídas](https://docs.digibee.com/documentation/v/pt-br/monitor/completed-executions).



### Alertas de Monitor - Novo canal: Webhook (Beta Restrito) <a href="#undefined" id="undefined"></a>

Agora a pessoa usuária tem a opção de enviar alertas de notificação usando um _webhook_, além de e-mail e Telegram. A pessoa usuária deve fornecer o _endpoint_ necessário para ativar o _webhook_.

Saiba mais na [documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).\


A _feature_ Alertas está em fase beta restrito e disponível somente para clientes específicos. Se você deseja ter acesso a esta _feature_, entre em contato com o suporte ou com seu CSM. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).



### Alertas de Monitor - Notificações de novas métricas (Beta restrito) <a href="#undefined" id="undefined"></a>

Lançamos 4 novos alertas de notificação de Monitor, conforme detalhado a seguir:

* **Uso de memória do **_**pipeline**_**:** mostra a porcentagem média de uso de memória de cada réplica de um _pipeline_ para o intervalo de tempo ao longo do período selecionado.
* **Tempo de resposta do **_**pipeline**_**:** mostra o tempo médio (em milissegundos) que um _pipeline_ leva para gerar uma resposta ao longo do período selecionado para todas as réplicas.
* **Tamanho da mensagem do **_**pipeline**_**:** mostra o tamanho médio (em bytes) das mensagens recebidas e retornadas por todas as réplicas do _pipeline,_ para o intervalo de tempo selecionado.
* **Execuções de **_**pipeline**_** em andamento:** mostra o número total de execuções em andamento (em mensagens) - para todas as réplicas - durante o intervalo no período de tempo selecionado.

Saiba mais na[ documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).\


A _feature_ Alertas está em fase beta restrito e disponível somente para clientes específicos. Se você deseja ter acesso a esta _feature_, entre em contato com o suporte ou com seu CSM. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2Fd39HYnb9Cungn5T0CnNF%2FAlerts_new%20metrics%20and%20webhook_1.mp4?alt=media&token=bb319ab9-d595-4053-8814-5c2f67e04595" %}
Vídeo de novas métricas e webhook
{% endembed %}

\






### Nós também solucionamos alguns _bugs:_

* **Papéis - Lista de **_**bindings**_** selecionados:** solucionamos o _bug_ em que durante a seleção de novos _bindings_ de papéis, eles não eram ordenados seguindo a sequência em que foram selecionados.
* **Papéis - **_**Bindings**_** de papéis salvos:** solucionamos o _bug_ em que _bindings_ de um grupo não eram exibidos por ordem alfanumérica após serem salvos.
* **Papéis - Seleção de **_**bindings**_** de Papéis**_**:**_ solucionamos o _bug_ em que papéis já vinculados ao grupo continuavam aparecendo na lista de seleção disponível.
* **Menu do perfil de pessoa usuária:** solucionamos o _bug_ em que o botão Criar sobrepunha o menu do perfil de pessoa usuária.
* **Canvas - Validação do Painel de execução:** solucionamos o _bug_ em que o editor do _Payload_ do Painel de execução não validava propriedades duplicadas como o antigo _Test mode_.



***

## Novidades 01/08/2023



### Componentes

* **Basic Auth para os **_**triggers**_** REST, HTTP e HTTP File (Beta):** o Basic Auth é um método de autenticação que utiliza criptografia Base64 para evitar acessos não autorizados. Essa _feature_ está atualmente na fase Beta.\
  Saiba mais na documentação de [Consumers (Chaves de API)](https://docs.digibee.com/documentation/v/pt-br/configurations/chaves-de-api-consumers) e dos _triggers_ [REST](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger), [HTTP](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger) e [HTTP File](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger).
* **Filtrar e ordenar lista de contas para componentes conectores **_**(General Availability)**_**:** fizemos uma melhoria para todos os componentes conectores que usem uma lista de contas ([saiba mais na documentação sobre Contas](https://docs.digibee.com/documentation/v/pt-br/configurations/contas-accounts)). Agora, a pessoa usuária pode visualizar apenas as contas suportadas para um componente conector específico em ordem alfabética. A documentação de cada componente conector também informa as contas suportadas nos parâmetros de configuração.



### Suporte a credenciais dinâmicas (Beta Restrito)

Esta é uma _feature_ exclusiva do Engine V2 que permite a pessoa usuária alterar as configurações de suas credenciais na págona de Runtime, através do componente Store Account.

Saiba mais na [documentação sobre suporte à credenciais dinâmicas](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito).



### Implementação da Digibee Integration Platform no Amazon Web Services (Beta Restrito)

Agora, a Digibee Integration Platform pode ser instalada e executada no Elastic Kubernetes Service (EKS), o serviço de gerenciamento de Kubernetes da Amazon. Essa implementação expande o nosso leque de possibilidades para clientes SaaS dedicado, com mais uma opção de fluxos de trabalho totalmente _cloud-native_.

Saiba mais na [documentação sobre EKS](https://docs.digibee.com/documentation/v/pt-br/plataforma/saas-dedicado-na-digibee-integration-platform/digibee-dedicated-saas-installation-on-aws) para clientes SaaS dedicado.



### Documentação de componentes e _triggers (General Availability)_

Agora é possível documentar o propósito de componentes e _triggers_ nos seus formulários de configuração, tornando a resolução de problemas e a colaboração na construção de _pipelines_ mais fácil e eficiente.

Saiba mais na [documentação sobre o campo _Documentation_ no Canvas](https://docs.digibee.com/documentation/v/pt-br/build/new-canvas-beta-restricted#documentacao-de-componentes-e-triggers).



### Páginas Usuários, Papéis e Grupos _(General Availability)_

Fizemos algumas melhorias na experiência da pessoa usuária para visualizar e editar Permissões dentro das páginas Usuários, Papéis e Grupos:

* Mudamos o componente de Permissões na tabela de configuração destas páginas.
* Incluímos um _tooltip_ sobre o assunto na coluna de permissões específicas.
* Incluímos o link para nossa documentação acima da tabela de [configuração de permissões de papéis](https://docs.digibee.com/documentation/v/pt-br/administration/novo-controle-de-acesso/papeis-do-controle-de-acesso).
* Na coluna Específica consideramos a contagem de seleções das permissões quando há mais de um item selecionado.

Saiba mais na [documentação sobre Usuários, Papéis e Grupos](https://docs.digibee.com/documentation/v/pt-br/administration/novo-controle-de-acesso).



### Acessos via IdP (Beta)

A _feature_ passou da fase Beta Restrito para Beta e está disponível para todos os clientes que configuraram seus Provedores de Identidade (IdP). Note que a partir desta mudança, o gestor de acesso poderá controlar o método de login das pessoas usuárias em um _realm_ com _Single Sign-On_ (SSO).

Saiba mais na [documentação sobre Acessos via IdP.](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/acessos-via-idp)



### Desbloqueio de login por código de segurança _(General Availability)_

O número de tentativas de login mal-sucedido restantes é exibido na página de desbloqueio de login e o contador é redefinido para cada tentativa bem-sucedida.

Saiba mais na [documentação sobre Fluxo de login](https://docs.digibee.com/documentation/v/pt-br/administration/user-authentication-and-autorization/fluxo-de-login).



### Integrações de grupos (Beta)

Ao arquivar uma integração de grupo ativa, seu _status_ passa automaticamente para inativa. Caso todas as integrações de grupo ativas sejam arquivadas, o _realm_ volta a ser não federado.

Saiba mais na [documentação sobre integração de grupos IdP com grupos Digibee](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups).



### Monitor - Novo alerta de notificação para Mensagens em fila (Beta restrito)

A métrica de [Mensagens em fila](https://docs.digibee.com/documentation/v/pt-br/monitor/alertas/mensagens-em-fila) informa às pessoas usuárias quando o volume de solicitações de entrada requer um número maior de réplicas de _pipeline_ para aumentar a capacidade de processamento disponível.

A _feature_ Alertas está em fase beta restrito e disponível somente para clientes específicos. Se você deseja ter acesso a esta _feature_, entre em contato com o suporte ou com seu CSM. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).



### _Rollback_ de versão implantada _(General Availability)_

Agora, as pessoas usuárias podem reverter o _pipeline_ para uma versão de implantação anterior que esteja em funcionamento.

Saiba mais na [documentação sobre _Rollback_ de versão implantada.](https://docs.digibee.com/documentation/v/pt-br/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)



### Promovendo _pipelines_ entre ambientes _(General Availability)_

Agora, as pessoas usuárias podem reverter o _pipeline_ para uma versão de implantação anterior que esteja em funcionamento.

Saiba mais na [documentação sobre ](https://docs.digibee.com/documentation/v/pt-br/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)[_Rollback_](https://docs.digibee.com/documentation/v/pt-br/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)[ de versão implantada.](https://docs.digibee.com/documentation/v/pt-br/run/deployment/how-to-rollback-to-a-previous-deployment-version-restricted-beta)



### Digibee Academy

Não perca a fantástica oportunidade de expandir seu conhecimento e [trilhar seu caminho para a autossuficiência em integrações na Digibee Integration Platform:](https://digibee.academy/)

* Agora, nossos webinars [Event Driven Architecture I](https://digibee.academy/webinars/event-driven-architecture-i-pt/?lang=pt-br) e [Level up your pipelines working with files](https://digibee.academy/webinars/learn-to-work-with-files-on-the-digibee-integration-platform-pt/?lang=pt-br) possuem legendas em português, inglês e espanhol. [Confira no Digibee Academy!](https://digibee.academy/)

Acesse a ferramenta [AI Assistant](https://digibee.academy/ai-assistant) diretamente da Digibee Integration Platform. Ela está localizada no menu do ícone "?" (ponto de interrogação), logo abaixo de Documentação.\
\
\


### Nós também solucionamos alguns _bugs:_

* **Canvas - Estrutura do **_**Choice**_**:** solucionamos o _bug_ que às vezes colava estruturas que continham o componente _Choice_ de maneira incorreta.
* **Canvas - Imagens dos componentes:** solucionamos o _bug_ que não exibia imagens de alguns componentes no Canvas.
* **Canvas - Alerta do **_**Linter**_** para o **_**Session**_**:** solucionamos o _bug_ em que o _Linter_ alertava de maneira incorreta que a variável do componente _Session_ não estava sendo usada quando o fluxo tinha um componente _Session_ com uma requisição PUT dentro de um _OnProcess_, outro componente _Session_ com uma requisição de GET fora deste _OnProcess_, e o _OnException_ do primeiro componente vazio.
* **Canvas - **_**Choice**_** desconfigurado:** solucionamos o _bug_ que desconfigurava o nome das condições do componente _Choice_ e impedia o _pipeline_ de ser executado ao criar mais de dez condições no _Choice_.
* **Usuários:** solucionamos o _bug_ que às vezes não retornava registros ao pesquisar o nome completo ou apenas o sobrenome do usuário.
* **Componentes - Script:** corrigimos um bug que afetava o componente Script.&#x20;
* **Componentes - REST V2:** corrigimos um bug que causava comportamento incorreto ao realizar chamadas de API através do componente REST V2.
