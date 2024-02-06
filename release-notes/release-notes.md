# Release notes 2021

## Novidades 21/12/2021

### COMPONENTES <a href="#h_8e10b846f9" id="h_8e10b846f9"></a>

* **Email V2:** adicionamos o parâmetro FORCE TLS V1.2 que permite definir como obrigatório o uso do protocolo TLS V1.2 nas conexões com os servidores de email.\
  Importante: recomendamos a utilização deste parâmetro com servidores de email Microsoft Exchange. [Clique aqui para o artigo completo do componente.](https://intercom.help/godigibee/pt-BR/articles/4645082-email-v2)

Nós também solucionamos alguns _bugs_:

* **Trigger Scheduler:** corrigimos o erro que, em raras situações, impedia a execução consecutiva de tarefas agendadas.

## Novidades 14/12/2021

### NOVO MODELO DE CONTROLE DE ACESSO <a href="#h_78ee1558f1" id="h_78ee1558f1"></a>

Desenvolvemos um novo modelo de controle de acesso mais robusto e prático. Agora, a gestão de acesso permite o agrupamento e reuso de perfis de acessos similares para melhorar a experiência de acesso do _realm_.

Exemplo da nova concessão de permissões:

![](<../.gitbook/assets/dez\_01 (1).png>)

O novo modelo de Controle de Acesso conta com novos conceitos de Grupos, Papéis e Usuários que se relacionam como no modelo abaixo:

\\

![](../.gitbook/assets/dez\_02.png)

Para saber mais sobre o novo Controle de Acesso, leia os artigos abaixo:

1. [Novo modelo de Controle de Acesso](https://intercom.help/godigibee/pt-BR/articles/5808132-novo-modelo-de-controle-de-acesso)
2. [Grupos do Controle de Acesso](https://intercom.help/godigibee/pt-BR/articles/5810361-grupos-do-controle-de-acesso)
3. [Papéis do Controle de Acesso](https://intercom.help/godigibee/pt-BR/articles/5810244-papeis-do-controle-de-acesso)
4. [Papéis de sistema e grupos padrão](https://intercom.help/godigibee/pt-BR/articles/5811758-papeis-de-sistema-e-grupos-padrao)
5. [Conceitos básicos sobre Usuários](https://intercom.help/godigibee/pt-BR/articles/5808313-conceitos-basicos-sobre-usuarios)

Para que nenhum usuário perca suas permissões, planejamos um período de transição onde os dois modelos de acesso irão conviver. Todos os usuários devem ser migrados até **31 de Março/2022.**\
Para saber mais sobre a transição, leia o artigo [completo aqui.](https://intercom.help/godigibee/pt-BR/articles/5810530-transicao-do-novo-controle-de-acesso)

### TELA DE CONSUMERS - RENOMEADA PARA API KEYS <a href="#h_f58b49b2fd" id="h_f58b49b2fd"></a>

Visando melhorar a experiência dos nossos usuários e dar mais clareza no uso de alguns termos, atualizamos a tela de Consumers, dentro do menu Configurações. Agora, ela se chama API Keys. Sua função se mantém a mesma e o fluxo de configurações também.

### AUDITORIA <a href="#h_223f81ae67" id="h_223f81ae67"></a>

Realizamos melhorias na experiência de auditoria. Agora, os logs de auditoria contam com novos dados:

Serviço - identificação da funcionalidade da Digibee Integration Platform que foi auditada. Ex.: pipelines, globals, accounts.

Ação - a ação realizada que originou o registro. Ex.: created, updated, deleted, viewed.

Referência - é o nome amigável do objeto que foi auditado.

IMPORTANTE: nesta fase de entrega, apenas os objetos Pipeline, Account e Global possuem a referência.

Status: indica se a ação foi concluída com sucesso ou erro.

Esta entrega é parte de um processo mais amplo de aprimoramento que incluirá a possibilidade de navegação até o objeto que foi auditado.

### COMPONENTES <a href="#h_3508a845d5" id="h_3508a845d5"></a>

* XML Schema Validator: O cliente poderá validar um XML contra os arquivos XSD. [Clique aqui para ler o artigo completo.](https://intercom.help/godigibee/pt-BR/articles/5811671-xml-schema-validator)

\
Nós também solucionamos alguns _bugs_:

* Componente CSV to Excel: corrigimos o erro que impedia a leitura de arquivos com charsets diferentes de UTF-8.
* Métricas de pipelines: corrigimos o erro que impedia a exibição correta de dados quando filtrados pelo período de 15 minutos.
* Email Trigger V2: corrigimos um erro que impedia novos emails de serem lidos e também de serem movimentados e deletados corretamente após serem processados.

## Novidades 30/11/2021

### NOVA EXPERIÊNCIA DE IMPLANTAÇÃO (Beta) <a href="#h_8d80704c08" id="h_8d80704c08"></a>

Desenvolvemos uma nova experiência para as implantações de seus pipelines.\
A nova tela de implantação oferece mais autonomia, facilidade e traz mais dados para facilitar a tomada de decisão no momento de implantação, como a indicação do usuário que a realizou.\
[Clique aqui](https://intercom.help/godigibee/pt-BR/articles/5775833-modernizacao-da-interface-de-criar-implantacao) para ler o artigo completo sobre a nova tela.

IMPORTANTE: Durante o período do Programa Beta a funcionalidade será oferecida em paralelo a atual, desta forma você verá dois botões na tela.

​

![](../.gitbook/assets/nov\_01.png)

​

Para saber mais sobre o Programa Beta, [acesse aqui](https://intercom.help/godigibee/pt-BR/articles/5267114-programa-beta) a nossa documentação.

### HISTÓRICO DE VERSÕES DE PIPELINES (Beta) <a href="#h_941d4df3ef" id="h_941d4df3ef"></a>

Adicionamos uma nova funcionalidade ao histórico de versões de pipelines. Agora, é possível visualizar qualquer versão secundária de um pipeline, seus componentes e as configurações de cada um.\
[Clique aqui](https://intercom.help/godigibee/pt-BR/articles/5776001-historico-de-versoes-de-pipelines) para ler o artigo completo sobre o histórico de versões.

Para saber mais sobre o programa Beta, [acesse aqui](https://intercom.help/godigibee/pt-BR/articles/5267114-programa-beta) a nossa documentação.

### PROJETOS <a href="#h_fefb9beca7" id="h_fefb9beca7"></a>

Implementamos uma melhoria no gerenciamento de Projetos.\
Quando um pipeline é movido para um novo projeto é necessário implantá-lo novamente pois os ambientes de execução de pipelines (Test e Prod) são imutáveis.\
Assim, será exibido um alerta nas implantações que precisam desta ação.​

![](../.gitbook/assets/nov\_02.png)

> **IMPORTANTE**: essa funcionalidade ainda não suporta implantações multi-instância.

### LOGIN <a href="#h_d76962c83f" id="h_d76962c83f"></a>

Visando mais segurança no acesso à Plataforma, realizamos uma melhoria para que a senha de _login_ expire a cada 15 dias.\
A partir de agora será necessário criar uma nova senha quinzenalmente e refazer o login para que a sessão seja restabelecida.\
Caso haja necessidade de alterar o prazo de expiração da senha, entre em contato com o suporte via chat. Somente o administrador do _realm_ pode fazer a solicitação.

### CONTAS COM OAUTH <a href="#h_3104c5e810" id="h_3104c5e810"></a>

Atualizamos a documentação do artigo de Contas para adicionar o prazo de expiração de tokens previsto pelos provedores abaixo:

Microsoft - 3 meses\
Google - 6 meses\
Mercado Livre - 6 meses

[Clique aqui](https://intercom.help/godigibee/pt-BR/articles/4280470-utilizacao-de-accounts) para ler o artigo completo.

### COMPONENTES <a href="#h_52fa83c849" id="h_52fa83c849"></a>

* **Rest V2**: atualizamos a documentação do artigo do componente. [Clique aqui](https://intercom.help/godigibee/pt-BR/articles/4198646-rest-v2) para ler o artigo completo.

## Novidades 17/11/2021

### AUDITORIA <a href="#h_08cb6904d1" id="h_08cb6904d1"></a>

Realizamos melhorias na performance de consulta dos registros em Auditoria. Além disso, agora é possível identificar a referência do objeto auditado (Object ID). Isto é parte de um processo mais amplo de aprimoramento que incluirá a possibilidade de navegação até o objeto que foi auditado.

### FUNÇÕES { { DOUBLE BRACES } } <a href="#h_20f1c1008d" id="h_20f1c1008d"></a>

#### RANDOMSTRINGS <a href="#h_1a0329077e" id="h_1a0329077e"></a>

A função possibilita gerar _strings_ aleatórias com base em um _charset_ e um tamanho. Os _charsets_ disponíveis são: _ALPHANUMERIC_, _ASCII_, _NUMERIC_ e _ALPHABETIC_.\
Para ler sobre esta e outras Funções de String clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string).

#### RANDOMNUMBERS <a href="#h_af64c1c7ff" id="h_af64c1c7ff"></a>

A função possibilita gerar números aleatórios com base em um intervalo de valores inclusivos. Para saber mais sobre essa e outras Funções Numéricas clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4624062-double-braces-funcoes-numericas).\
\\

Nós também solucionamos alguns _bugs_:

* **Tela de Relacionamento:** corrigimos o erro que impossibilitava buscar registros na tela de configuração de Relacionamento.\\
* **Edição de Projetos:** corrigimos o erro que impedia acessar a tela de edição de Projetos.\\
* **Edição de Cápsulas:** corrigimos o erro que impedia acessar a tela de edição de Cápsulas.\\
* **Visualização de \_logs**\_**:** corrigimos o erro que impedia a consulta através do link de _Ver todos os Logs_ nos detalhes de uma transação.

## Novidades 02/11/2021

### CHAT <a href="#h_8cf6809eb7" id="h_8cf6809eb7"></a>

Para garantir que nosso suporte esteja sempre disponível, criamos uma funcionalidade alternativa para o envio de mensagens. Agora, é possível enviar pedidos ao nosso time de suporte mesmo que haja intermitências no serviço de chat _online_. As respostas serão enviadas por email.

### OAuth 2.0 <a href="#h_2c7fa10693" id="h_2c7fa10693"></a>

Após as atualizações do servidor de OAuth do Mercado Livre, modificamos o provedor OAuth do Mercado Livre para autenticar no _endpoint_ de contas do Brasil ([www.mercadolivre.com.br/authorization](https://app.intercom.com/)).

IMPORTANTE: os _tokens_ existentes em Accounts não são afetados. Novos _tokens_ serão obtidos através do novo _endpoint_.

### COMPONENTES <a href="#h_bcec1427ad" id="h_bcec1427ad"></a>

#### Google IAP Token <a href="#h_55af042394" id="h_55af042394"></a>

O novo componente possibilita gerar tokens do tipo _OpenID_ para autenticações de _proxies_ IAP (Identity Aware Proxy). Clique [aqui ](https://intercom.help/godigibee/pt-BR/articles/5696361-google-iap-token)para ler o artigo completo.

#### SQS <a href="#h_3a37525119" id="h_3a37525119"></a>

Adicionamos uma nova funcionalidade ao componente. Agora, o SQS também possibilita o envio de mensagens para filas do tipo FIFO do serviço AWS SQS. Clique [aqui ](https://intercom.help/godigibee/pt-BR/articles/5696376-sqs-aws)para ler o artigo completo.

### FUNÇÕES <a href="#h_0769226772" id="h_0769226772"></a>

#### CARDINALITYONE <a href="#h_033a9c9ffc" id="h_033a9c9ffc"></a>

A função possibilita aplicar uma cardinalidade de n:1 na estrutura informada, onde independente da quantidade de elementos na entrada, a saída será sempre 1 elemento. Para ler sobre essas e outras funções JSON, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json).

#### CARDINALITYMANY <a href="#h_5a02ceacbe" id="h_5a02ceacbe"></a>

A função possibilita normalizar a saída em cardinalidade múltipla. Ou seja, caso a entrada seja um array com n elementos, a saída será um array com n elementos e caso a entrada seja um único objeto, a saída será um array contendo este único objeto. Clique [aqui ](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json)para ler o artigo completo de funções JSON.\
\\

Nós também solucionamos alguns _bugs_:

* **Componente LDAP**: corrigimos o erro que causava um bloqueio na execução de _pipelines_ que possuíam o componente LDAP.\\
* **Chat**: Removemos a obrigatoriedade de um usuário possuir a permissão USER:READ para acessar o chat.\\
* **Histórico de versões de um \_pipeline**\_**:** Corrigimos o erro que causava tela branca quando o todas as versões de um _pipeline_ fossem arquivadas e quando uma das versões fosse restaurada.

## Novidades 19/10/2021

### COMPONENTES <a href="#h_61396cded7" id="h_61396cded7"></a>

* **NFS:** O componente manipula arquivos. É possível listá-los, fazer o download e upload de arquivos e deletá-los. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5599772-nfs) para acessar o artigo sobre NFS.

IMPORTANTE: o componente só é suportado em SaaS dedicado devido às características do protocolo NFS.\
\\

Nós também solucionamos um bug:

* **Seletor de ambiente em Monitor:** Corrigimos o bug que não armazenava o último ambiente selecionado ao alternar entre telas.

## Novidades 28/09/2021

### digibeectl - BETA Restricted <a href="#h_8746b8c8a7" id="h_8746b8c8a7"></a>

O digibeectl é o CLI (command-line interface) da Digibee que permite a execução de uma série de passos relacionados aos serviços disponíveis na Digibee Integration Platform HIP, até então somente disponíveis através da interface gráfica. Para saber mais sobre o digibeectl e sua documentação [clique](https://intercom.help/godigibee/pt-BR/articles/5214735-guia-de-uso-do-digibeectl).\
\
**IMPORTANTE:** Solicite sua participação no programa Beta Restricted do digibeectl via [chat ](https://www.godigibee.io/login)da plataforma ou com o time de Customer Success. Para entender o que é o programa Beta clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5267114-programa-beta).\\

### TRIGGERS <a href="#h_fc8d0c0f84" id="h_fc8d0c0f84"></a>

* **Trigger HTTP/REST:** agora os Triggers REST, HTTP e HTTP File adicionam o path invocado como parte das informações do request que chegam ao pipeline.\
  Você pode acessar o artigo destes Triggers nos link abaixo:\
  [Trigger REST](https://intercom.help/godigibee/pt-BR/articles/2950054-rest-trigger)\
  [Trigger HTTP](https://intercom.help/godigibee/pt-BR/articles/2950053-http-trigger)\
  [Trigger HTTP FIle](https://intercom.help/godigibee/pt-BR/articles/3615656-http-file-trigger-uploads)

### FUNÇÕES { {DOUBLE BRACES} } <a href="#h_9c594f871e" id="h_9c594f871e"></a>

* **PUSH:** agora é possível utilizar a função PUSH(_array_, _element_) para inserir novos elementos no final de um _array_ com o intuito de implementar uma estrutura de pilha. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json) para acessar o artigo sobre PUSH e outras funções de JSON.\
  \\
* **POP:** agora é possível utilizar a função POP(_array_) para remover o último elemento de um _array_ com o intuito de implementar uma estrutura de pilha. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json) para acessar o artigo sobre POP e outras funções de JSON.

## Novidades 10/09/2021

### TELA DE PIPELINE LOGS <a href="#h_1f1297b2c9" id="h_1f1297b2c9"></a>

Realizamos uma melhoria que visa diminuir o atraso na exibição dos logs de _pipelines_. Isto é parte de um processo mais amplo de aprimoramento do desempenho da coleta de logs.

\
\
Nós também solucionamos alguns _bugs_:

* **Listagem de \_pipelines**\_\*\* vazia:\*\* corrigimos um erro onde o botão de criar _pipeline_ não tinha ação.
* **Listagem vazia de implantações:** corrigimos o botão de atualização de implantações que não exibia o texto correto.

## Novidades 31/08/2021

### COMPONENTES <a href="#h_acfeab79e7" id="h_acfeab79e7"></a>

#### Hash <a href="#h_5942917a59" id="h_5942917a59"></a>

Adicionamos o algoritmo BCrypt ao componente _Hash_. Para ler o artigo atualizado, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/2950090-hash).\
\\

### NOVO LAYOUT <a href="#h_c6674e08d9" id="h_c6674e08d9"></a>

Recentemente comunicamos a habilitação automática do nosso novo _layout_. A partir de hoje (31/08), você não terá mais acesso ao _layout_ antigo. Ao fazer o _login_, você será direcionado para a Plataforma com uma estética consistente com o ciclo de construção de integrações, baseado em _Build_, _Run_ e _Monitor_.

Mas não se preocupe…

* essa mudança não afeta em nada a sua experiência
* continuaremos recebendo os seus comentários sobre o novo _layout_ através do canal de _feedback_

​

![](../.gitbook/assets/agosto\_01.png)

​

\
Nós também solucionamos alguns _bugs_:

* **Projetos:** corrigimos uma falha que não permitia a movimentação de _pipelines_ para projetos com caracteres especiais nos seus títulos. Além disso, _pipelines_ já existentes nos projetos não eram exibidos na tela de Run.
* **Monitor e Build:** realizamos ajustes para melhorar o carregamento da listagem e dos _dashboard_ de _pipelines_ nas telas _Monitor_ e _Build_.
* **Audit:** solucionamos o _bug_ que não permitia a visualização do menu de acesso no novo _layout_ da Plataforma.

## Novidades 17/08/2021

### COMPONENTES <a href="#h_d415ba040c" id="h_d415ba040c"></a>

#### Digibee JWT <a href="#h_b3fd43a975" id="h_b3fd43a975"></a>

O componente que já existia na nossa paleta, e que se chamava _JWT_, agora se chama _Digibee JWT_. Ele é próprio para autenticação que utiliza o _gateway_ da Digibee e não sofreu alterações em suas funções.

#### JWT <a href="#h_90f7512c99" id="h_90f7512c99"></a>

Agora está disponível o novo componente _JWT_, que gera e decodifica _tokens_ JWT para uso externo. Com isso, você pode manipular os _tokens_ JWS ou JWE conforme a sua necessidade de criptografia, assinaturas e _payloads_ dinâmicos.

**Nota:** para entender melhor a diferença entre os 2 componentes, clique nos títulos abaixo e acesse a documentação atualizada de cada um deles:

[Digibee JWT](https://intercom.help/godigibee/pt-BR/articles/2950114-digibee-jwt) (uso interno)\
[JWT](https://intercom.help/godigibee/pt-BR/articles/5489578-jwt) (uso externo)\\

### FUNÇÕES (DOUBLE BRACES) <a href="#h_a27a48419a" id="h_a27a48419a"></a>

#### REMOVEAT <a href="#h_59b68bce28" id="h_59b68bce28"></a>

Agora é possível utilizar a função REMOVEAT (_array_, _index_) para remover elementos específicos de um _array_ em um JSON. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json) para acessar o artigo sobre REMOVEAT e outras funções de JSON.

### RUN <a href="#h_8aa51ad52c" id="h_8aa51ad52c"></a>

Adicionamos uma nova validação do _pipeline_ que permite verificar se o _trigger_ configurado precisa de uma configuração dedicada para o ambiente do _realm_.

### NOVO LAYOUT <a href="#h_f546795dbb" id="h_f546795dbb"></a>

Estamos realizando a habilitação automática do nosso novo _layout_. A partir de agora, ao fazer o _login_, você será direcionado para a Plataforma com uma estética consistente com o ciclo de construção de integrações, baseado em _Build_, _Run_ e _Monitor_.\\

Mas não se preocupe…

* essa mudança não afeta em nada a sua experiência
* você terá até o dia 30/08/2021 para utilizar o _layout_ anterior, bastando clicar no ícone do seu perfil para selecioná-lo.

![](../.gitbook/assets/agosto\_02.png)

​

* continuaremos recebendo os seus comentários sobre o novo _layout_ através do canal de _feedback_ ​

!\[

]\(../.gitbook/assets/agosto\_03.png)

Nós também solucionamos um _bug_:

* **Digibee Storage:** resolvemos o problema que gerava um link incorreto para download ao realizar o _upload_ de um arquivo para um diretório que começasse com o caractere “ / ”.

## Novidades 03/08/2021

### COMPONENTES <a href="#h_a056faefdf" id="h_a056faefdf"></a>

#### SOAP V2 <a href="#h_4826b42234" id="h_4826b42234"></a>

Adicionamos uma nova funcionalidade ao componente, que permite a gravação da resposta de uma determinada requisição em arquivo local do _pipeline_. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3353639-soap-v2) para ler o artigo completo sobre o _SOAP V2_.

#### Kafka <a href="#h_e2bf0beaf0" id="h_e2bf0beaf0"></a>

Agora é possível informar a partição do tópico para a qual se deseja enviar uma mensagem ao _Kafka_. Para ler o artigo atualizado sobre o componente, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3576368-kafka).

#### DB V2 <a href="#h_460669dec7" id="h_460669dec7"></a>

Dados do tipo CLOB podem ser enviados através de um arquivo agora. Você pode ler o artigo atualizado do componente clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/3672590-db-v2).

### TRIGGERS <a href="#h_73396c6b4d" id="h_73396c6b4d"></a>

#### Kafka <a href="#h_f18fb61769" id="h_f18fb61769"></a>

Agora é possível informar as partições do tópico a consumir mensagens do _Kafka_. Para ler o artigo atualizado sobre o _trigger_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3967565-kafka-trigger).

### FUNÇÕES <a href="#h_7cc944d0fa" id="h_7cc944d0fa"></a>

#### ESCAPE/UNESCAPE <a href="#h_60a7d08030" id="h_60a7d08030"></a>

As funções ESCAPE e UNESCAPE agora permitem que o tipo de escape nos padrões JSON, CSV, _html_ e _xml_ seja informado. Para ler sobre essas e outras funções de _string_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string).

#### SIZE <a href="#h_1fb516de76" id="h_1fb516de76"></a>

Adicionamos um novo parâmetro à função SIZE. Com ele, é possível determinar se uma exceção deve ser lançada (_true_) ou não (_false_) quando algo der errado na verificação do tamanho de um objeto, _array_ ou JSON. Você pode ler o artigo sobre SIZE e outras funções de utilidades clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/4625538-double-braces-funcoes-de-utilidades).

### PROJETOS (BETA) <a href="#h_7e9b4e7165" id="h_7e9b4e7165"></a>

Por padrão, todos os Projetos atuais são visíveis para todos os usuários. Mas agora, além de criar e editar Projetos, você também pode dar permissões de visibilidade por usuário. Com essa melhoria, os seus Projetos serão visualizados por usuários específicos.\
\
\\

Nós também solucionamos alguns _bugs_:

* **Versões major de pipeline por Projeto (Beta):** ajustamos uma falha que permitia a apresentação de todas as versões do _pipeline_ mesmo quando uma versão _major_ específica era movida para outro Projeto.
* **Implantação:** corrigimos o problema que impedia a criação de novas implantações quando todas as implantações existentes em um _realm_ eram removidas.

## Novidades 20/07/2021

### DOCUMENTAÇÃO <a href="#h_1c2a455c9b" id="h_1c2a455c9b"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos sobre:

* [Dropbox](https://intercom.help/godigibee/pt-BR/articles/2950079-dropbox)
* [Retry](https://intercom.help/godigibee/pt-BR/articles/2950071-retry)
* [XML to JSON Transformer](https://intercom.help/godigibee/pt-BR/articles/2950110-xml-to-json-transformer)

\\

### COMPONENTES <a href="#h_d2bde518f3" id="h_d2bde518f3"></a>

#### DB V2 <a href="#h_6783d23d42" id="h_6783d23d42"></a>

Realizamos melhorias no componente _DB V2_ para possibilitar o recebimento de tipos de dados customizados (STRUCT) via _procedures_ em bancos de dados Oracle. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3672590-db-v2) para acessar o artigo atualizado sobre o _DB V2_.

#### Mongo DB <a href="#h_52db8615e2" id="h_52db8615e2"></a>

Agora você pode configurar propriedades de conexão (ex.: _timeout_) no componente _Mongo DB_. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/2950098-mongo-db) para ler o artigo.\
\\

Nós também solucionamos alguns _bugs_:

#### CSV to JSON V2 <a href="#h_b81e5263c0" id="h_b81e5263c0"></a>

Tornou-se possível especificar o _charset_ do arquivo a ser lido pelo componente _CSV to JSON V2_.

#### Ajustes no Portal <a href="#h_c142044cb6" id="h_c142044cb6"></a>

* redução no tempo para salvar _pipelines_;
* _pipelines_ com muitas versões deixaram de apresentar erro ao serem salvos;
* melhoria da responsividade na listagem de _pipelines_ e implantações;
* correção na tela de reexecução de _pipeline_, que impedia o envio da requisição;
* aperfeiçoamento na apresentação de informações sobre ajustes para a publicação de Cápsulas;
* a listagem dos nomes de _pipelines_ movidos entre projetos passou a ser exibida em sua totalidade.

### CÁPSULAS PÚBLICAS <a href="#h_605356faa6" id="h_605356faa6"></a>

Pensando facilitar cada vez mais o seu dia-a-dia com a Digibee Integration Platform, estamos disponibilizando Cápsulas prontas para utilização.

Veja quais são as Coleções que estão com novidades:

#### SAP <a href="#h_382fb478cb" id="h_382fb478cb"></a>

As Cápsulas da Coleção SAP foram todas projetadas para abstrair as chamadas ao SAP, encapsulando a capacidade de chamar funções remotas (RFC) ao sistema SAP e entregando flexibilidade e facilidade para integrar outros sistemas com o SAP.

* **SAP RFC - Connector (JSON Input):** Cápsula genérica, utilizada para qualquer operação com as funções remotas do SAP. É possível ler dados de tabelas e cadastros de modo mais completo, atualizar ou incluir novos cadastros (fornecedores, clientes, endereços, etc.).
* **SAP RFC - Read Nota Fiscal:** obtém informações da nota fiscal através da função _BAPI\_J\_1B\_NF\_GETDETAIL_.
* **SAP RFC - Connectivity test:** Cápsula para testes de conectividade com o SAP.
* SAP RFC - Read Table: consulta dados das tabelas do SAP através da RFC READ\_TABLE.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5406297-sap) para ler o artigo completo sobre essa Coleção.#\\

## Novidades 06/07/2021

### TERMO DE USO <a href="#h_1dbfef7c4e" id="h_1dbfef7c4e"></a>

Atualizamos o nosso Termo de Uso, que será ativado em 08/07/2021 às 12h (horário de Brasília, GMT-03). Para garantir o seu uso individual da Plataforma, faça o seu _login_, leia atentamente o conteúdo e selecione a opção “Eu aceito o Termo descrito acima”.

### DOCUMENTAÇÃO <a href="#h_1f5f01a442" id="h_1f5f01a442"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos sobre:

* [Digibee Storage](https://intercom.help/godigibee/pt-BR/articles/2950061-digibee-storage)
* [HTTP Trigger](https://intercom.help/godigibee/pt-BR/articles/2950053-http-trigger)
* HTTP File Trigger ([Uploads](https://intercom.help/godigibee/pt-BR/articles/3615656-http-file-trigger-uploads) e [Downloads](https://intercom.help/godigibee/pt-BR/articles/3648727-http-file-trigger-downloads))
* [REST Trigger](https://intercom.help/godigibee/pt-BR/articles/2950054-rest-trigger)

### CONFIGURAÇÃO DE CONSUMERS <a href="#h_57252c2886" id="h_57252c2886"></a>

Fizemos melhorias na interface de associação de _pipelines_ a um _consumer_, garantindo desempenho superior no carregamento de lista de _pipelines_.

### EXPIRAÇÃO DA SESSÃO <a href="#h_12ef5c2ece" id="h_12ef5c2ece"></a>

Por questões de segurança, a sua sessão na Plataforma passará a expirar a cada 60 dias, havendo atividade ou não.

### MELHORIAS DE USABILIDADE <a href="#h_ca94bd6802" id="h_ca94bd6802"></a>

Estamos sempre buscando melhorar a sua experiência na Plataforma. Veja o que fizemos:

* adicionamos informações sobre as configurações utilizadas no _trigger_ dos _pipelines_;
* inserimos a data de ocorrência do último erro do _pipeline_.

​

![](../.gitbook/assets/julho\_01.png)

!\[

]\(../.gitbook/assets/julho\_02.png)

Nós também solucionamos um _bug_:

* **Coleções:** corrigimos uma falha que permitia a exibição de Coleções, Grupos e Cápsulas mesmo após arquivamento. Agora esses itens são exibidos apenas quando estão ativos.

## Novidades 22/06/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### MELHORIAS DE USABILIDADE <a href="#h_c3e4443cbb" id="h_c3e4443cbb"></a>

Estamos sempre buscando melhorar a sua experiência na Plataforma. Veja o que fizemos:

* adicionamos um novo componente de prévia de carregamento.

​

![](../.gitbook/assets/julho\_03.gif)

### COMPONENTES <a href="#h_9f412c4fd8" id="h_9f412c4fd8"></a>

#### DBs <a href="#h_d8aac01f87" id="h_d8aac01f87"></a>

Os componentes [DB V2](https://intercom.help/godigibee/pt-BR/articles/3672590-db-v2) e [Stream DB V3](https://intercom.help/godigibee/pt-BR/articles/3527793-stream-db-v3) agora podem realizar consultas que manipulam o tipo CLOB como arquivo. Clique no título dos componentes para acessar a documentação atualizada.\\

#### Kafka <a href="#h_8b9d5648c8" id="h_8b9d5648c8"></a>

Agora é possível informar um _truststore_ que contém a cadeia de certificados confiáveis e/ou um _keystore_ que contém a cadeia de certificados e a chave privada do lado cliente para publicar nos tópicos de Kafka. Para acessar o artigo atualizado sobre o componente, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3576368-kafka).

### TRIGGERS <a href="#h_b1961cb809" id="h_b1961cb809"></a>

#### Kafka <a href="#h_11899635f8" id="h_11899635f8"></a>

Agora é possível informar um _truststore_ que contém a cadeia de certificados confiáveis e/ou um _keystore_ que contém a cadeia de certificados e a chave privada do lado cliente para consumir dos tópicos de Kafka. Para acessar o artigo atualizado sobre o _trigger_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3967565-kafka-trigger).

### DOCUMENTAÇÃO <a href="#h_146ec5418f" id="h_146ec5418f"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos de:

* [Google Storage](https://intercom.help/godigibee/pt-BR/articles/2950057-google-storage)
* [XML Transformer](https://intercom.help/godigibee/pt-BR/articles/4198773-xml-transformer)
* [AES Cryptography](https://intercom.help/godigibee/pt-BR/articles/3516037-aes-cryptography)

### CÁPSULAS <a href="#h_f93143fe55" id="h_f93143fe55"></a>

Agora você pode:

* editar nomes de grupos;
* remover grupos;
* criar uma Cápsula a partir de um grupo existente.

​

![](../.gitbook/assets/julho\_04.gif)

​

\
_A funcionalidade acima requer permissões específicas que o seu usuário talvez ainda não tenha. Caso necessário, entre em contato com o administrador do seu Realm._

### ORACLE <a href="#h_b20dae7989" id="h_b20dae7989"></a>

Agora é possível receber tipos customizados do Oracle em _queries_ que utilizam os componentes DB V2 e Stream DB V3.\
\\

Nós também solucionamos um _bug_:

* **Stream DB V3:** solucionamos o _bug_ que interrompia a execução de um _pipeline_ com erro quando um BLOB nulo era recebido.

## Novidades 08/06/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### NOVO LAYOUT E PROJETOS BETA <a href="#h_62e125477d" id="h_62e125477d"></a>

A nova tela de Run também está disponível no nosso novo _layout_.

​

![](../.gitbook/assets/junho\_01.jpg)

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5267106-novo-layout) para acessar o artigo atualizado sobre o novo _layout_.

### DOCUMENTAÇÃO <a href="#h_ea47dc3136" id="h_ea47dc3136"></a>

Atualizamos a leitura sobre um componente para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar o novo artigo de Assert clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/2950063-assert-v1).

## Novidades 25/05/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### NOVO LAYOUT E PROJETOS BETA <a href="#h_8aa5538c07" id="h_8aa5538c07"></a>

Estamos lançando a versão beta do nosso novo _layout_ e da funcionalidade Projetos. Para que você possa aproveitar o melhor que essas novidades têm a oferecer, criamos artigos que esclarecem:

* o que o novo _layout_ traz de diferente e como habilitá-lo
* o que é a funcionalidade Projetos, como ela funciona, como habilitá-la e o passo-a-passo de utilização

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5267106-novo-layout) para acessar o artigo sobre o novo _layout_.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5267035-projetos) para acessar o artigo sobre a funcionalidade Projetos.

### COMPONENTES <a href="#h_25a7d03259" id="h_25a7d03259"></a>

* **Stream XML File Reader:** criamos um novo componente que permite que grandes estruturas XML disponibilizadas em arquivos sejam percorridas item a item, com filtros e de forma eficiente em termos de uso de memória. Leia o artigo sobre _**Stream XML File Reader**_ clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/5265780-stream-xml-reader).
* **Object Store:** inserimos na documentação do componente _Object Store_ uma explicação sobre a operação UPSERT dentro de um componente _loop_ quando a opção de execução em paralelo está habilitada. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3107068-object-store) para ler o artigo atualizado.

### RUNTIME <a href="#h_120bdda8bd" id="h_120bdda8bd"></a>

* **Validação de pipelines:** melhoramos a sua experiência com a Plataforma ao prover mais _feedback_ durante a implantação, economizando tempo e evitando implantações consecutivas por pequenas falhas.
* **Mudança visual:** agora ficou ainda mais fácil de você entender o status das implantações. Veja como está o visual dos cartões:

![](../.gitbook/assets/maio\_01.png)

![](../.gitbook/assets/maio\_02.png)

\
\
Nós também solucionamos alguns _bugs_:

![](../.gitbook/assets/maio\_03.png)

* **Runtime e configurações:** solucionamos o _bug_ que impedia a exibição de mensagens de confirmação ou falha em processos de criação, remoção ou edição nas configurações ou implantações.
* **REST V2:** resolvemos o problema que impedia a utilização de _Custom Accounts_ na configuração de uma chamada com multipart/form-data e _Double Braces_.
* **S3 Storage:** ajustamos o nome do parâmetro _Link Expiration (in ms)_ para _Expiration Timestamp (in ms)_ e, com isso, você tem mais clareza sobre como realizar a devida configuração do parâmetro. Para entender melhor essa mudança, acesse o artigo atualizado do _**S3 Storage**_ clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/3557995-s3-storage).

### CÁPSULAS PÚBLICAS <a href="#h_721962c0d1" id="h_721962c0d1"></a>

Pensando facilitar cada vez mais o seu dia-a-dia com a Digibee Integration Platform, estamos disponibilizando Cápsulas prontas para utilização.

Veja quais são as Coleções que estão com novidades:

#### Digibee Tools <a href="#h_aa48a842e2" id="h_aa48a842e2"></a>

Essa Coleção de Cápsula traz ferramentas que auxiliam na padronização do seu _pipeline_ por meio das melhores práticas, assim como agilidade, qualidade em validações e transformações prontas.\\

* **CPF CNPJ Validator:** possibilita que o número do dígito verificador de documentos brasileiros referente a cadastro de pessoas seja validado.
* **Digibee Publish Error:** envia notificações de mensagens padronizadas para que se tenha maior clareza e eficiência nos alertas e tratamentos de erros.
* **Parallel Execution List to Objects:** transforma _arrays_ de objetos produzidos por execuções paralelas. Essa Cápsula é bastante útil quando utilizada em combinação com o componente _Parallel Execution_.
* **Sort Array by field:** ordena listas no formato JSON a partir de um campo determinado.
* **Validate Consumers:** valida a quantidade de _consumers_ configurados de acordo com o Runtime do _pipeline_.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5261176-digibee-tools) para ler o artigo completo sobre essa Coleção.\\

## Novidades Digibee

O que estamos entregando para melhorar a sua experiência com a Digibee Integration Platform.

### **Tenha acesso ao novo \_layout**\_\*\* e a Projetos!\*\* <a href="#h_e137583221" id="h_e137583221"></a>

Sabia que a partir do dia **25/05/2021** você terá acesso à versão beta do nosso novo _layout_ e da funcionalidade de Projetos?

\
**Novo layout**

O novo _layout_ da Digibee Integration Platform é o primeiro passo da revolução que estamos promovendo na nossa interface. A ideia é que você usufrua de uma navegação mais objetiva e com uma estética mais agradável, amigável e consistente. Com isso também queremos te oferecer, de maneira mais ágil, funcionalidades como Projetos.\
\
**Projetos**

Projetos são como pastas, que podem ser utilizados para organizar _pipelines_. Na versão beta você poderá:

* criar projetos informando nome e descrição;
* alterar nome e descrição de projetos;
* mover _pipelines_ de um projeto para outro;
* criar _pipelines_ associados a um projeto;
* arquivar projetos que não tenham _pipelines_.

#### O QUE VOCÊ PODE QUERER SABER... <a href="#h_cfb857ce1d" id="h_cfb857ce1d"></a>

#### O que são versões beta? <a href="#h_d11183151d" id="h_d11183151d"></a>

As versões beta surgem como uma oportunidade para verificarmos como os usuários da Plataforma se sentem em relação à estabilidade, à escalabilidade, ao desempenho e à usabilidade de novos _layouts_ e funcionalidades.

Enquanto você estiver utilizando as versões beta, algumas situações indesejadas podem ocorrer. O motivo para isso é que elas não são as versões finais e ainda seguem em processo de melhoria. Ao final do período de teste, levando em consideração o _feedback_ dos usuários, o reporte de eventuais erros de execução ou a identificação de problemas de usabilidade, optaremos por prorrogar as versões beta ou disponibilizar as versões finais dos _layouts_ e das funcionalidades.

#### Como eu posso aderir às versões beta? <a href="#h_efbee7b5e5" id="h_efbee7b5e5"></a>

Todos os usuários da Plataforma podem aderir às versões beta. Ao ativar o novo _layout_, você automaticamente realiza a sua adesão e concorda com os termos de uso. Para acessar as funcionalidades, ative o Layout Beta a partir de sua conta:

​

![](../.gitbook/assets/maio\_04.png)

​\
\
**Quais são os termos de uso da versão beta na Plataforma?**

Para utilização da versão beta, você deve:

* respeitar todos os termos de uso da versão operacional;
* concordar que a utilização da versão beta da Plataforma implica em não estar coberto pelo SLA aplicado à versão operacional ativa;
* concordar que a versão beta e as suas funcionalidades podem não ser disponibilizadas em uma versão operacional;
* não utilizar os meios normais de suporte. Comentários, críticas, elogios e sugestões devem ser registradas através do canal “Enviar Feedback”.\\

**Como eu faço para enviar feedback sobre uma versão beta?**

A Plataforma já possui um canal para que os usuários enviem _feedbacks_. Veja:

​

![](../.gitbook/assets/maio\_05.png)

​

Você deve encaminhar todas as suas sugestões, elogios, reclamações e comentários por meio desse canal. Dessa forma, os seus _feedbacks_ são encaminhados para a equipe responsável, que se encarrega de fazer ajustes e melhorias.

Caso você tenha qualquer outra dúvida, fique à vontade para entrar em contato com o seu Customer Success Manager.

#### Como eu faço para voltar para o layout antigo? <a href="#h_aef62553b8" id="h_aef62553b8"></a>

Basta acessar o menu do seu perfil (no exemplo abaixo representado pela letra A com fundo laranja) e selecionar a opção "Default Layout":

​

![](../.gitbook/assets/maio\_06.png)

## Novidades 11/05/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### COMPONENTES <a href="#h_c01d543fba" id="h_c01d543fba"></a>

#### gRPC <a href="#h_c9677d898d" id="h_c9677d898d"></a>

Disponibilizamos um novo componente que torna possíveis chamadas gRPC através da Digibee Integration Platform. Com isso você pode executar chamadas do tipo _unary_ e _client stream_. Leia o artigo sobre o componente _gRPC_ clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/5222262-grpc).

#### Stream JSON File Reader <a href="#h_e288051798" id="h_e288051798"></a>

Criamos um novo componente que permite que grandes estruturas JSON disponibilizadas em arquivos sejam percorridas item a item, com filtros e de forma eficiente em termos de uso de memória. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5222126-stream-json-file-reader) para acessar o artigo sobre o _**Stream JSON File Reader**_.

#### Log <a href="#h_ffac24d38a" id="h_ffac24d38a"></a>

Campos marcados como sensíveis em seu _realm_ ou na configuração de um _pipeline_ agora são ofuscados no componente _**Log**_. Você pode saber mais sobre esse componente clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/2950096-log).

### DOCUMENTAÇÃO <a href="#h_c876f7e80a" id="h_c876f7e80a"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar o novo artigo de:

* [Stream Excel](https://intercom.help/godigibee/pt-BR/articles/2950058-stream-excel)

### CÁPSULAS <a href="#h_9b8401c2e7" id="h_9b8401c2e7"></a>

Para facilitar a sua experiência na criação de Coleções de Cápsulas, criamos um guia de melhores práticas para personalização. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5215091-criacao-de-colecoes-de-capsulas) para acessar a leitura.

### RUNTIME <a href="#h_88579811aa" id="h_88579811aa"></a>

Quando uma das réplicas de um _pipeline_ era reinicializada, apresentávamos o termo "crash". No entanto, entendemos que o termo "crash" não representa fielmente o ocorrido. Por isso, passamos a adotar o termo "recycled".

![](../.gitbook/assets/maio\_07.png)

Nós também solucionamos alguns _bugs_:

* **Configuração de componentes:** solucionamos um _bug_ que permitia que um campo obrigatório fosse preenchido apenas com espaços em branco. Com isso, _pipelines_ e componentes são corretamente documentados.
* **Configuração de pipelines:** corrigimos o erro que impedia a alteração dos valores de InSpec/OutSpec de um _pipeline_.

### CÁPSULAS PÚBLICAS <a href="#h_78dc1f17aa" id="h_78dc1f17aa"></a>

Pensando facilitar cada vez mais o seu dia a dia com a Digibee Integration Platform, estamos disponibilizando Cápsulas prontas para utilização.

Veja quais são as Coleções de Cápsulas que estão com novidades:

#### Google Sheets <a href="#h_1f7c72b88f" id="h_1f7c72b88f"></a>

* **Get Spreadsheets By Id:** consulte metadados na sua planilha compartilhada.
* **Get Rows Values by Range:** obtenha dados existentes dentro da planilha e trabalhe com consultas paginadas de acordo com o intervalo desejado.
* **Append Data:** escreva novos dados em uma planilha existente.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5209400-google-sheets) para ler o artigo completo sobre essa Coleção de Cápsulas.

### E VEM POR AÍ... <a href="#h_2d2563845d" id="h_2d2563845d"></a>

O _**gRPC Trigger**_ permitirá a exposição de _pipelines_ seguindo o protocolo gRPC.

## Novidades 27/04/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### MÉTRICAS DE PIPELINE <a href="#h_b6cf5d94d9" id="h_b6cf5d94d9"></a>

Lançamos uma funcionalidade que te permite acompanhar o que está acontecendo com os _pipelines_ por meio destes novos gráficos em tempo real:\\

* Execuções de _pipeline_ por segundo (eps)
* Tempo de resposta do _pipeline_ (em milissegundos)
* Execuções de _pipeline_ em andamento (_inflights_)
* Tamanho das mensagens do _pipeline_ (_bytes_)
* Consumo de memória do _pipeline_ (%)
* Mensagens na fila do _pipeline_ (mensagens)
* Consumo de CPU do _pipeline_ (%)

​

![](../.gitbook/assets/abril\_01.gif)

​

### NAVEGAÇÃO DA PLATAFORMA <a href="#h_30c8fc1751" id="h_30c8fc1751"></a>

Para que você se familiarize melhor com os termos e conceitos relacionados à navegação da Digibee Integration Platform, vamos lançar uma série de artigos esclarecedores.

Para começar, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5182067-runtime) e leia sobre _Runtime_.

### COMPONENTES <a href="#h_9f960cc50e" id="h_9f960cc50e"></a>

Atualizamos o artigo do componente LDAP. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3051016-ldap) para acessá-lo.

### COLEÇÕES <a href="#h_8e39575f7e" id="h_8e39575f7e"></a>

Agora você pode arquivar Coleções que não estão mais sendo utilizadas.

​

![](<../.gitbook/assets/abril\_02 (1).gif>)

### FUNÇÕES <a href="#h_a33557cafe" id="h_a33557cafe"></a>

Criamos novas funções para otimizar a sua experiência com integrações na Plataforma. Veja quais são elas:

\
**Funções de String**

* CONTAINS

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string) para ler o artigo sobre essa e outras _Funções de String_.

\
**Funções de JSON**

* GETELEMENTAT
* LASTELEMENT
* NEWEMPTYOBJECT
* NEWEMPTYARRAY

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623857-double-braces-funcoes-de-json) para ler o artigo sobre essas e outras _Funções de JSON_.

### FAIL ON ERROR <a href="#h_310930424d" id="h_310930424d"></a>

Atualizamos a descrição de _Fail On Error_ na documentação de alguns dos nossos componentes, sem modificar o comportamento desse parâmetro de configuração. Reveja os seguintes artigos:

* [Stream Excel](https://intercom.help/godigibee/pt-BR/articles/2950058-stream-excel)
* [Stream File Reader](https://intercom.help/godigibee/pt-BR/articles/2950104-stream-file-reader)
* Stream DB ([V1](https://intercom.help/godigibee/pt-BR/articles/2950105-stream-db-v1) e [V3](https://intercom.help/godigibee/pt-BR/articles/3527793-stream-db-v3))
* [Stream File Reader Pattern](https://intercom.help/godigibee/pt-BR/articles/4689428-stream-file-reader-pattern)
* [Retry](https://intercom.help/godigibee/pt-BR/articles/2950071-retry)
* [For Each](https://intercom.help/godigibee/pt-BR/articles/2950075-for-each)\\

### RETENÇÃO DE EXECUÇÕES E LOGS <a href="#h_b904db21d8" id="h_b904db21d8"></a>

Corrigimos a informação de retenção de dados nas telas:

* painel
* execuções concluídas
* _pipeline logs_

### CÁPSULAS PÚBLICAS <a href="#h_4f19e8dfaf" id="h_4f19e8dfaf"></a>

Pensando facilitar cada vez mais o seu dia-a-dia com a Digibee Integration Platform, estamos disponibilizando Cápsulas prontas para utilização.

Veja quais são as Coleções que estão com novidades:

#### Gupy <a href="#h_cb87e282c6" id="h_cb87e282c6"></a>

* **Configuring Webhooks:** configure e consulte os _webhooks_ da Gupy com mais agilidade.
* **Upsert Department:** gerencie cadastros de departamentos para as vagas existentes na Gupy.
* **Gupy Business Flow JOB:** fluxo para a criação de vagas, que agrupa passos importantes (cargo, departamento, filial, _template_) de forma simples e mantém a segurança e o tratamento de erros.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5152034-gupy) para ler o artigo completo sobre essa Coleção.

\\

### E VEM POR AÍ... <a href="#h_a515a9d5a3" id="h_a515a9d5a3"></a>

* Em breve você poderá gerenciar as imagens dos cabeçalhos de Cápsulas e Coleções em uma área específica. Esse gerenciamento pode ser feito até mesmo por usuários que não têm permissão para criar Cápsula. Com isso, não há preocupações em relação à segurança das Cápsulas.
* Estamos trabalhando para que a Plataforma suporte o uso do protocolo gRPC na construção de _pipelines_.

## Novidades 13/04/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### DOCUMENTAÇÃO <a href="#h_c7f6968a9c" id="h_c7f6968a9c"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos de:

* [Transformer (JOLT)](https://intercom.help/godigibee/pt-BR/articles/2950062-transformer-jolt)
* [File Writer](https://intercom.help/godigibee/pt-BR/articles/4177860-file-writer)

### TELA DE LOGS <a href="#h_4bbca00021" id="h_4bbca00021"></a>

O artigo “Busca na tela de logs” foi renomeado para “Tela de logs” e passou trazer informações sobre dados sensíveis e limites de retenção, incluindo o tamanho da mensagem (conceito de DGB Truncated). Para acessar a leitura atualizada, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4622404-tela-de-logs).

\
\
Nós também solucionamos um _bug_:

* **Tela de consumer:** normalizamos o acesso à tela de configurações quando não há dados no Realm.

### E VEM POR AÍ... <a href="#h_3d53d18d6e" id="h_3d53d18d6e"></a>

* **Layout de navegação:** em breve teremos novidades de navegação para melhorar a sua experiência na Plataforma.

​

![](../.gitbook/assets/abril\_03.jpg)

* **Projetos:** você poderá organizar melhor os seus _pipelines_, o que garante um processo de gestão mais efetivo.
* **Métricas de pipelines:** que tal acompanhar o que está acontecendo com os seus _pipelines_ por meio de novos gráficos em tempo real?

## Novidades 30/03/2021

Gostaríamos de compartilhar algumas melhorias e novidades:\\

### COMPONENTES <a href="#h_44d723d8de" id="h_44d723d8de"></a>

#### HTML to PDF <a href="#h_e03e1c570d" id="h_e03e1c570d"></a>

O componente HTML to PDF passou a suportar a inclusão de proteção por senha e também a definição de permissões de acesso. Dessa forma, é possível gerar PDFs com uma camada de segurança e com permissões de acesso específicas. Para ler o artigo completo sobre o componente, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4252030-html-to-pdf).

#### Kafka <a href="#h_5ea355f544" id="h_5ea355f544"></a>

Adicionamos novas configurações ao componente Kafka, possibilitando que os valores do cabeçalho sejam enviados para o _broker_ Kafka aplicando o _charset_ selecionado. Além disso, o valor do cabeçalho de uma mensagem pode ser interpretado em formato binário (base64). Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3576368-kafka) para acessar o artigo atualizado sobre o componente.

#### Log <a href="#h_ab09f2c17c" id="h_ab09f2c17c"></a>

Implementamos uma melhoria ao componente Log e, a partir de agora, você não precisa utilizar funções para retirar os caracteres de quebra de linha no seu uso. Leia o artigo atualizado desse componente clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/2950096-log).

### TRIGGERS <a href="#h_6ebf400f88" id="h_6ebf400f88"></a>

#### Kafka <a href="#h_69c0dd35a9" id="h_69c0dd35a9"></a>

Adicionamos o recurso que pode ser ativado para possibilitar o recebimento de um ou mais cabeçalhos (_headers_) em mensagens consumidas do _broker_ Kafka. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3967565-kafka-trigger) para acessar o artigo sobre o Kafka _trigger_.

### FUNÇÕES <a href="#h_6a910cabab" id="h_6a910cabab"></a>

Para otimizar a sua experiência de leitura, melhoramos os exemplos no artigo “Double Braces - Funções de String”, mais especificamente nas funções INDEXOF e LASTINDEXOF. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623887-double-braces-funcoes-de-string) para acessar o artigo.

### DOCUMENTAÇÃO <a href="#h_a04bacd9bc" id="h_a04bacd9bc"></a>

Atualizamos a leitura sobre um componente para que você tenha uma melhor experiência com as suas integrações.

Acesse o novo artigo de Scheduler Trigger clicando [aqui](https://intercom.help/godigibee/pt-BR/articles/4184400-custom-scheduler-trigger).\\

\
Nós também solucionamos um _bug_:

* **Componentes DB:** resolvemos o problema que impedia o uso de componentes de bancos de dados com bases do tipo OLAP.

## Novidades 16/03/2021

Gostaríamos de compartilhar algumas melhorias e novidades

### COMPONENTES <a href="#h_eeaf776aa8" id="h_eeaf776aa8"></a>

#### SSH Remote Command <a href="#h_6ffa32d404" id="h_6ffa32d404"></a>

Entregamos um novo componente que permite a execução de comandos em um servidor que suporte SSH remoto. Para saber mais sobre o _SSH Remote Command_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/5031347-ssh-remote-command).

\
**Kafka**

Adicionamos o recurso de inclusão de um ou mais cabeçalhos (_headers_) na mensagem enviada para o _broker_ Kafka. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3576368-kafka) para ler o artigo completo e atualizado do componente.\\

### DOCUMENTAÇÃO

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos de:

* [For Each](https://intercom.help/godigibee/pt-BR/articles/2950075-for-each)
* [RabbitMQ](https://intercom.help/godigibee/pt-BR/articles/4223092-rabbitmq)

### FEEDBACK <a href="#h_4499c0218c" id="h_4499c0218c"></a>

Gostaríamos de saber quais são os seus comentários e sugestões de melhoria para a Plataforma. Por isso, te convidamos a utilizar o novo recurso de compartilhamento de opiniões. Veja como é fácil enviar o seu _feedback_:

​

![](../.gitbook/assets/março\_01.gif)

​\
\
Nós também solucionamos alguns _bugs_:

* **Stream DB V3:** resolvemos uma falha na gestão do _pool_ de conexões que, após uma execução com erro de _timeout_, impedia que as conexões fossem devolvidas ao _pool_. Além disso, eliminamos o problema que causava a interpretação incorreta de expressões _Double Braces_ duplicadas no _Stream DB V3_.
* **Do While e Parallel Execution:** solucionamos o _bug_ que criava uma inconsistência nos componentes _Do While_ e _Parallel Execution_ quando eram criadas versões Major de _pipelines_.
* **Telas de configuração:** corrigimos um problema de proporção nas telas de configuração de Consumer, Global, Relation e Multi instance, que dificultava a visualização do formulário.
* **Tela de erro padrão:** anteriormente erros não tratados geravam uma tela em branco. Agora uma tela com a exibição de erros padrão é mostrada.

## Novidades 02/03/2021

Gostaríamos de compartilhar algumas melhorias e novidades:\\

### FUNÇÕES <a href="#h_95ddeb2d92" id="h_95ddeb2d92"></a>

Adicionamos a função _DIFFDATE_ à Plataforma. Agora você pode calcular a diferença de anos, meses, dias, horas, minutos, segundos e milissegundos entre duas datas. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623805-double-braces-funcoes-de-data) para acessar o nosso artigo completo sobre essa e outras Funções de Data.

### DOCUMENTAÇÃO <a href="#h_5f4d257630" id="h_5f4d257630"></a>

Atualizamos a leitura sobre alguns componentes para que você tenha uma melhor experiência com as suas integrações.

Você pode acessar os novos artigos de:

* [JMS](https://intercom.help/godigibee/pt-BR/articles/2950091-jms)
* [Validator](https://intercom.help/godigibee/pt-BR/articles/2950108-validator)
* [REST Trigger](https://intercom.help/godigibee/pt-BR/articles/2950054-rest-trigger)

### TELA DE PIPELINE LOGS <a href="#h_2ff318ad51" id="h_2ff318ad51"></a>

Passamos a fornecer uma melhor visualização dos _logs_ referentes aos passos de implantação de _pipelines_. Com isso, você pode verificar o andamento da implantação e as mensagens de erro que antes não apareciam.

### TELA DE LISTAGEM DE PIPELINES <a href="#h_86a1581b14" id="h_86a1581b14"></a>

Redesenhamos a apresentação da listagem de _pipelines_ para que você possa aproveitar melhor a tela. Além disso, tornamos a tela mais responsiva, se adaptando melhor a diferentes resoluções.

### FEEDBACK <a href="#h_46d9e2215f" id="h_46d9e2215f"></a>

Criamos um meio exclusivo para você compartilhar a sua opinião sobre a Plataforma, podendo enviar comentários gerais e sugestões de melhoria. Esse recurso está presente em cada uma das nossas telas, o que nos possibilita saber a origem da sua opinião. Veja como nos enviar o seu _feedback_:

![](../.gitbook/assets/março\_02.gif)

​\
\
Nós também solucionamos alguns _bugs_:

* **JSON to CSV V2:** corrigimos um problema que exibia uma mensagem de erro do componente DB V2, quando na verdade o erro ocorria na execução do componente JSON to CSV V2.
* **Stream DB V3:** os componentes de _stream_ (_Streamers DB_ e _File Reader_) passaram a fechar os recursos de maneira adequada após o término das suas execuções ao invés de fechá-los apenas após o término da execução do _pipeline_.
* **Append File:** ajustamos a lista de "Files To Append" para suportar _Double Braces_ no campo onde é informado o nome do arquivo.
* **Zip File:** ajustamos a lista de "Files" para suportar _Double Braces_ no campo onde é informado o nome do arquivo.
* **Email Trigger V2:** arrumamos uma falha que permitia que operações efetuadas em mensagens recebidas pelo _trigger_ Email V2 não fossem corretamente movidas, marcadas como lidas ou removidas, pois a caixa postal já havia se desconectado.
* **Pipeline com multi-instância:** eliminamos o _bug_ que permitia a implantação de um _pipeline_ com nome conflitante entre _pipelines_ multi-instância e não multi-instância. Por exemplo: o _pipeline_ "store-newyork" cujo nome é "store" e a instância é "newyork" poderia conflitar com um _pipeline_ previamente implantado com o nome "store-newyork". Apesar de serem _pipelines_ diferentes, os nomes coincidem e isso não é permitido

## Novidades 16/02/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### COMPONENTES <a href="#h_02ffc6adf1" id="h_02ffc6adf1"></a>

#### Base64 <a href="#h_8c48ad032d" id="h_8c48ad032d"></a>

Criamos um componente que possibilita a transformação de um arquivo ou texto para o formato Base64, gerando como saída um novo texto ou um novo arquivo de acordo com sua necessidade. Para ler o artigo sobre o _Base64_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4903281-base64).

#### Append File <a href="#h_69ac1574f6" id="h_69ac1574f6"></a>

Entregamos um novo componente que te permite acrescentar o conteúdo de um arquivo a um outro arquivo já existente. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4903256-append-file) para ler o artigo sobre o _Append File_.

#### SOAP V2 <a href="#h_8011a46fbf" id="h_8011a46fbf"></a>

Adicionamos uma nova funcionalidade ao componente SOAP V2 para que você possa especificar que o corpo da requisição será fornecido por um arquivo. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3353639-soap-v2) para acessar o artigo atualizado sobre o _SOAP V2_.

#### DB V2 <a href="#h_c10ed8b1f2" id="h_c10ed8b1f2"></a>

Agora é possível definir o tamanho do _pool_ de conexões do _DB V2_ como um número equivalente à quantidade de _consumers_ configurados durante a implantação. Além disso, você pode definir que o _pool_ é exclusivo do componente.

#### JMS <a href="#h_9210a6cd61" id="h_9210a6cd61"></a>

Passamos a suportar o IBM MQ, um novo _broker_ do componente _JMS_. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/2950091-jms) para ler o artigo atualizado.

### TRIGGERS <a href="#h_f87eb7a5e7" id="h_f87eb7a5e7"></a>

#### HTTP Trigger <a href="#h_7145c4b753" id="h_7145c4b753"></a>

Atualizamos a leitura sobre o _HTTP Trigger_ para que você tenha uma melhor experiência com as suas integrações. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/2950053-http-trigger) para acessar o artigo.

#### JMS Trigger <a href="#h_df6ee80fae" id="h_df6ee80fae"></a>

Passamos a suportar o IBM MQ, um novo _broker_ do _JMS Trigger_. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3918191-jms-trigger) para ler o artigo atualizado.

### BANCOS DE DADOS <a href="#h_24a049514f" id="h_24a049514f"></a>

Homologamos na Plataforma o banco de dados Snowflake. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4520594-bancos-de-dados-suportados) para saber quais outros bancos de dados são suportados.\\

### TEMPO DE EXECUÇÃO EXCEDIDO <a href="#h_edf22ecace" id="h_edf22ecace"></a>

Melhoramos a mensagem que informa sobre o andamento das execuções que excedem o limite máximo de espera do _test-mode_ na tela do _pipeline canvas_. Além disso, passamos a informar que essas execuções podem ser consultadas no Dashboard, dentro de “Execuções concluídas”.

### MELHORIAS DE USABILIDADE <a href="#h_0794492930" id="h_0794492930"></a>

Estamos sempre buscando melhorar a sua experiência na Plataforma.

Agora, ao clicar no link “Voltar para _pipelines_” ou no logo da Digibee, você pode usar os seguintes modificadores para abrir uma nova guia, preservando o _pipeline canvas_ aberto:

* **Windows / Linux:** CTRL + botão esquerdo do mouse
* **Mac:** COMMAND + botão esquerdo do mouse

### SEGURANÇA <a href="#h_a1b5ccdf1e" id="h_a1b5ccdf1e"></a>

* Alteramos a forma de recuperação de senha, onde um link de troca é enviado junto com o e-mail contendo as instruções.
* Melhoramos a sensibilidade do mecanismo RECAPTCHA, diminuindo os casos de falsos positivos.

\
\
Nós também solucionamos um _bug_:

* **Runtime:** realizamos um ajuste na tela de Runtime, onde não estava ocorrendo a exibição da lista de _pipelines_ implantados quando o número de licenças era excedido em uma nova implantação.

## Novidades 02/02/2021

Gostaríamos de compartilhar algumas melhorias e novidad

### CÁPSULAS DIGIBEE <a href="#h_387f0b288c" id="h_387f0b288c"></a>

Lançamos as Cápsulas Digibee! Cápsulas são componentes reutilizáveis que podem ser criados por qualquer usuário da Plataforma, usando o mesmo modelo de desenvolvimento visual concebido na criação do _pipeline_.

Uma Cápsula permite que a integração de fluxos seja publicada na paleta de componentes para ser utilizada em outro momento, de maneira simplificada e ainda mais rápida.

Clique [aqui](https://digibee.com/pt-br/digibee-capsulas/) para saber mais detalhes sobre as Cápsulas na nossa página.

Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4854330-guia-inicial-para-o-uso-das-capsulas) para acessar o nosso Guia inicial para o uso de Cápsulas.

​

![](../.gitbook/assets/fev\_01.jpg)

​

### COMPONENTES <a href="#h_794dd852fb" id="h_794dd852fb"></a>

#### Parallel Execution <a href="#h_ed981a4f3e" id="h_ed981a4f3e"></a>

Adicionamos ao componente as seguintes capacidades:

* definição do resultado das linhas de execuções (por exemplo, uma saída resumida do total de execuções ou o detalhamento de todas as execuções);
* exibição dos resultados com base no nome das linhas de execução;
* ocultação opcional dos erros.

​

![](../.gitbook/assets/fev\_02.jpg)

​

Para ler o artigo atualizado sobre o _Parallel Execution_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4767439-parallel-execution).

#### Google Drive <a href="#h_757122bb4a" id="h_757122bb4a"></a>

Adicionamos o campo “Mime Type” ao componente _Google Drive_, possibilitando que determinados arquivos sejam convertidos para algum tipo do Google Workspace no momento do _upload_. Para ler o artigo completo sobre esse componente, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3967132-google-drive).

#### Zip File <a href="#h_d58451f1b2" id="h_d58451f1b2"></a>

O componente _Zip File_ passou a descomprimir arquivos _zip_, além de comprimir vários arquivos em um único _zip_.

### FUNÇÕES <a href="#h_914fae15cb" id="h_914fae15cb"></a>

Adicionamos a função de utilidades TOBOOLEAN à Plataforma. Para saber mais sobre essa e outras funções, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4623447-double-braces-funcoes).

### MELHORIAS DE USABILIDADE <a href="#h_95a2505fa3" id="h_95a2505fa3"></a>

Estamos sempre buscando melhorar a sua experiência na Plataforma. Veja o que fizemos:

* adicionamos uma indicação de recebimento de mensagens no novo ícone de ajuda;

​

![](../.gitbook/assets/fev\_03.gif)

​

* inserimos a opção de buscar por todos os tipos de mensagens no filtro de busca nas telas de execuções concluídas e _logs_ de _pipelines_;

​

![](../.gitbook/assets/fev\_04.gif)

![](../.gitbook/assets/fev\_05.gif)

​​

​

* agora o formato de hora na tela de Runtime segue o padrão das demais telas da Plataforma (24h).

\
\
Nós também solucionamos alguns _bugs_:

* **Mensagem de erro no Canvas:** melhoramos a qualidade da mensagem de erro no _test-mode_ quando um teste era realizado no _pipeline_ fazendo referência a um _account_ ou _globals_ inexistente.
* **SAP:** eliminamos um erro que impedia o _test-mode_ de responder corretamente quando o administrador do SAP efetuava uma alteração na RFC. Para _pipelines_ implantados, continua sendo necessário fazer a reimplantação.

## Novidades 19/01/2021

Gostaríamos de compartilhar algumas melhorias e novidades:

### COMPONENTES <a href="#h_3e265d30d0" id="h_3e265d30d0"></a>

#### DB <a href="#h_32fafc4a22" id="h_32fafc4a22"></a>

O componente passou a suportar o Oracle Netsuite ERP. Esse novo banco de dados só permite consultas ao banco, não sendo possível realizar as operações de INSERT, UPDATE e DELETE. Para saber quais são os outros bancos de dados suportados pela Plataforma, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4520594-bancos-de-dados-suportados).

### SUPORTE <a href="#h_a9fe6d539e" id="h_a9fe6d539e"></a>

O menu de ajuda dentro do _pipeline canvas_ está mais completo. Além de um caminho para iniciar uma conversa com o nosso time de suporte, você também pode:

* acessar a central de ajuda e pesquisar o que quiser sobre a Plataforma;
* ver a lista das nossas novidades mais recentes, caso tenha perdido nossos comunicados;
* clicar no ícone para os atalhos do teclado, que antes ficava no topo da sua página.

​

![](../.gitbook/assets/jan\_01.png)

\
\
Nós também solucionamos um _bug_:

* **SAP:** quando era realizada uma chamada com um _payload_ inválido a uma RFC, uma inconsistência no componente SAP afetava o funcionamento das demais chamadas. Agora, mesmo que esse erro ocorra, o _pipeline_ continua funcionando normalmente para as chamadas corretas. Se você utiliza esse componente nos seus _pipelines_, faça a reimplantação para que a correção seja aplicada.

## Novidades 05/01/2021

Gostaríamos de compartilhar algumas melhorias e novidades:\\

### COMPONENTES <a href="#componentes" id="componentes"></a>

#### JSON Transformer <a href="#json-transformer" id="json-transformer"></a>

Criamos um novo componente para que você possa transformar os seus JSONs de maneira mais rápida, eficiente e sem código. Para saber mais sobre o _**JSON Transformer**_, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4766368-json-transformer).

#### Parallel Execution <a href="#parallel-execution" id="parallel-execution"></a>

Entregamos um novo componente que te permite criar fluxos de execução paralela. Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/4767439-parallel-execution) para ler o artigo.

### TRIGGERS <a href="#triggers" id="triggers"></a>

Adicionamos aos _triggers_ REST e HTTP um novo parâmetro que te permite definir o tamanho máximo do _payload_ enviado em uma requisição. Os valores de configuração são:

* 1MB
* 2MB
* 3MB
* 4MB
* 5MB

O valor limite atual utilizado em todos os _pipelines_ é de 5MB.

\
\
Nós também solucionamos um _bug_:

* **Multi-instance:** a Plataforma permitia erroneamente o cadastro de _fields_ com valores apenas numéricos, tornando-os inutilizáveis devido à falta de suporte para nomes compostos apenas por números. Por isso, foi criada uma regra para impedir a criação de _fields_ inválidos.

\\
