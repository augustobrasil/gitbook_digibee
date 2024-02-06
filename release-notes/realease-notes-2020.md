# Release notes 2020

## Novidades 22/12/2020

EEscrito por Erick Rubiales\
Atualizado há mais de uma semana

Gostaríamos de compartilhar algumas melhorias e novidades:\\

### COMPONENTES <a href="#componentes" id="componentes"></a>

#### Pipeline Executor <a href="#pipeline-executor" id="pipeline-executor"></a>

Construímos um novo componente que te permite efetuar invocações a outros _pipelines_. O _Pipeline Executor_ possibilita a invocação de qualquer outro _pipeline_, de forma síncrona ou assíncrona. Para ler o artigo do componente, clique [aqui](https://docs.digibee.com/documentation/release-notes/release-notes-2020#pipeline-executor).

#### DB <a href="#db" id="db"></a>

Homologamos o banco de dados _DB Informix_ para que você possa utilizá-lo quando estiver configurando as diferentes versões do componente DB.\\

#### REST V2 <a href="#rest-v2" id="rest-v2"></a>

* Adicionamos o “Http Status Message” no retorno das chamadas dos _endpoints_ no componente _REST V2_, caso essa informação esteja presente na resposta do _endpoint_.
* Passou a ser possível configurar o _REST V2_ com o _pool_ de conexões desabilitado - com isso, o componente lida melhor com alguns _endpoints_ que requerem novas conexões a cada chamada.
* Também se tornou possível configurar o _REST V2_ com invalidação de sessão SSL a cada requisição.

Leia o artigo completo do componente clicando [aqui](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2).

### FUNÇÕES <a href="#funes" id="funes"></a>

Criamos novas funções para otimizar a sua experiência com integrações na Plataforma. Veja quais são elas:

* ISOBJECT
* ISARRAY
* ISBOOLEAN
* ISNUMBER
* ISSTRING
* ISNULL
* SWITCHCASE

Para saber como utilizar essas novas funções condicionais, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais).

### INTERFACE GRÁFICA <a href="#interface-grfica" id="interface-grfica"></a>

Estamos sempre investindo na melhoria da experiência visual da Digibee Integration Platform.

Desta vez, criamos ícones e formas para facilitar a identificação dos componentes:

* Choice: terá formato único de losango;
* _Streamers_ (ou componentes com _subpipelines_): terão formato de pentágono.

Os ícones dos demais componentes mantiveram os seus formatos.

![](../.gitbook/assets/dez\_01.png)

### TELA DE CONFIGURAÇÃO DE CONTAS <a href="#tela-de-configurao-de-contas" id="tela-de-configurao-de-contas"></a>

Agora ocultamos dados de campos sensíveis na tela de configuração de contas (_accounts_) durante a digitação.\\

### DASHBOARD <a href="#dashboard" id="dashboard"></a>

Modificamos o comportamento do filtro de buscas quando datas são utilizadas. Veja o exemplo:

**Data de início:** 21/12/2020 15:47

**Data de fim:** 21/12/2020 15:52\\

Como a busca será efetuada:

**Data de início:** 21/12/2020 15:47:**00.000**

**Data de fim:** 21/12/2020 15:52:**59.999**

![](<../.gitbook/assets/dez\_02 (1).png>)

Nós também solucionamos alguns _bugs_:

* **CSV to JSON V2:** eliminamos uma falha que, em algumas situações, ignorava o delimitador durante a conversão de CSV para JSON por meio do componente _CSV to JSON V2_.
* **Triggers HTTP:** corrigimos um _bug_ que impedia a realização de _requests_ de _pipelines_ multi-instância caso fossem selecionados _triggers_ HTTP (REST, HTTP ou HTTP File).
* **Choice:** solucionamos o problema que permitia configurar o nome de uma linha do componente _**Choice**_ com os seguintes caracteres inválidos: **&**, **?** e **/**
* **Runtime:** resolvemos o _bug_ que não removia a infraestrutura implantada de _pipelines_ com nome muito grande durante o _redeploy_.

## Novidades 08/12/2020

Gostaríamos de compartilhar algumas melhorias e novidades:\\

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **Stream File Reader Pattern:** o novo componente foi criado para a leitura _stream_ de arquivos com base em padrões de início e fim, como por exemplo XMLs, logs, busca de _tags_ específicas, multilinhas e blocos REGEX, possibilitando a leitura de estruturas complexas. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-file-reader-pattern) para ler o artigo.
* **JSON to CSV V2:** a versão repaginada do _JSON to CSV_, além de transformar um JSON em CSV, também suporta _Double Braces_. Para ler o artigo sobre o componente, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-to-csv-v2).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

Os _triggers_ REST e HTTP não exigem mais “content-type” para o método GET.

#### RUNTIME <a href="#runtime" id="runtime"></a>

Evoluímos o nosso processo de reimplantação e alteração de versão para garantir que o _pipeline_ anterior fique ativo até que o novo _pipeline_ esteja disponível para substituí-lo.

Criamos a possibilidade de verificar no cartão da implantação se um _pipeline_ está sendo reiniciado por erro (_Errors_) ou por estouro de memória (_Out of Memory_).\
\
**Importante:** reimplante o seu _pipeline_ para ativar essa funcionalidade.

![](../.gitbook/assets/dez\_03.png)

#### TELA DE DASHBOARD <a href="#tela-de-dashboard" id="tela-de-dashboard"></a>

Para melhorar ainda mais a sua experiência com execuções na Plataforma, fizemos algumas atualizações na tela de _dashboards_:

* a aba conhecida por LOGS foi renomeada para EXECUÇÕES CONCLUÍDAS e também melhorada para tornar a busca por execuções mais simplificada;
* uma nova seção permite que você encontre _pipeline logs_ com muito mais facilidade, veja os seus detalhes e consulte as execuções de origem;
* essa nova seção permite que você verifique _logs_ internos do _pipeline_ não relacionados a execuções (inicialização de _pipeline_, erros de configuração de componentes), que antes não eram acessíveis por meio da Plataforma;
* se tornou possível buscar informações em _logs_ internos do _pipeline_, como por exemplo _logs_ emitidos pelo componente [_Log_](https://intercom.help/godigibee/pt-BR/articles/2950096-log);
* quando você utiliza o filtro “log message”, os resultados de buscas em _logs_ internos do _pipeline_ aparecem realçados (_highlighted_);
* o sistema de busca otimizado inclui a exibição pela chave do _pipeline_ e botões de ação mais evidentes e acessíveis na visualização das listas.

#### PIPELINE CANVAS <a href="#pipeline-canvas" id="pipeline-canvas"></a>

Melhoramos a aparência do Canvas do Pipeline para você ter uma experiência visual mais limpa e agradável.

![](../.gitbook/assets/dez\_04.png)

Nós também solucionamos alguns _bugs_:

* **REST, HTTP e HTTP File Trigger:** ajustamos a falha que gerava _deploy_ falho quando os métodos eram escritos com letras minúsculas ou eram inválidos. Agora você pode configurar esses _triggers_ tanto com letra maiúscula quanto com minúscula.
* **HTTP File Trigger / HTTP Trigger:** solucionamos o problema que impedia a criação do _response header Authorization_ quando o _HTTP File Trigger_ ou o _HTTP Trigger_ era utilizado em um _pipeline_ que gera um _token_ JWT.
* **Pipeline Engine:** corrigimos um _bug_ que impedia o uso de _tokens_ JWT em _pipelines_ configurados com _HTTP File_ ou _HTTP Trigger_.
* **DB V2 / Stream DB V3:** ajustamos a falha que retornava, para alguns bancos de dados, o nome original da coluna ao invés do nome que era configurado no _alias_ em _select_. Além disso, criamos a propriedade “Output Column From Label” para controlar esse comportamento.
* **Mongo DB / Object Store:** solucionamos o problema que impedia, em alguns casos, o retorno correto dos atributos do tipo “objectId” fora do nível raiz nos componentes _Mongo DB_ e _Object Store_.

## Novidades 24/11/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **DB V2:** o componente DB V2 passou a suportar o novo banco de dados Firebird. Para rever o artigo, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2).
* **Email V2:** repaginamos o componente de envio de e-mail, que em sua nova versão suporta _Double Braces_ e anexos. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/email-v2) para ler o artigo.

#### TELA DE LOGS <a href="#tela-de-logs" id="tela-de-logs"></a>

* **Campo \_payload**\_**:** criamos um novo artigo que explica o funcionamento do campo _payload_ na tela de busca de _logs_ da Plataforma.
* _**Payloads**_\*\* truncados:\*\* passamos a exibir alertas que informam a ausência do _payload_ completo dependendo do seu tamanho. Anteriormente, o _payload_ era identificado com a propriedade _@@DGB\_TRUNCATED@@_.

#### CADASTRO E EDIÇÃO DE USUÁRIOS <a href="#cadastro-e-edio-de-usurios" id="cadastro-e-edio-de-usurios"></a>

Adicionamos suporte a permissões específicas por ambientes. Por exemplo: DEPLOYMENT:CREATE{ENV:TEST} para acesso exclusivo ao ambiente TEST e DEPLOYMENT:CREATE{ENV:PROD} para acesso exclusivo ao ambiente PROD. A permissão DEPLOYMENT:CREATE continua válida e dá acesso a ambos os ambientes.

#### FUNÇÕES <a href="#funes" id="funes"></a>

Para melhorar a sua experiência com as Funções da Plataforma, agrupamos os artigos sobre o tema em categorias:

* de comparação
* numéricas
* condicionais
* de data
* de arquivo
* de JSON
* matemáticas
* de _string_
* de utilidades

Entenda a nova divisão clicando clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais).

Nós também solucionamos alguns _bugs_:

* **Exibições em \_logs**_\*\* e nos \*\*_**payloads**\_\*\* de re-execuções:\*\* corrigimos um defeito que fazia a truncagem incorreta de números com muitos algarismos e alguns números com alta precisão.
* **SFTP:** corrigimos um _bug_ que causava duplicidade de registros na operação de listagem de diretórios do componente SFTP.
* **Object Store:** corrigimos o problema que, em algumas situações, não criava o índice mesmo que o \_**Object Store** \_ fosse definido como _unique_. A partir de agora, caso o _pipeline_ não consiga criar o índice após 3 tentativas, não será feita a sua inicialização.

## Novidades 10/11/2020

Gostaríamos de compartilhar algumas melhorias e novidades:\\

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* S**FTP:** novos atributos são retornados quando uma listagem no diretório do componente SFTP é feita, contendo informações dos arquivos e diretórios. Para ler o artigo completo sobre o SFTP, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/sftp).

#### FUNÇÕES <a href="#funes" id="funes"></a>

A função XOR aceita múltiplos parâmetros.

Nós também solucionamos alguns _bugs_:

* **File Reader:** corrigimos o _bug_ que não considerava a configuração da propriedade “Maximum File Size”. Para garantir a retrocompatibilidade, adicionamos uma nova propriedade chamada “Check File Size”, que valida se o componente _File Reader_ deve ou não verificar o tamanho do arquivo antes que ele seja lido.
* **Componentes inválidos:** adicionamos um processo de verificação que impede que componentes inválidos ou inexistentes em um determinado _Realm_ sejam adicionados ao _Canvas_.
* **Upgrade na nova versão principal:** corrigimos o problema que invalidava as _Libraries_ no seu _pipeline_ após a realização do Upgrade na nova versão principal do _pipeline_.
* **Exibição de números grandes e fracionados:** corrigimos um defeito que fazia a truncagem incorreta de números com muitos algarismos e alguns números com alta precisão em execuções TEST MODE.
* **Tratamento de erros:** conforme anunciado em comunicado prévio, resolvemos a questão que estava causando mudança de comportamento no tratamento de erros de componentes que possuem _subpipeline_ e, com isso, não há mais quebra de compatibilidade em _pipelines_ já implementados.

## Novidades 27/10/2020

Gostaríamos de compartilhar algumas melhorias e novidades:\\

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **Throw Error:** entregamos um componente que permite o lançamento de erros em pontos desejados de um _pipeline_ em execução, o que te dá mais controle sobre os cenários de erro/exceção. Para conhecer o _Throw Error_, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/tools/throw-error).
* **Block Execution:** desenvolvemos um componente que te permite agrupar trechos do _pipeline_ dentro de um bloco para obter mais organização e conseguir tratar melhor os erros. Para ler sobre o _Block Execution_, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/block-execution).
* **Do-While:** atualizamos a documentação sobre esse componente para que você entenda melhor o tratamento de erros. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/do-while) para ler o artigo do Do-While.
* **Retry:** atualizamos a documentação sobre esse componente para que você entenda melhor o tratamento de erros. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/retry) para ler o artigo do Retry.
* **REST:** ouvimos o seu _feedback_ e percebemos que a ocultação dos _logs_ nas chamadas do componente REST causou diminuição de visibilidade. Por esse motivo, revertemos essa ação para não te impactar negativamente.

#### DESIGN <a href="#design" id="design"></a>

* **Imagens:** adotamos formato vetorial para os ícones dos componentes do _pipeline Canvas_. Com isso, além das imagens terem mais qualidade, o tempo de carregamento diminui.
* **Melhorias visuais:** para melhorar a sua experiência, refinamos a tela de _login_ da Plataforma, ajustamos a falha que permitia o fechamento indevido do _sidesheet_ e realizamos outros ajustes na consistência da interface.

#### DOCUMENTAÇÃO <a href="#documentao" id="documentao"></a>

Estamos revisando a nossa documentação para que você tenha acesso a leituras completas e atualizadas. Te convidamos a rever os seguintes artigos:

* [JSON to XML](https://docs.digibee.com/documentation/v/pt-br/components/tools/xml-to-json-transformer)
* [FTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/ftp)
* [SFTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/sftp)
* [Stream DB V3](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stream-db-v3)
* [Event Publisher](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/event-publisher)
* [Event Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/event-trigger)
* [S3 Storage](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/s3-storage)
* [Hash](https://docs.digibee.com/documentation/v/pt-br/components/security-components/hash)
* [Template Transformer](https://docs.digibee.com/documentation/v/pt-br/components/tools/template-transformer)

\\

Nós também solucionamos um _bug_:

* **Retry:** corrigimos o erro que surgia em fluxos bem sucedidos, quando o componente Retry era configurado com 1 tentativa e tinha a opção “failOnError” habilitada. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/retry) para acessar o artigo revisado desse componente.

## Novidades 14/10/2020

EEscrito por Erick Rubiales\
Atualizado há mais de uma semana

Gostaríamos de compartilhar algumas melhorias e novidades:\\

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **REST Connector:** os campos sensíveis são respeitados no componente, impedindo a exposição indevida de informações.
* **MongoDB Connector:** você pode realizar uma agregação nesse componente utilizando as operações “$merge” e “$out”.
* **CSV to JSON V2:** a nova versão do componente suporta _Double Braces_. Para saber mais sobre o CSV to JSON V2, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/tools/csv-to-json-v2).

#### FUNÇÕES <a href="#funes" id="funes"></a>

Fizemos ajustes em algumas funções:

* **JOIN:** aceita receber um _array_ de _strings_
* **AND e OR:** aceitam múltiplos parâmetros
* **TOINT, TODOUBLE e TOFLOAT:** não retornam erro ao receber o parâmetro _null_

Além disso, criamos novas funções para otimizar a sua experiência com integrações na Plataforma. Veja quais são elas:

* UNESCAPE
* JSONPATH
* TOJSON
* SUMDATE
* SIZE
* LASTINDEXOF
* INDEXOF

#### BANCOS DE DADOS <a href="#bancos-de-dados" id="bancos-de-dados"></a>

Listamos todos os Bancos de Dados e as respectivas versões com as quais você pode trabalhar. Para conhecer o que a Plataforma suporta, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/plataforma/bancos-de-dados-suportados).

Nós também solucionamos alguns _bugs_:

* **REST V2 / SOAP V2:** ambos os componentes REST Connector V2 e SOAP Connector V2 passaram a respeitar o _charset_ de resposta do _endpoint_.
* **Headers e Query Parameters:** suportam nomes contendo pontos (.)
* **WGet Connector:** a utilização de _Double Braces_ está habilitada dentro dos campos de HEADER e QUERY PARAMETER sem que ocorram erros indevidos.
* **Versões minor:** _pipelines_ arquivados não são mais mostrados indevidamente na tela de _deployment_.
* **Input number:** agora o componente do tipo “input number” está com fonte e altura corretas.
* **Scroll:** a barra de _scroll_ já está disponível na tela de configuração de _pipelines_.
* **Resolução de tela:** a resolução mínima foi ajustada para 1280 x 720 px nos [requisitos mínimos de sistema](https://docs.digibee.com/documentation/v/pt-br/plataforma/requisitos-de-sistema) da Digibee Integration Platform.
* **Log:** corrigimos a falha que deixava a tela branca quando a sequência _log - detalhes - mensagens_ era clicada.
* **Re-execução de pipeline:** corrigimos o problema que impedia a re-execução do _pipeline_ a partir do _log_.

## Novidades 29/09/2020

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **Apresentação:** os componentes são listados a partir de nomes mais amigáveis.

#### OAUTH <a href="#oauth" id="oauth"></a>

* **Google:** o provedor de Google foi atualizado para permitir que a mesma conta Google seja utilizada em diferentes _accounts_ com escopos idênticos sem que ocorra expiração indevida. Para usufruir dessa novidade, atualize sua _account_.

#### INTERFACE GRÁFICA <a href="#interface-grfica" id="interface-grfica"></a>

Estamos sempre investindo na melhoria da experiência visual da Digibee Integration Platform.

Desta vez, você vai ver as alterações nas telas de:

\
**PERFIL**

* Gestão de Duplo Fator
* Alteração de senha

\
**CONFIGURAÇÕES**

* API Keys
* Globais
* Contas
* Relacionamento
* Multi-instância

\
**DASHBOARDS**

* Visão geral
* _Logs_

\
Com isso, a experiência em todas as telas está renovada.\\

Nós também solucionamos alguns _bugs_:

* **Forgot password:** fizemos ajustes nas indicações de erro para que você saiba quando o _link_ da função "Esqueci minha senha" expirou.
* **Configuração de componentes:** corrigimos um problema que fazia aparecer as configurações do componente incorreto em algumas situações não usuais.
* **Execução de \_pipeline**\_**:** eliminamos o erro de Zip File Closed que ocorria após a implantação de _pipelines_, nas primeiras execuções.

## Novidades 15/09/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **Kafka Connector:** o Kafka Connector agora possui suporte à autenticação Kerberos. Para ler o artigo sobre o componente, clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3576368-kafka-connector).
* **DB Connectors:** a Plataforma permite o uso do banco de dados Postgres para operações em _batch mode_.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka Trigger:** o Kafka Trigger também suporta autenticação Kerberos. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/triggers/kafka-trigger) para ler o artigo a respeito.

#### PIPELINES <a href="#pipelines" id="pipelines"></a>

Foram feitas melhorias que reduziram o tempo de salvamento de _pipelines_ muito grandes.

#### SEGURANÇA <a href="#segurana" id="segurana"></a>

Adicionamos a possibilidade de restaurar permissões removidas de usuários.

#### INTERFACE GRÁFICA <a href="#interface-grfica" id="interface-grfica"></a>

Estamos sempre investindo na melhoria da experiência visual da Digibee Integration Platform.

Desta vez, você vai ver as alterações:

* na tela de gestão de usuários
* na tela de auditoria
* nos ícones dos _triggers_

## Atualizações de Segurança Digibee

Setembro/2020, 2ª edição\\

#### Tudo o que você precisa saber sobre os nossos avanços na Segurança <a href="#tudo-o-que-voc-precisa-saber-sobre-os-nossos-avanos-na-segurana" id="tudo-o-que-voc-precisa-saber-sobre-os-nossos-avanos-na-segurana"></a>

#### O QUE EU PRECISO SABER? <a href="#o-que-eu-preciso-saber" id="o-que-eu-preciso-saber"></a>

Seguindo as melhores práticas de mercado, atualizamos os nossos certificados de criptografia de _endpoints_ HTTPS a cada 3 meses. Logo, a próxima atualização está prevista para 21/09/2020 às 22:00 (horário de Brasília).\
\\

#### O QUE SERÁ ALTERADO <a href="#o-que-ser-alterado" id="o-que-ser-alterado"></a>

Com a atualização de certificados de criptografia, os seguintes _endpoints_ serão renovados:

* api.godigibee.io
* test.godigibee.io
* core.godigibee.io
* [www.godigibee.io](http://www.godigibee.io/)

A disponibilidade desses _endpoints_ não será afetada durante o processo de atualização.

#### EU TENHO QUE FAZER ALGUMA COISA? <a href="#eu-tenho-que-fazer-alguma-coisa" id="eu-tenho-que-fazer-alguma-coisa"></a>

Se os sistemas que acessam os _endpoints_ da Digibee…\\

* **tiverem o certificado da Digibee manualmente importado**

então os certificados deverão passar pela atualização. Recomendamos que os certificados raiz sejam importados no lugar do certificado da Digibee para que o processo seja transparente.\\

* **tiverem o certificado raiz manualmente importado**

então você não precisa fazer nada, pois o processo de atualização já está pronto para ser completamente transparente.\\

* **utilizarem certificadoras globais**

então você não precisa fazer nada, pois o processo de atualização já está pronto para ser completamente transparente.

## Atualizações de Segurança Digibee

Setembro/2020

#### Tudo o que você precisa saber sobre os nossos avanços na Segurança <a href="#tudo-o-que-voc-precisa-saber-sobre-os-nossos-avanos-na-segurana" id="tudo-o-que-voc-precisa-saber-sobre-os-nossos-avanos-na-segurana"></a>

A Digibee executa testes de penetração de segurança regularmente e incluímos na nossa demanda a realização de _**Pentests**_ a cada 6 meses. Durante esses testes, nós podemos encontrar questões que precisem da nossa atenção e que podem nos levar a fazer mudanças ou ajustes no produto para beneficiar você, usuário.

Se quiser saber mais sobre os últimos testes que realizamos, é só acompanhar os detalhes abaixo.\
\\

#### O QUE EU PRECISO SABER? <a href="#o-que-eu-preciso-saber" id="o-que-eu-preciso-saber"></a>

* **TLS:** adicionamos uma camada de segurança nos serviços da Plataforma para aceitar somente a utilização do TLS 1.2 ou superior. Com isso, o protocolo TLS nas versões 1.0 e 1.1, além das cifras com segurança fraca, não será mais aceito nas tentativas de conexão. Essa mudança impactou o acesso ao [Portal da Digibee](http://www.godigibee.io/) e ao _endpoint_ de [Core APIs](http://core.godigibee.io/).
* **Recaptcha:** atualmente utilizamos o RECAPTCHA V3 na nossa Plataforma. A principal política dessa versão é não interferir na sua utilização como usuário, ou seja, você não será mais perguntado se é um robô. Sendo assim, implementamos uma técnica que bloqueia acessos identificados como suspeitos - na primeira tentativa, o acesso será bloqueado por 60 segundos; e cada nova tentativa de _login_ terá o seu tempo dobrado.
* **Sessão Local:** adotamos mecanismos ainda mais seguros para o armazenamento de dados gerenciados pela Plataforma no seu _browser_.

#### EU TENHO QUE FAZER ALGUMA COISA? <a href="#eu-tenho-que-fazer-alguma-coisa" id="eu-tenho-que-fazer-alguma-coisa"></a>

Por enquanto, apenas recomendamos que você faça um _upgrade_ no seu _browser_ caso ele não suporte o TLS 1.2+, já que os nossos _endpoints_ rejeitam conexões que utilizam versões descontinuadas do TLS.

## Novidades 01/09/2020

Gostaríamos de compartilhar algumas melhorias e novidades:\\

#### COMPONENTES <a href="#componentes" id="componentes"></a>

* **REST Connector V2:** você pode fazer o _download_ de arquivos através das chamadas do REST Connector V2, também podendo transformá-los imediatamente para base64, formato binário ou leitura _raw_ do conteúdo. Além disso, agora o componente permite que o uso do protocolo HTTP 1.1 seja forçado durante a chamada. Para ler o artigo sobre o REST Connector V2, é só clicar [aqui](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Email Trigger V2:** criamos uma nova versão do _trigger_ que, além de melhorar as funcionalidades da sua versão anterior, agora suporta o recebimento de anexos. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/triggers/email-trigger-v2) para ler o artigo sobre o Email Trigger V2.

#### DESIGN <a href="#design" id="design"></a>

* **Imagens:** colocamos as ilustrações e os ícones da Plataforma em um formato vetorial. Com isso, além das imagens terem mais qualidade, o tempo de carregamento diminui.

#### INTERFACE GRÁFICA <a href="#interface-grfica" id="interface-grfica"></a>

Estamos sempre investindo na melhoria da experiência visual da Digibee Integration Platform.

Desta vez, você vai ver as alterações em:

* tela de listagem de _pipelines_
* histórico de versões
* tela de Runtime

## Novidades 18/08/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **DB Connector V2:** a nova funcionalidade _rollback_ é suportada em _batch mode_ e se aplica quando ocorre pelo menos um erro na execução. Além disso, a lista de erros é exibida caso haja alguma falha durante a execução em _batch_. Para entender melhor como essa nova funcionalidade pode te ajudar na utilização do componente, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2) para ler o nosso artigo.
* **REST Connector V2:** adicionamos suporte a contas do tipo AWS-4 para que você possa autenticar no serviço AWS, assim como Lambda e DynamoDB, que deseja utilizar através das chamadas do REST Connector V2. Para conhecê-lo melhor, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2).

\
Nós também solucionamos alguns _bugs_:

* **DB Connector V2:** ajustamos a exibição do _status_ da execução do _batch mode_ quando ocorrem falhas na utilização do banco de dados Oracle. Também ajustamos uma falha na tela de configurações desse componente, que excluía o item incorreto na sessão “Type Properties”.
* **Pipelines:** corrigimos o problema que impedia salvar uma nova versão do _pipeline_, criada a partir de outra que estava arquivada.

## Novidades 04/08/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **RabbitMQ Trigger:** criamos um novo _trigger_ que recebe mensagens a partir de um _broker_ RabbitMQ. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rabbitmq-trigger) para acessar o artigo.

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **S3 Storage Connector:** agora o componente suporta paginação na operação de listagem, além de mover arquivos entre diretórios remotos.
* **GZip Connector V2:** a nova versão do componente, que suporta Double Braces, comprime e descomprime arquivos, assim como dados do seu _pipeline_. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/files/gzip-v2) para acessar o artigo sobre o GZip Connector V2.

#### FUNÇÕES <a href="#funes" id="funes"></a>

Adicionamos funções inéditas à Plataforma para te dar mais agilidade no processo de integração, não sendo mais necessário recorrer a soluções complexas. Veja quais são as funções novas disponíveis:

* TOSTRING
* SUBSTRING
* BASEDECODE
* BASEENCODE
* SPLIT
* JOIN
* TOINT
* TOLONG
* TODOUBLE
* LEFTPAD
* CAPITALIZE
* NORMALIZE
* RIGHTPAD

\
Para entendê-las melhor e saber como utilizá-las, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais) para acessar o nosso artigo.

#### DESIGN <a href="#design" id="design"></a>

* **Identidade visual:** o site já está com o nosso novo logo, assim como as novas fontes e cores - tornamos a Plataforma visualmente mais elegante, sem afetar nenhuma funcionalidade.

#### OAUTH <a href="#oauth" id="oauth"></a>

Agora a nossa Plataforma permite que o tipo de conta OAuth2 também seja utilizado com o provedor Mercado Livre.

\
Nós também solucionamos alguns _bugs_:

* **Chat:** fizemos ajustes para que as notificações de mensagens do _chat_ fiquem sobre a interface na tela de criação de _pipelines_.
* **JMS Connector:** corrigimos a falha que encerrava o _pool_ de conexões desse componente e impedia o envio de novas mensagens.

## Novidades 21/07/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **HTML To PDF Connector:** o componente permite a criação de arquivos em PDF, com imagens e diagramações a partir de um HTML. Para conhecê-lo melhor, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/tools/html-to-pdf) e leia o nosso artigo.
* **Assert V2 Connector:** a nova versão do componente permite que você configure as condições de validação através de Double Braces, assim como as mensagens internas e a interrupção de fluxos mediante a ocorrência de erros. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/tools/assert-v2) para saber mais.
* **FTP/SFTP Connector:** adicionamos a esses componentes a função _MOVE_, que move um arquivo de um diretório remoto para outro.

#### DADOS SENSÍVEIS <a href="#dados-sensveis" id="dados-sensveis"></a>

Adicionamos a capacidade de definir dados sensíveis (_sensitive fields_) em nível de Realm, garantindo governança global. Para fazer essa solicitação, entre em contato conosco através do _chat_.

\
Nós também solucionamos alguns _bugs_:

* **SFTP Connector:** corrigimos a falha que ignorava o _Remote File Name_ durante a operação _upload_.
* **Zip File Connector:** o componente deixou de expor o caminho completo (_full file path_) do arquivo quando um erro acontece.
* **Mudança de senha:** atualizamos a mensagem de erro quando a nova senha de usuário é alterada para uma versão já utilizada.
* **Multi instance:** arrumamos o erro que impedia a reimplantação de um _pipeline multi instance_.
* **Gestão de usuários:** adicionamos uma validação que impede o cadastro de usuários já existentes.
* **CSV To Excel Connector:** a propriedade _Fail On Error_ deixou de ser ignorada durante o uso desse componente.
* **One Drive Connector:** eliminamos o erro que ocorria na listagem da raiz e na utilização de nomes com espaço.

## Novidades 07/07/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **REST Connector V2:** inserimos ao conector a capacidade de enviar arquivo no corpo da requisição (_request body_).
* **CMS Connector:** quando a opção ENCAPSULATED é ativada, o conteúdo dos campos especificados (opção SIGN FIELDS) ou do _payload_ (opção SIGN PAYLOAD) é incluído na mensagem assinada.
* **RabbitMQ Connector:** desenvolvemos um novo componente para que você possa publicar mensagens em uma fila RabbitMQ. Para conhecer melhor o componente, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/rabbitmq) e leia o nosso artigo.
* **OneDrive Connector:** atualizamos o conector com a última versão o SDK da Microsoft e incluímos novas funcionalidades, como LIST, SEARCH, paginação, entre outros.

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

Desenvolvemos 2 novas funções com _Double Braces_ para que você possa confirmar a existência de um arquivo (FILEEXISTS) e o tamanho de um arquivo (FILESIZE). Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais) para ler o nosso artigo e entender melhor essas funções. (#7630)

#### OAUTH MICROSOFT <a href="#oauth-microsoft" id="oauth-microsoft"></a>

Atualizamos o fluxo de autenticação OAuth (oauth-2) da Microsoft para a última versão.

#### PROVEDOR DE IDENTIDADE INTEGRADO <a href="#provedor-de-identidade-integrado" id="provedor-de-identidade-integrado"></a>

Disponibilizamos a autenticação integrada, que te permite centralizar o controle de acesso, além de incluir e excluir colaboradores da nossa Plataforma no seu provedor de identidade. Se você deseja ativar essa solução, entre em contato com a gente via _chat_.

Nós também solucionamos alguns _bugs_:

* **Stream DB Connector V3 / DB Connector V2:** valores de parâmetros agora são substituídos de acordo com a ordem apresentada em _Double Braces_.
* **Mongo DB Connector:** os valores gerados pelo construtor de objetos _ObjectId_ passaram a ser exibidos da maneira correta quando aplicados em atributos diferentes de “\_id”.
* **Double Braces:** corrigimos um erro de interpretação de _Double Braces_ que ocorria durante a avaliação de múltiplas expressões em uma única propriedade (em particular, ao utilizar múltiplas vezes a função UUID).
* **Status de usuário:** agora o usuário recém-criado recebe o status “Redefinir senha”.
* **REST Connector V2:** adicionamos a funcionalidade que te permite especificar _Double Braces_ com escopo do tipo _account_ dentro do parâmetro FORM-DATA quando você utiliza o REST Connector V2 com o _content type_:application/x-www-form-urlencoded.

## Novidades 22/06/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **CMS Connector:** o novo componente permite que você assine \_payload\_s e campos, além de verificar assinaturas no padrão de criptografia CMS. Você pode clicar [aqui](https://en.wikipedia.org/wiki/Cryptographic\_Message\_Syntax) para entender o conceito de _Cryptographic Message Syntax_. E para saber mais sobre o conector, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/security-components/cms) e leia o nosso artigo.

#### ACCOUNTS <a href="#accounts" id="accounts"></a>

* **Kerberos:** criamos um novo tipo de _account_ para que você possa configurar o _principal_ e a _keytab_.

\\

#### KERBEROS <a href="#kerberos" id="kerberos"></a>

As versões mais recentes de todos os conectores de banco de dados suportam a autenticação do tipo Kerberos. Se você quiser utilizar esse tipo de autenticação, entre em contato com o nosso suporte.

\\

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

* **Accounts:** agora você pode informar mais de uma conta no REST Connector V2 e no Soap Connector V2, o que traz mais flexibilidade e segurança na permissão de uso das credenciais através de expressões _Double Braces_. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais) para ler o nosso artigo sobre o tema.\\

#### GERENCIAMENTO DE USUÁRIOS <a href="#gerenciamento-de-usurios" id="gerenciamento-de-usurios"></a>

Melhorias na Plataforma permitem que você possa reativar usuários removidos. Além disso, o _login_ pode ser integrado com o seu próprio Provedor de Identidade (AD) através de SAML V2, ampliando a capacidade de gestão da Plataforma.

## Novidades 09/06/2020

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **DB Connector V2:** aperfeiçoamentos no conector permitem que você realize transações em lote por meio do _batch mode_. Para ler o nosso artigo atualizado sobre o DB Connector V2, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2).

#### GERENCIAMENTO DE USUÁRIOS <a href="#gerenciamento-de-usurios" id="gerenciamento-de-usurios"></a>

Realizamos atualizações para que você possa adicionar novos dados relacionados aos usuários cadastrados, incluindo nome e _timezone_. Além disso, adicionamos uma camada de segurança no _token_ para reduzir o tempo de expiração para apenas 30 dias.

\
Nós também solucionamos alguns _bugs_:

* **Soap Connector V2:** ampliamos a capacidade do conector para que você possa utilizar _accounts_ com uma cadeia de certificados.
* **Google Drive Connector:** corrigimos a falha que não permitia a remoção de arquivos quando a função DELETE era selecionada.
* **JMS Trigger:** agora os consumidores são devolvidos ao _pool_ quando é detectada uma perda de conexão com o _broker_.
* **Login:** corrigimos a apresentação de mensagens que orientam sobre o preenchimento da senha.
* **Gerenciamento de Usuários:** o _status_ do usuário não fica mais oculto e os processos “Primeiro Acesso” e “Esqueceu a sua senha?” estão livres de erros.

## Novidades 26/05/2020

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **CSV To Excel:** uma nova funcionalidade nesse conector permite que você adicione múltiplas planilhas dentro de um arquivo em Excel novo ou pré-existente. Deseja saber mais sobre o CSV To Excel? Clique [aqui](https://intercom.help/godigibee/pt-BR/articles/3543950-csv-to-excel-connector) para acessar o nosso artigo.
* **REST Connector V2:** um novo suporte adicionado à esse conector permite que chamadas aos serviços de API do Google, assim como _Translate_, _Vision_, _Machine Learning_, entre outros, sejam efetuadas com a utilização de uma chave de conta de serviço do seu projeto Google Cloud cadastrada como uma _account_ (conta) Digibee. Para saber mais sobre Google Service Account, clique [aqui](https://cloud.google.com/iam/docs/service-accounts).

​\
Nós também solucionamos um _bug_:

* **Choice:** resolvemos a falha na validação de _labels_ (nomes) que considerava indevidamente uma repetição de caminhos no Choice.

\
_**⚠ Pipelines existentes que utilizam CSV To Excel**_

_O recebimento do nome do arquivo em Excel foi modificado (propriedade: EXCEL FILE NAME) e isso impacta a saída da propriedade fileName do conector. Por favor, altere o parâmetro para passar o nome completo do arquivo em Excel com a extensão fileName.xlsx antes de reimplantar o pipeline._\\

## Novidades 12/05/2020

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **Object Store:** ao utilizar as operações _Update by object ID_ ou _Update by query_ é possível saber se houve um registro afetado quando a opção for _Upsert_.
* **Hive JDBC:** os conectores de Banco de Dados suportam execuções Apache Hive JDBC.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka:** uma nova configuração no Kafka Trigger permite o processamento de mensagens uma a uma com confirmação de recepção após o retorno bem-sucedido do _pipeline_.

#### RUNTIME <a href="#runtime" id="runtime"></a>

Em _pipelines_ implantados é possível obter informações mais completas dos _endpoints_ configurados.

## Novidades 28/04/2020

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **Google Drive:** pode ser configurado para listar, fazer _upload_ e _download_, remover e mover objetos do Google Drive para o _pipeline_ e vice-versa. Para ler o artigo sobre esse conector, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/google-drive).

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **Kafka:** permite a realização de subscrições para o disparo do _pipeline_. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/triggers/kafka-trigger) e conheça melhor esse novo _trigger_.
* **Allow Redelivery:** essa configuração avançada pode ser aplicada a qualquer _trigger_ para que seja determinado se o _pipeline_ deve reprocessar mensagens descartadas ou perdidas.

#### DOUBLE BRACES <a href="#double-braces" id="double-braces"></a>

É possível acessar detalhes particulares (metadata.execution.key, metadata.execution.timeout, metadata.execution.startTimestamp e metadata.execution.redelivery) da execução de _pipelines_ através do contexto metadata de Double Braces.

#### PIPELINE ENGINE <a href="#pipeline-engine" id="pipeline-engine"></a>

Aprimoramos alguns mecanismos do motor de execução dos _pipelines_:

* **Processamento de mensagens:** o tempo de expiração das mensagens não é mais afetado, já que o Pipeline Engine não realiza a remoção prematura das mensagens para processamento. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine) e entenda mais lendo o nosso artigo.
* **Tempo de início do \_pipeline**\_**:** a infraestrutura aguarda a disponibilidade do Pipeline Engine antes de habilitar os acessos de _triggers_ para ele.
* _**Crashes**_\*\* do **\_**pipeline\*\*\_\*\*:\*\* o _pipeline_ é reiniciado automaticamente quando ocorre falta de memória (OOM).

#### RUNTIME <a href="#runtime" id="runtime"></a>

É atribuído o status STARTING na tela do Runtime aos pipelines com implantação em andamento. Quando a implantação é concluída, os status ACTIVE ou ACTIVE BUT DEGRADED indicam que os _pipelines_ estão disponíveis.

#### DESIGN <a href="#design" id="design"></a>

A aplicação da paleta de cores em nossos botões gera mais familiaridade entre as páginas do sistema e facilita a identificação de componentes.

Nós também solucionamos alguns _bugs_:

* **Rest / HTTP / HTTP-File Trigger:** agora é possível construir fluxos que recebam _tokens_ personalizados no header Authorization quando não se deseja utilizar o mecanismo JWT da Digibee. Para isso, desabilite a opção JWT na configuração do _trigger_.
* **Scheduler Trigger:** em raras situações, poderiam ocorrer duplicações da execução do pipeline. Foi adicionado um mecanismo de proteção para impedir que isso aconteça. Deseja saber mais sobre esse _trigger_? Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/triggers/scheduler-trigger) para ler o nosso artigo.

## Novidades 15/04/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

Melhoramos a usabilidade da lista de conectores, tornando os itens visíveis tanto para os usuários que não possuem mouse de rolagem quanto para os que preferem utilizar o _scroll_.\\

* **Choice:** a nossa nova mensagem de erro indica o caminho para que os itens repetidos sejam encontrados. Para ler o artigo sobre esse conector, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/choice).
* **File Reader:** adicionamos uma capacidade para leitura consolidada de todas as linhas em um único _string_ facilita o processamento de arquivos.
* **Rest Connector V2:** é possível informar o tipo do arquivo no envio baseado no multipart/form-data.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* **JMS:** _pipelines_ construídos com esse trigger adicionam mais resiliência ao parametrizar o consumo de mensagens/tópicos JMS. Para ler o artigo sobre esse _trigger_, clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/jms).

#### CANVAS <a href="#canvas" id="canvas"></a>

A paleta de componentes é acessível mesmo quando o test-mode se encontra aberto.

Nós também solucionamos alguns _bugs_:

* **Rest / HTTP / HTTP-File Triggers:** a mensagem de _log_ passou a mostrar o _payload_ inválido que é apresentado ao _pipeline_.
* **Execuções Simultâneas:** eliminamos o erro que não permitia a edição do execuções simultâneas quando o seu _pipeline_ associado era apagado.
* **Atalhos de Teclado:** agora a lista de atalhos possui uma barra de rolagem.
* **Breadcrumb:** voltou a ser possível copiar e colar o nome do _pipeline_/nível.

## Novidades 30/03/2020

#### CONECTORES <a href="#conectores" id="conectores"></a>

* **JMS:** agora suporta _double braces_ dinâmicos e estáticos. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/jms) para saber mais sobre esse conector.
* **SAP:** atualizamos a documentação desse conector com informações sobre iDoc. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/capsulas-publicas/sap) para ler.
* **Do-While:** criamos uma nova _feature_ que permite o seguimento normal do fluxo em caso de erros. Também atualizamos a documentação desse conector. Clique [aqui](https://docs.digibee.com/documentation/v/pt-br/components/logic/do-while) para ler.

#### DESIGN <a href="#design" id="design"></a>

O modal de atalhos com mais espaçamento entre os itens e clareamento da linha entre eles facilita a leitura dos dados.\\

#### CANVAS <a href="#canvas" id="canvas"></a>

O atalho _Shift + Delete_ é capaz de remover conectores durante a edição do _pipeline_, assim como o _Ctrl + Delete_.

#### BREADCRUMB <a href="#breadcrumb" id="breadcrumb"></a>

O menu “more” exibe todos os links que não cabem no _header_. Além disso, títulos que excedem o espaço são exibidos em sua totalidade através de _tooltips_.

![](../.gitbook/assets/mar\_01.gif)

Nós também solucionamos alguns _bugs_:

* **Dificuldades no login:** o Realm passou a poder ser digitado com letra minúscula, maiúscula ou intercalando as duas opções.
* **Mensagem de erro:** corrigimos uma falha de grafia em um aviso que aparecia durante a edição de _pipelines_.
* **OAuth Authentication:** resolvemos o problema que impedia a execução consecutiva de _pipelines_ utilizando a autenticação OAuth.
* **OAuth:** melhoramos o tratamento de obtenção de _tokens_ através do mecanismo OAuth utilizando recursos específicos dos provedores como Google e Microsoft.
* **iDoc SAP:** ajustamos uma limitação de envio do XML nesse modelo.
* **Kafka Connector:** agora são suportados os _security protocols_ SASL\_SSL e SSL.
* **Trigger:** solucionamos o problema de rota que esporadicamente tornava inacessíveis alguns _pipelines_ implantados.
* **JWT Connector:** as _requests_ deixaram de ser barradas em um cenário específico.

## Novidades 15/03/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### CONECTORES <a href="#conectores" id="conectores"></a>

Agora suportam _double braces_ estáticos:

* LDAP
* MongoDB
* ObjectStore

Para saber mais sobre os conectores, leia os artigos atualizados que disponibilizamos no nosso Help Center.

#### TRIGGERS <a href="#triggers" id="triggers"></a>

* Rest / HTTP / HTTP-File: Nova interface de configuração e nova funcionalidade que permitem adição de rotas personalizadas, promovendo maior flexibilidade, controle e segurança. [Saiba mais.](https://docs.digibee.com/documentation/v/pt-br/components/triggers/configuracoes-de-triggers/nova-interface-de-configuracao-e-rotas-personalizaveis)

\
Nós também solucionamos alguns _bugs_:

* **Diálogo de confirmação indevido:** resolvemos as mensagens intermitentes que surgiam ao salvar _pipelines_ e _libraries_.
* **Campo Account:** substituímos o campo Account por um menu suspenso na configuração do E-mail Trigger.
* **Choice Connector:** reparamos a falha de execução em linhas de Choice com nomes repetidos em OnProcess/OnException aninhados.
* **Rest Connector**: ajustamos a apresentação dos _headers_ padrão \_\_ desse conector na tela de configuração.
* **Estabilidade:** melhorias de estabilidade em caso de indisponibilidade de serviços.

## Novidades 27/02/2020

Gostaríamos de compartilhar algumas melhorias e novidades:

#### Trigger E-mail (BETA) <a href="#trigger-e-mail-beta" id="trigger-e-mail-beta"></a>

Os serviços de e-mail com suporte a IMAP são verificados por meio desse gatilho, que identifica mensagens não lidas e dispara o _pipeline_.\\

#### SQS - Amazon Simple Queue Service <a href="#sqs---amazon-simple-queue-service" id="sqs---amazon-simple-queue-service"></a>

#### ▸Connector (BETA) <a href="#connector-beta" id="connector-beta"></a>

Habilitamos o gerenciamento de filas de mensagens com o novo conector SQS.

#### ▸Trigger (BETA) <a href="#trigger-beta" id="trigger-beta"></a>

As mensagens SQS são processadas de acordo com ordem de entrada.\\

#### Melhorias no Breadcrumb <a href="#melhorias-no-breadcrumb" id="melhorias-no-breadcrumb"></a>

Agora o nome dado ao conector do tipo OnProcess/OnException é mantido no Breadcrumb, o que facilita a identificação durante a sua edição.

![](../.gitbook/assets/fev\_01.gif)

Nós também solucionamos alguns bugs:

* **Problemas com \_copy-paste**\_**:** em algumas situações, esse comando não estava retornando o valor esperado.
* **Mensagem indevida no Choice:** removemos a confirmação de saída da plataforma que surgia durante a edição desse conector.
* **Idioma \_tooltip**\_**:** alguns _tooltips_ não estavam no idioma correto.

## Novidades 15/02/2020

#### Novidades nos Conectores <a href="#novidades-nos-conectores" id="novidades-nos-conectores"></a>

Suporte a múltiplos arquivos e estrutura de diretórios no contexto do pipeline. Conectores como: FileReaderConnector, FileWriterConnector, CSVFileWriterConnector, CsvToExcelConnector, ExcelConnector, StreamExcelConnector e outros se beneficiam dessa nova funcionalidade.\
Confira mais detalhes [aqui](https://docs.digibee.com/documentation/v/pt-br/components/files/como-ler-e-escrever-arquivos-dentro-de-pastas).

#### Correção de bugs <a href="#correo-de-bugs" id="correo-de-bugs"></a>

▸ Contexto do atalho copiar e colar\
▸ Limitações de acesso ao Intercom\
▸ Ajustes no conector OAuth\
▸ Melhorias de usabilidade

## Novidades 30/01/2020

#### Novidades nos Conectores <a href="#novidades-nos-conectores" id="novidades-nos-conectores"></a>

DBConectorV2 com suporte a query para teste de conexão e opção para manter a conexão ativa por 5 ou 30 minutos.\
[https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2)

#### Novo recurso de alerta <a href="#novo-recurso-de-alerta" id="novo-recurso-de-alerta"></a>

Caso haja alguma alteração que exija sua ação nos pipelines você será notificado diretamente através da interface da plataforma.

\\

![](../.gitbook/assets/jan\_01.gif)

![](../.gitbook/assets/jan\_02.gif)

#### Correção de bugs <a href="#correo-de-bugs" id="correo-de-bugs"></a>

▸ Ajustes de usabilidade

## Novidades - 15/01/2020

#### HTTP File Trigger <a href="#http-file-trigger" id="http-file-trigger"></a>

Agora é possível fazer download de arquivos através do HTTP File Trigger.\
[https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger-downloads](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger-downloads)

#### Melhorias na Interface <a href="#melhorias-na-interface" id="melhorias-na-interface"></a>

▸ Maior acuidade visual em telas com baixa resolução\
▸ Consistência e mais facilidade para carregar mensagens e logs\
▸ Melhor aproveitamento de espaço no diálogo de configuração de conectores

#### Novidades nos Conectores <a href="#novidades-nos-conectores" id="novidades-nos-conectores"></a>

Google Storage Connector e Digibee Storage Connector agora possui a função de listagem e paginação.

{% embed url="https://docs.digibee.com/documentation/v/pt-br/components/file-storage/google-storage/google-storage-cenarios-de-uso" %}

![](../.gitbook/assets/jan\_03.gif)

#### Correção de bugs <a href="#correo-de-bugs" id="correo-de-bugs"></a>

▸ Ajustes no processo de recuperação de mensagens e logs

▸ Usabilidade - Diversos ajustes relacionados feedback, alinhamento e contraste

## 15/07/2019

#### Nova tela de login <a href="#nova-tela-de-login" id="nova-tela-de-login"></a>

Nossa nova tela de login está com visual repaginado, além de incluir diversas melhorias de segurança.

![](../.gitbook/assets/2019\_01.jpg)

#### Força da senha <a href="#fora-da-senha" id="fora-da-senha"></a>

Novo padrão para cadastro de senha na plataforma:

* mínimo de 8 caracteres
* ao menos uma letra maiúscula
* uma letra minúscula
* números e caracteres especiais.

![](../.gitbook/assets/2019\_02.jpg)

#### Autenticação com verificação de dois fatores <a href="#autenticao-com-verificao-de-dois-fatores" id="autenticao-com-verificao-de-dois-fatores"></a>

Reforçando ainda mais nossas opções de segurança, a verificação por dois fatores também foi disponibilizada a todos. Para mais informações sobre a verificação de dois fatores, clique abaixo:

#### PGP connector <a href="#pgp-connector" id="pgp-connector"></a>

Conector que implementa as práticas de Pretty Good Privacy, criptografando e descriptografando payloads recebidos via pipeline usando chaves públicas ou privadas.

## 30/07/2019

### \{{Double Braces\}}

Disponibilizamos novos recursos para entrada de dados nos conectores. Agora você pode simplificar a construção de suas integrações.

[Conheça o Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/double-braces-e-entrada-de-dados)

#### Funções <a href="#funes" id="funes"></a>

Conheça as funções disponíveis para simplificar conversões e transformações dos dados durante o fluxo dos seus pipelines.

[Ver funções](https://docs.digibee.com/documentation/v/pt-br/build/funcoes-double-braces/funcoes-condicionais?q=double+braces)

#### Conectores: <a href="#conectores" id="conectores"></a>

**Novos:**

* _Json Generator Connector_ - Componente que gera e transforma jsons de forma genérica. [veja aqui a documentação](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-generator)
* _Object Store_ - Base de dados da Digibee onde os clientes podem armazenar dados e realizar consultas, edições e exclusões de uma forma mais simplificada. [veja aqui a documentação](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/object-store)

**Atualização e melhoria:**

* _MongoDB_ - Aumentamos o tempo máximo de execução para 5 minutos (timeout).

#### Correção de Bugs: <a href="#correo-de-bugs" id="correo-de-bugs"></a>

Agora você pode utilizar componentes que precisam de OAuth 2.0 na tela de _Teste de Pipelines._
