# Dezembro

## Novidades 27/12/2022

### NOVO CANVAS (BETA)

Lançamos o novo Canvas em beta, com melhorias significativas relacionadas à experiência de construção e navegação de _pipelines_, além dos seguintes recursos e funcionalidades:

* _**Flow tree**_, estrutura em forma de árvore que exibe os componentes de um _pipeline_, simplificando a navegação entre subníveis e o entendimento da lógica aplicada no fluxo de integração;
* **Campo de pesquisa**, que permite ao usuário buscar contas, _globals_ e componentes de maneira fácil e rápida;
* **Alertas de validação** durante a construção de um pipeline, que ajudam a identificar e corrigir problemas comuns mais rápido. Para saber mais, leia a documentação de [Validação de construção de pipeline](../../build/new-canvas-beta-restricted/validacao-de-construcao-do-pipeline.md);
* **Minimapa**, que agiliza a navegação e a leitura durante a construção de um _pipeline_;
* **Maior precisão** ao colar um componente ou fluxo em uma área específica do novo Canvas;
* **Seta magnética**, que facilita a conexão entre os componentes;
* _**Auto pan**_, que facilita a navegação ao arrastar componentes em _pipelines_ muito grandes.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2F0Lqdi02FJ855Y7OYcw45%2Fnovo%20canvas%20gif.gif?alt=media&token=e8899f72-cb69-43e9-956f-3f5e3fce895d" %}

Para saber mais, leia a documentação sobre o [Novo Canvas](../../build/new-canvas-beta-restricted/) e [Navegação em um pipeline](../../build/pipelines/pipeline-navigation.md).

**IMPORTANTE:** ao utilizar o novo Canvas, você automaticamente faz sua adesão ao programa Beta e concorda com os termos de uso. Para mais informações sobre versões beta, leia a documentação [Programa beta](../../general/programa-beta.md).\




### COMPONENTES

* **SAP:** evoluímos o [componente SAP](../../build/capsulas/public-capsules/sap.md) que agora conta com dois novos parâmetros (_Send as File_ e _File Name_). Assim, o componente pode fazer requisições para o SAP utilizando um arquivo, sendo útil para envio de conteúdos muito grandes, o que antes não era possível.
* **Google Big Table:** criamos o [componente BigTable](../../components/structured-data/google-big-table.md), que estabelece uma conexão e permite realizar operações em instâncias de bancos de dados no serviço Google BigTable.
* **DB V2, Stream DB V3 e Stored Procedure suporte TeraData:** atualizamos nossos bancos de dados suportados para incluir o [TeraData Database](../../plataforma/bancos-de-dados-suportados.md#teradata-database). É necessário que o cliente entre em contato com o time de suporte Digibee e providencie a ativação do _driver_ JDBC licenciado junto a TeraData.
* **MongoDB:** fizemos uma melhoria de funções para o [componente MongoDB.](../../components/structured-data/mongo-db.md) Agora, contamos com suporte ao protocolo de segurança TLS para estabelecer conexões e operações para manipulação de índices.
* **CassandraDB:** fizemos uma melhoria no [componente Cassandra](../../components/structured-data/cassandra-db.md) e agora, a paginação de resultados com uma grande quantidade de registros é feita automaticamente, consolidando o resultado na saída como uma consulta atômica. Essa melhoria dispensa a necessidade de outras configurações ou ações para obter esses resultados.

### &#x20; MEU CONSUMO

Além de poder visualizar o consumo de [_Pipeline Subscriptions_](broken-reference) e[ _RTUs_](../../licensing/usage-limits.md) no geral, agora também é possível ver em qual ambiente e projeto eles estão sendo consumidos através da página Meu consumo. A nova página reúne as seguintes funcionalidades:

* **Painel de consumo:** visualize a quantidade de _Pipeline Subscriptions_ e _RTUs_ consumidas em cada ambiente.
* **Lista de consumo:** confira uma lista detalhada de cada item de consumo — projeto, ambiente, _pipeline_, _trigger_, tamanho da implantação, _RTUs_ e réplicas. Você também pode exportar esses dados para um arquivo CSV.
* **Lista de contato:** acesse facilmente os nomes e endereços de e-mail das pessoas que ajudam em sua jornada com a _Digibee Integration Platform_.

**IMPORTANTE:** no momento, a página Meu consumo está em Beta restrito, mas em breve, estará disponível para todos os clientes. Se quiser fazer parte do [Programa beta restrito](../../general/programa-beta.md#h\_d59e60e1bd), fale com o seu _Customer Success Manager_ (CSM).

### &#x20; RUN

* _**Auto refresh**_**:** nós atualizamos o _layout_ do intervalo de _auto refresh_, facilitando sua visualização, deixando de uma forma mais dinâmica.
* **Informação de projeto e instâncias:** agora, ao selecionar o _pipeline_ para implantar ou reimplantar, são exibidas as informações do projeto e da instância (que pertence ao _pipeline_ que será implantado, ou reimplantado), facilitando o rastreamento de implantações.
* **Redirecionamento para o projeto do **_**pipeline**_** implantado:** agora, depois de implantar seu _pipeline_, você será redirecionado para a tela de origem do projeto do _pipeline_, para poder acompanhar suas implantações com mais facilidade.
* **Aviso de conflito de rotas:** atualizamos o aviso de conflito de rotas, que agora informa qual pipeline e versão estão utilizando a rota selecionada no _Additional API Routes_. Desse modo, informamos e impedimos que existam rotas iguais em _pipelines_ diferentes que possam sobrepor uma à outra.

### &#x20; DESBLOQUEIO DE LOGIN

Usuários que tiveram o login bloqueado agora podem desbloqueá-lo sem acionar o time de suporte. Após o bloqueio do login, um código é enviado automaticamente para o e-mail do usuário. Este código deve ser usado na página de desbloqueio para que o usuário consiga fazer login.

Para saber mais, leia a nossa documentação sobre [Problemas para fazer login na Digibee Integration Platform](https://intercom.help/godigibee/pt-BR/articles/6618894-problemas-para-fazer-o-login-na-digibee-integration-platform).



### DOCUMENTAÇÃO

Visando melhorar nossa documentação, atualizamos os artigos abaixo:

* [Histórico de versões de pipelines](../../build/pipelines/historico-de-versoes-de-pipelines.md)
* [Versionamento de pipelines](../../build/pipelines/versionamento-de-pipelines.md)
* [Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md)
* [Grupos do Azure AD não aparecem na federação de grupos](https://intercom.help/godigibee/pt-BR/articles/6852139-grupos-do-azure-ad-nao-aparecem-na-federacao-de-grupos)
* [Status de implantação do pipeline](../../run/general-status/pipeline-deployment-status.md)
* [Reimplantando um pipeline](../../run/deployment/redeploying-a-pipeline.md)
* [Aviso de conflito de rotas](https://intercom.help/godigibee/pt-BR/articles/6820343-aviso-de-conflito-de-rotas)\
  \
  \
  &#x20;

Nós também solucionamos alguns _bugs_:

* **Contas:** corrigimos o _bug_ que trazia uma página em branco quando o usuário tentava editar _accounts_ do tipo OAuth-2.
* **Grupos:** corrigimos o _bug_ que impedia o gestor de acessos de remover usuários de grupos a partir da página **Grupos**.
* **Canvas V1 e novo Canvas:** corrigimos o _bug_ que impedia alguns _pipelines_ de serem salvos enquanto o usuário estivesse navegando pelo fluxo principal.
* **WebDAV:** corrigimos o _bug_ que causava o comportamento incorreto no componente, obrigando o usuário a informar um arquivo, mesmo numa operação de listagem.

\




## Novidades 14/12/2022

### MONITOR

* **Visão geral:** agora, a tabela de visão geral exibe o número de erros e de execuções de _pipeline_ em conjunto. Também omitimos a coluna “dinâmica” e trocamos a posição da tabela e do gráfico nesta página.



### NOVO CANVAS (Beta restrito)

Melhoramos a performance do novo Canvas, dando mais rapidez para a navegação entre subníveis de um _pipeline_.

**IMPORTANTE**: para participar do programa de [Beta restrito](../../general/programa-beta.md), fale com o seu _Customer Success Manager (CSM)_.

### &#x20; COMPONENTES

* **RPA**: o componente RPA foi descontinuado. A documentação relacionada ainda está disponível, mas foi sinalizada no título como descontinuada.
* **Suporte SQL Server 2019**: atualizamos nossa lista de [Bancos de Dados suportados](../../plataforma/bancos-de-dados-suportados.md) com a inclusão do Microsoft SQL Server 2019.
* **S3 Storage (AWS):** uma evolução do S3 Storage permite o uso de um _endpoint_ customizado via URL no componente.

### &#x20;RUN

* **Reimplantar:** a reimplantação do _pipeline_ ficou mais fácil e rápida: basta selecionar a opção REIMPLANTAR no _pipeline card_, que irá abrir um painel lateral com as informações já preenchidas. Então, selecione o novo tamanho, execuções simultâneas e réplicas e finalize clicando em IMPLANTAR. Leia nossa [documentação sobre reimplantação do pipeline aqui](../../run/deployment/redeploying-a-pipeline.md).
* _**Status**_** de implantação do **_**pipeline**_**:** ficou mais fácil acompanhar o _status_ da implantação do _pipeline_. O novo _design_ do _pipeline card_ inclui o _status_ do _pipeline_ em tempo real. Leia nossa [documentação sobre o status de implantação do pipeline aqui.](../../run/general-status/pipeline-deployment-status.md)
* _**Auto refresh**_**:** essa nova funcionalidade permite selecionar o intervalo de atualização da página e, consequentemente, a atualização do _status_ do _card_ dos _pipelines_, facilitando obter informações do _pipeline_ em tempo real. [Leia sobre o auto refresh aqui.](../../run/general-status/pipeline-deployment-status.md#intervalo-de-auto-refresh)
* **Aviso de conflito de rotas:** temos um novo aviso que ajuda a prevenir e solucionar o problema de conflitos de rota durante a implantação. _Pipelines_ com rotas iguais ou que começam com parâmetros que recebem o valor de ":id" através do "queryAndPath" geram erros e substituem _pipelines_ devido a essas definições. Leia mais sobre o [aviso de conflito de rotas aqui.](https://intercom.help/godigibee/pt-BR/articles/6820343-aviso-de-conflito-de-rotas)

### &#x20;MEU CONSUMO (Beta restrito)

* **Lista de contatos:** liberamos em nossa página “Meu Consumo” os nomes e e-mails das pessoas que prezam pelo sucesso da sua jornada com a Digibee Integration Platform. Entre em contato com o seu _Customer Success Manager_ (CSM) em caso de dúvidas sobre seu plano.

**IMPORTANTE:** a página “Meu consumo” está no momento em Beta restrito e estará disponível para todos os clientes em breve. Para participar do programa de [Beta restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta), fale com o seu _Customer Success Manager_ (CSM).

\


### DOCUMENTAÇÃO

Visando melhorar nossa documentação, atualizamos o artigo abaixo:

* [Pipeline](../../build/pipelines/)
* [Conceitos básicos sobre usuários](broken-reference)
* [Subpipelines](../../build/pipelines/subpipelines.md)\
  \
  \
  &#x20;

Nós também solucionamos alguns _bugs_:

* **Pipeline logs:** corrigimos o _bug_ no qual o nome LIMPAR no botão de limpar mudava para BUSCAR quando o tamanho da página era reduzido.
* **Expiração de senha:** corrigimos o _bug_ em que o botão CONFIRMAR ficava carregando por tempo indeterminado quando o usuário solicitava o cadastro de uma nova senha informando a antiga incorretamente.
* **Simulação de integração de grupos:** corrigimos o _bug_ que atrasava a contagem do temporizador quando o usuário minimizava a página de teste.
* **Blob Storage (Azure):** corrigimos o _bug_ que exibia tela branca no novo Canvas quando o formulário de configuração do componente Blob Storage (Azure) era aberto.
* **Flow tree:** corrigimos o _bug_ que impedia o usuário de redimensionar o tamanho da lista de componentes quando a estrutura do _Flow tree_ estivesse aberta no novo Canvas.
* **Remoção de um Parallel Execution:** corrigimos o _bug_ que exibia uma página branca ao remover ou reconectar o componente Parallel Execution ao fluxo de um _pipeline_ no novo Canvas.
* **Remoção de um Choice:** corrigimos o _bug_ que exibia uma página branca ao remover os parâmetros “_when”_ ou “_otherwise”_ do componente Choice quando no novo Canvas_._
* _**Test mode**_** na interpretação de HTML:** corrigimos o _bug_ que fazia o _Test mode_ renderizar textos em HTML e não exibí-los simplesmente como _plain text_ nos _logs_ do Canvas V1 e novo Canvas.

\
