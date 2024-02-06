# Julho

## Novidades 18/07/2023

### COMPONENTES <a href="#undefined" id="undefined"></a>

* **Dynamic Keys para REST V2 (**_**General Availability**_**):** atualizamos o componente [REST V2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2) para permitir o uso de _Double Braces_ nas chaves do _header._
* **Evolução do PGP (**_**General Availability**_**):** uma melhoria para o componente [PGP](https://docs.digibee.com/documentation/v/pt-br/components/security-components/pgp) agora oferece suporte à criptografia AEAD.
* **Lista de região EUA (US) para S3 Storage, SQS (AWS) V2, e JMS trigger (**_**General Availability**_**):** uma melhoria para os componentes [S3 Storage](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/s3-storage), [SQS (AWS) V2](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/sqs-aws-new) e para o [JMS trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/jms-trigger) agora oferece a lista de regiões em inglês.\


### MONITOR _-_ PIPELINE LOGS _(General Availability)_ <a href="#undefined" id="undefined"></a>

Ao clicar em "Ver todos os logs", a pessoa usuária era redirecionada para a página de Pipeline Logs, onde eram exibidos todos os logs de uma determinada execução. Com essa melhoria, os resultados são abertos em uma nova aba para que a pessoa usuária não perca as informações inseridas nos filtros da página de execuções concluídas.

Para saber mais, leia a [documentação sobre Pipeline Logs](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-logs).



\
\


Nós também solucionamos alguns _bugs:_\


* **Integração de Grupos:** solucionamos o _bug_ que impedia a atribuição automática de permissões a usuários após login via _single sign-on_ (SSO) em _realms_ não federados, isto é, sem integração de grupos ativa.
* **Canvas - Linhas conectoras:** solucionamos o _bug_ que algumas vezes removia o nome das linhas conectoras dos componentes _Parallel_ e _Choice_.
* **Canvas - Lista de Cápsulas:** solucionamos o _bug_ que não mostrava o nome de Cápsulas corretamente na lista de Cápsulas dentro do Canvas.
* **Canvas - **_**Global**_** inexistente**: atualizamos a mensagem de erro de quando um _pipeline_ tenta usar uma _Global_ que não está cadastrada.
* **Canvas - Linhas do **_**Parallel e Choice**_**:** atualizamos o comportamento de duplo clique nas linhas conectoras dos componentes _Parallel_ e _Choice_. Agora, o duplo clique na linha abre o formulário de configuração da execução ou da condição.
* **Duplicação de versão **_**minor**_** de **_**pipelines**_**:** solucionamos o _bug_ que duplicava versões _minor_ do _pipeline_ e impedia que elas fossem editadas e salvas.



***

##

## Novidades 04/07/2023

### CANVAS - PAINEL DE EXECUÇÃO - EXPORTAÇÃO E IMPORTAÇÃO DE DADOS DA EXECUÇÃO DO _PIPELINE (General Availability)_ <a href="#undefined" id="undefined"></a>

Agora, você pode exportar e importar dados de uma execução de um _pipeline_ no Painel de execução.

* Exportar faz o _download_ de um arquivo no seu computador com os dados do fluxo criado e da execução do _pipeline_.
* Importar faz o _upload_ de um arquivo no Painel de execução e reconstrói o painel como estava no momento que o _pipeline_ foi executado.

Para saber mais, leia a [documentação sobre Exportar e Importar](https://docs.digibee.com/documentation/v/pt-br/build/new-canvas-beta-restricted/execution-panel-beta#exportar-e-importar).



### CANVAS - FOCO NO RESULTADO DE BUSCA _(General Availability)_ <a href="#undefined" id="undefined"></a>

Agora, ao realizar uma busca no Canvas, é possível focar o resultado no _pipeline_ clicando sobre o resultado listado ou no botão com o ícone de foco. O resultado será focado no _pipeline_ independente do nível em que ele está localizado.

Para saber mais, leia a [documentação sobre Navegação em um pipeline](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/pipeline-navigation#campo-de-busca).

<figure><img src="https://lh4.googleusercontent.com/nRXAY1Z9zTTuLasPSMk516g20jfUU6HqMCBne3Bj6vnpYmivt7TCl--t0i9PwfsxLJHxq1SvK1EDEIKNi2gJ4yoMggqsfwXH_Co3dQn1nmwKGy-Tv68ypWQqZINNIh0LfYKS3Ufh8cy67BHxuvEEiSo" alt=""><figcaption></figcaption></figure>



### IMPLEMENTAÇÃO DA DIGIBEE INTEGRATION PLATFORM NO AZURE KUBERNETES SERVICE (Beta Restrito). <a href="#undefined" id="undefined"></a>

A Digibee Integration Platform agora pode ser executada no Azure Kubernetes Service (AKS), o serviço de gerenciamento de Kubernetes da Microsoft. Isso simplifica a integração dos _pipelines_ de clientes SaaS dedicados, desenvolvendo um fluxo de trabalho totalmente _cloud-native._

Para saber mais, leia a [documentação sobre a Digibee Integration Platform no AKS.](https://docs.digibee.com/documentation/v/pt-br/plataforma/instalacao-do-digibee-dedicated-saas-no-azure)

### &#x20;MONITOR _-_ PIPELINE LOGS _(General Availability)_ <a href="#undefined" id="undefined"></a>

Antes desta melhoria, a pessoa usuária perdia os parâmetros inseridos nos campos ao pesquisar na página Pipeline Logs e ao alterar o ambiente de Test para Prod. Agora, os parâmetros são mantidos ao usar o botão BUSCAR.

Para saber mais, leia a [documentação sobre Pipeline Logs](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-logs).



### RUN _- ROLLBACK_ DE VERSÃO IMPLANTADA (Beta Restrito) <a href="#h_61208c6d47" id="h_61208c6d47"></a>

Agora, as pessoas usuárias podem fazer o rollback, ou, reverter a versão de implantação de um _pipeline_ para uma versão anterior que estava em funcionamento.

Esta _feature_ está em fase Beta Restrito, disponível para clientes específicos.

Caso tenha interesse em participar, entre em contato com o seu CSM.



### RUN - SELEÇÃO DE VERSÃO DO PIPELINE ENGINE (Beta Restrito) <a href="#undefined" id="undefined"></a>

Esta nova _feature_ na página de Run permite que as pessoas usuárias selecionem a versão do pipeline engine. Esta seleção estará disponível ao fazer uma nova implantação, e ela visa melhorar o desempenho, o processamento e a eficiência em toda a Digibee Integration Plataform.

Esta _feature_ está em fase Beta Restrito, disponível para clientes específicos.

Para saber mais, leia a [documentação sobre seleção de versão do pipeline engine.](https://docs.digibee.com/documentation/v/pt-br/run/como-alterar-a-versao-do-pipeline-engine-beta-restrito)

### &#x20;<a href="#h_dbb727a16c" id="h_dbb727a16c"></a>

### MONITOR - EXECUÇÕES CONCLUÍDAS _(General Availability)_ <a href="#h_dbb727a16c" id="h_dbb727a16c"></a>

Agora, as pessoas usuárias podem usar o _hyperlink_ “Abrir o pipeline em uma nova aba” no canto superior direito para acessar no Canvas o _pipeline_ cuja a execução estão analisando.

Esta _feature_ estava em fase Beta e foi promovida para _General Availability_.

Para saber mais, leia a [documentação sobre execuções concluídas](https://docs.digibee.com/documentation/v/pt-br/monitor/execucoes-concluidas).

### &#x20;DIGIBEE ACADEMY 2.0 <a href="#undefined" id="undefined"></a>

**DIGIBEE AI ASSISTANT **_**(General Availability)**_

Nossa Digibee AI Assistant no Digibee Academy agora disponibiliza links redirecionando para o nosso [Portal de Documentação](https://docs.digibee.com/documentation/v/pt-br/) com base nas perguntas feitas pelas pessoas usuárias.\


**WEBINAR “EVENT DRIVEN ARCHITECTURE I ON DIGIBEE INTEGRATION PLATFORM”**

![](https://lh4.googleusercontent.com/i1Gn9OBVbn7pyJJUbdvue66eJ\_tbD-58Opx9hwruNXhxo4xkFSEuIR9dUyIcauWOP33-Ae6BozNgmZ\_Lfr2SIjWKSHpngFAoefCX3cB8mP8aAqWap9HCfiHXujxsqd-FMBKCT75Cly-7oSkCt\_b5I8c)

Nosso novo webinar “Event Driven Architecture I on Digibee Integration Platform” já está disponível no [Digibee Academy 2.0](https://digibee.academy/), com áudio em inglês e sem legendas.\






Nós também solucionamos alguns _bugs:_\


* **Canvas - Atalhos:** solucionamos o _bug_ em que os atalhos de salvar o _pipeline_ (CTRL+S; Cmd+S) e ativar e desativar o Minimapa (CTRL+M; Cmd+M) não funcionavam.
* **Canvas - Copiar e colar componente:** solucionamos o _bug_ que às vezes não permitia colar um componente copiado na área de transferência.
* **Canvas - Menu de ações do componente:** solucionamos o _bug_ em que se uma versão antiga do pipeline era aberta no histórico, o menu de ações não aparecia acima do componente no Canvas.
* **Canvas - Token JWT habilitado:** solucionamos o _bug_ em que o campo Token JWT no Trigger HTTP era habilitado por padrão.
* **Canvas - Atalho redefine tamanho do Painel de execução:** solucionamos o _bug_ em que o atalho CTRL+Enter ou Cmd+Enter fazia o Painel de execução ser redefinido para a altura padrão.
* **Canvas - Melhoria em mensagem de erro:** melhoramos a mensagem de erro quando uma _Global_ não existe no _realm._
* **Monitor - Detalhes de execução:** solucionamos o _bug_ da página de Execuções Concluídas, na aba de Detalhes de execução, que acontecia quando a pessoa usuária inseria valores numéricos decimais, e a mensagem retornava com valores inteiros.
* **Monitor - Pipeline Metrics:** solucionamos o _bug_ no qual o Grupo “Support” não tinha permissão para ver _pipelines_ na página Pipeline Metrics.
* **Acessos via IdP:** solucionamos o _bug_ que exibia uma página em branco quando a pessoa usuária usava a URL de redirecionamento para login via IdP.
* **Teste de Integração de Grupos:** solucionamos o _bug_ que fornecia a URL para login via IdP, levando a pessoa usuária para uma página em branco e a impedindo de realizar o teste de integração de grupos.
* **Teste de Integração de Grupos:** solucionamos o _bug_ que impedia o funcionamento correto do teste de integração de grupos.
* **Grupos:** solucionamos o _bug_ que exibia uma mensagem de erro genérica quando a pessoa gestora de acessos atribuía usuários a grupos usando a página Grupos.

