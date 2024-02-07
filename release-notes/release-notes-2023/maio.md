# Maio

## Novidades 23/05/2023

### TRIGGERS

* **HL7 Trigger (beta restrito):** [a documentação do _trigger_ HL7](https://docs.digibee.com/documentation/v/pt-br/components/industry-solutions/hl7-trigger-beta-restrito) está disponível em nosso portal de documentação.\


### INTEGRAÇÃO DE GRUPOS IDP

Ativação da integração de grupos: agora, nos _realms_ integrados com provedores de identidade (IdP), os gestores de acesso podem ativar suas próprias integrações de grupos Digibee com grupos do Active Directory (AD) do IdP usando a página de [integração de grupos](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee).

Não é mais necessário entrar em contato com a Digibee para fazer isso.

Esta _feature_ está em fase beta. [Aprenda mais sobre o programa beta da Digibee aqui](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).



### CONSUMO DE LICENÇAS

Agora a página poderá ser acessada pelos usuários que pertencerem ao grupo padrão "_governance-managers_". O grupo foi ajustado para incluir um novo papel chamado "_license-viewer_", que permite a visualização do consumo de licenças do _realm_ e de seus projetos.

Esta _feature_ foi promovida de beta para _general availability_.

### &#x20; RUN

Busca Global para _pipelines_ implantados: agora é possível encontrar seu _pipeline_ implantado pelo nome, ou parte dele, através de uma busca por todos os projetos. Dessa forma, não é mais necessário entrar em cada projeto para encontrá-lo.



### NOVO CANVAS - TEST MODE

Tempo de execução do Test mode: agora, o tempo de execução de _pipelines_ no Test mode passará de 30 segundos para 1 minuto. Leia mais na [documentação sobre o Test mode](../../build/canvas/execution-panel.md).

### &#x20; NOVA IDENTIDADE VISUAL

A Digibee Integration Platform está com aparência nova devido à adequação das fontes e cores de identidade da marca.

\


#### Nós também solucionamos alguns _bugs:_ 

**NOVO CANVAS**

* **Test mode:** corrigimos o _bug_ em que o Test mode não executava com o atalho (CTRL+Enter ou Cmd+Enter) quando estava aberto e com foco no _Input_ ou _Output_.
* _**Pipeline**_** bloqueado ao salvar:** corrigimos o _bug_ que bloqueava o botão SALVAR quando o _pipeline_ tinha um erro em um fluxo desconectado.





## Novidades 09/05/2023

### COMPONENTES

* **Validator V2 (General Availability):** criamos uma nova versão do componente que valida conteúdo JSON de forma dinâmica via Double Braces, com base em um JSON Schema. Saiba mais na [documentação do Validator V2](https://docs.digibee.com/documentation/v/pt-br/components/tools/validator-v2).
* **HL7 Trigger (Beta Restrito):** criamos um novo trigger que recebe mensagens no formato HL7 (Health Level 7) na Digibee Integration Platform. Este trigger está atualmente em [fase Beta Restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta#h\_d59e60e1bd) e disponível somente para clientes específicos.
* **CassandraDB, CSV to Excel e Zip File (General Availability):** os componentes estão em fase General Availability e disponíveis para todos os usuários. Saiba mais na documentação do [Cassandra DB](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/cassandra-db), [CSV to Excel](https://docs.digibee.com/documentation/v/pt-br/components/files/csv-to-excel) e [Zip File](https://docs.digibee.com/documentation/v/pt-br/components/files/zip-file).

### &#x20;NOVO CANVAS - TEST MODE

Fizemos algumas melhorias no Test mode do Novo Canvas. Agora, é possível redimensionar o tamanho da janela e também das colunas de Input e Output na aba de Teste. Além disso, o Test mode exibirá até 1000 mensagens de uma execução no Novo Canvas. Saiba mais na [documentação de Test mode](../../build/canvas/execution-panel.md).



### MONITOR - EXECUÇÕES CONCLUÍDAS

Adicionamos um link em Detalhes da execução que redireciona o usuário ao Canvas do pipeline cuja execução está sendo analisada. Esta _feature_ está em fase Beta. Saiba mais sobre o [programa Beta da Digibee aqui](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

### PÁGINA DE GRUPOS

Adicionamos à página de Grupos um _tooltip_ que exibe a descrição completa do grupo ao passar o cursor do mouse sobre a descrição do grupo.\
\
\


#### Nós também solucionamos alguns bugs:

#### NOVO CANVAS

* **Test mode:** corrigimos o bug que removia o conteúdo do Payload e Output do Test mode caso a página fosse atualizada.
* **Atalhos:** corrigimos o bug que impedia o uso dos atalhos para selecionar todos os componentes do novo Canvas de uma só vez (CTRL+A ou CMD+A).
* **Barra de tarefas:** corrigimos o bug onde o título da barra lateral esquerda do novo Canvas sumia ao rolar a barra para a lateral.
* **Configurações do pipeline:** corrigimos o bug que ativava a ação de salvar ao usar a tecla TAB para navegar entre os campos Name e Description nas configurações do pipeline.&#x20;
* **Componentes desconectados não são exibidos:** corrigimos o bug onde os componentes de subnível que tinham Choice ou Parallel desconectados sumiam no novo Canvas.
* **Flow tree:** corrigimos o bug onde a navegação pelo Flow tree não funcionava ao tentar voltar de um subnível do pipeline.
* **Cápsulas:** corrigimos o bug onde as Cápsulas apareciam sem os ícones quando eram arrastadas para o novo Canvas.
* **Breadcrumb do pipeline:** corrigimos o bug onde não era possível voltar para o nível principal do pipeline usando o breadcrumb.\


#### OUTROS

* Corrigimos um bug onde, às vezes, os filtros de nome e versão do pipeline não eram aplicados quando o usuário clicava no ícone de lupa na página de Visão geral.
* Corrigimos um bug onde a interface gráfica da página de Visão geral exibia a seleção incorreta do filtro de tempo quando o usuário alternava entre a aba de Monitor e outras abas.
