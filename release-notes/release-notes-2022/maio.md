# Maio

## Novidades 24/05/2022

#### **COMPONENTES**

* **CassandraDB:** corrigido para salvar JSON em um _string_ no Cassandra e _mapping_ para os tipos principais suportados por ele (_map, list, set, int, timestamp_, etc.), exceto os seguintes: _tuple, duration, user-defined types_ e _blob_ que ainda não são suportados. Leia a [documentação do CassandraDB aqui](../../components/structured-data/cassandra-db.md).
* **Kafka:** agora é possível definir as configurações de Acks e Client ID ao produzir mensagens para um broker Kafka. Também adicionamos ao componente a capacidade de configuração das estratégias de _Key_ e _Value_ (_Subject strategy_) ao produzir mensagens com dados no formato Avro. Leia a [documentação do componente Kafka aqui](../../components/queues-and-messaging/kafka.md).

#### **TRIGGERS**

* **Kafka:** agora é possível consumir mensagens no formato **Avro,** além do formato _string_. Leia a [documentação do Kafka trigger aqui](../../components/triggers/kafka-trigger.md).
* **HTTP:** agora todos os triggers do tipo HTTP (HTTP, REST, HTTP-FILE) informam uma nova propriedade contendo a _absolute URI_ da chamada. Leia a documentação do [Rest trigger](../../components/triggers/rest-trigger.md) aqui. E saiba mais sobre o [HTTP trigger aqui](../../components/triggers/http-trigger.md).

#### **FUNÇÕES**

* **BASEURLENCODE e BASEURLDECODE:** através dessas funções, é possível codificar e decodificar Base64 _URLs_. Leia a [documentação completa das Funções aqui](../../build/double-braces/funcoes-double-braces/double-braces-funcoes-de-utilidades.md).

#### **CONTROLE DE ACESSOS**

* Criamos uma funcionalidade que permite que um usuário com permissão de apenas leitura tenha acesso à visualização de detalhes na página de Grupos ao clicar no ícone de olho.

**IMPORTANTE**: em breve adicionaremos essa funcionalidade em outras páginas da Plataforma.

![](<../../.gitbook/assets/image1 (1).png>)

#### **ASSOCIAÇÃO DE ITENS**

* Melhoramos a experiência de associação de itens na Plataforma para as páginas Usuários, Grupos, Projetos, digibeectl e Chaves de API. Agora, ao clicar fora do campo de seleção, os itens selecionados são automaticamente associados. Isso previne problemas relacionados a associações não salvas caso o usuário esqueça de clicar no botão de confirmação (ícone ☑).

![](<../../.gitbook/assets/image2 (3).png>)

Nós também solucionamos alguns _bugs_:

* **Histórico de pipelines:** corrigimos o erro que impedia que alguns usuários abrissem uma versão _minor_ antiga dos _pipelines_.
* **Componentes:** corrigimos o erro que exibia uma descrição incompleta dos campos de alguns componentes.
* **Configuração de pipelines:** corrigimos o erro que impedia o usuário de salvar as configurações de um _pipeline_ se o campo “descrição” estivesse vazio.
* **API key:** corrigimos o erro ocorrido ao publicar pipelines com nomes ou _paths_ customizados que iniciavam com palavras idênticas.

## Novidades 10/05/2022

#### **COMPONENTES** <a href="#h_688fea3d7b" id="h_688fea3d7b"></a>

* **CassandraDB:** lançamos o componente Cassandra que realiza operações em bancos de dados modelo Apache CassandraDB e Amazon Keyspaces. Leia a [documentação do CassandraDB aqui](../../components/structured-data/cassandra-db.md).
* **JWT:** adicionamos o algoritmo AES 256 GCM de criptografia de _payloads_ para geração e decodificação de JWE. Leia a [documentação do JWT aqui](../../components/security-components/jwt-deprecated.md).
* **WebDAV V2:** criamos uma nova versão do componente WebDav para dar suporte ao _Double Braces_ nos parâmetros _File Name, Remote File Name e Remote Directory_. Leia a [documentação do WebDAV aqui](../../components/file-storage/webdav.md).

#### **TRIGGERS** <a href="#h_a0065a34e4" id="h_a0065a34e4"></a>

* **REST, HTTP e HTTP FILE:** adicionamos a capacidade de definir CORS Headers a serem retornados pelo _endpoint_ quando o processamento no _pipeline_ terminar. Este parâmetro define o CORS especificamente ao pipeline e suas restrições. Leia a [documentação sobre os _triggers_ aqui](../../components/triggers/).

#### **FUNÇÕES** <a href="#h_e225ef93c2" id="h_e225ef93c2"></a>

* **URIEncode e URIDecode:** estas duas novas funções permitem codificar e decodificar _URIs_, respectivamente. Leia o [artigo Double Braces - Funções de Utilidades](../../build/double-braces/funcoes-double-braces/double-braces-funcoes-de-utilidades.md) para mais detalhes.

#### **GRUPOS DIGIBEE - INTEGRAÇÃO COM PROVEDORES DE IDENTIDADE** <a href="#h_3c33c27e05" id="h_3c33c27e05"></a>

* Melhoramos o componente de mapeamento ao criar integração. Antes da mudança, era necessário clicar no botão “**+ INTEGRAÇÃO**” para exibir o formulário de mapeamento de integração. Agora, ao abrir o painel lateral de integração de grupos, o formulário para realizar o primeiro mapeamento é exibido em branco, para que o usuário preencha as informações necessárias.

Para saber mais, leia [o artigo sobre Integração dos grupos IdP com grupos Digibee](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/).

#### **CONTROLE DE ACESSOS** <a href="#h_98c3fd15f7" id="h_98c3fd15f7"></a>

* Criamos uma nova funcionalidade que permitirá ao usuário com permissão somente leitura tenha acesso à aba de detalhes nas páginas Usuários e Papéis.

**Importante**: em breve adicionaremos essa capacidade em outras páginas da Plataforma.

![](../../.gitbook/assets/WCxGRqR4GfHEyYuZJspuwDf11xiHrS5MaD7QiFoQjqqP4heAo6nvezyzL0r7gN5pqdyoJCLQYG4yU7GefQXqaiM2GtzXC6AgFM\_eIx9Lgj2cFWxUr56jfOqDYHl4ddMtTn9Y7osfsCgxoJcALQ.png)

Nós também solucionamos alguns _bugs_:

* **Pipeline:** corrigimos o _bug_ que gerava a exceção “java.util.ConcurrentModificationException” durante a execução de alguns _pipelines_.
* **API Key**: corrigimos o erro que impedia o usuário de arquivar ou editar um consumer contendo o caractere “.” no nome.
* **digibeectl**: corrigimos o comportamento que impedia a criação de _tokens_ e retornava o erro 500 ao usuário. Leia a [documentação para atualizar a versão do seu digibeectl aqui](../../plataforma/digibeectl/).
