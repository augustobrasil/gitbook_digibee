# Agosto

## Novidades 31/08/2022



#### COMPONENTES

* **Documentação:** agora é possível acessar a documentação de triggers e componentes diretamente de seus formulários no Canvas.

<figure><img src="https://lh5.googleusercontent.com/nSUmC4GcMJJmzeLe9HET1JtYjaZqjZEtzrANdT6eaXNFD0PkBwaLdZKrnf_9TZdlPexsivqbfO6P4z3dG7h_OR2LI-JA0mekLBnwXJZa7m3Rl8u-mtrmTBu5ahDPWRNuB0vsVpEoe_8APEN49UM6ErIT-NxBeTbuTYlahjGdWDrYNPZX3-thkd3L7Q" alt=""><figcaption></figcaption></figure>

**Componentes descontinuados:** versões antigas de componentes, como REST v1 e DB v1, foram removidas da lista de componentes e descontinuadas. Os componentes descontinuados continuam visíveis e funcionais dentro dos pipelines que os utilizam, no entanto, não é mais possível copiá-los ou colá-los.\


#### MONITOR

* **Execuções concluídas:** adicionamos um botão para limpar os parâmetros de busca na página de execuções concluídas.

<figure><img src="https://downloads.intercomcdn.com/i/o/571181276/a5becb348bf47620a70315e6/monitor+BR.png" alt=""><figcaption></figcaption></figure>



#### CLASSIFICAÇÃO DE ACESSO DE USUÁRIOS

Criamos uma funcionalidade para _realms_ integrados com Provedores de Identidade (IdP). Agora, você poderá **visualizar** a classificação de acesso de usuários por características de autenticação e autorização, na página de **Usuários**.

Ao exibir essas informações, a Plataforma ajuda na autossuficiência do gestor de acessos para resolver questões relacionadas à gestão de identidade e acesso de usuários, assim como na tomada de decisões sobre a governança de seu _realm_.

**IMPORTANTE:** atualmente, essa funcionalidade está disponível apenas para _realms_ integrados com Provedores de Identidade (IdP).

Para saber mais, leia nossa [documentação de classificação de acesso de usuários.](https://docs.digibee.com/documentation/v/pt-br/administration/visualizacao-da-classificacao-de-acesso-na-pagina-de-usuarios)

#### DOCUMENTAÇÃO

Visando melhorar nossa documentação, criamos os artigos abaixo:

* [Chaves de API (Consumers)](https://docs.digibee.com/documentation/v/pt-br/configurations/chaves-de-api-consumers)
* [Como enviar logs para serviços externos](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/como-enviar-logs-para-servicos-externos)





Nós também solucionamos um _bug_:

* **Execuções concluídas:** corrigimos a unidade de tempo exibida na coluna “Tempo decorrido” da tabela de execuções concluídas. A unidade correta é milissegundos, não segundos, como mostrado anteriormente.

## Novidades 17/08/2022

#### NOVO PORTAL DE DOCUMENTAÇÃO

Acesse o [novo portal de documentação](https://docs.digibee.com/documentation/v/pt-br/) da Digibee Integration Platform em [docs.digibee.com](http://docs.digibee.com/). Aproveite uma maior facilidade na navegação e na legibilidade dos artigos.

O [Help Center](https://intercom.help/godigibee/pt-BR/) da Digibee continuará sendo usado como uma ferramenta de suporte, base de conhecimento para _troubleshooting_ e resolução de problemas, e terá seu conteúdo atualizado em breve. Até lá, manteremos a convivência dos artigos antigos em ambas as plataformas.

#### COMPONENTES

* **Blob Storage (Azure):** fizemos uma melhoria no componente que permite listar _blobs_ de um _container_ como Copiados, Deletados, _Snapshots_ e _Uncommitted_, além de filtrar os resultados no momento da busca pelo campo _prefix._ Acesse a [documentação do Blob Storage aqui](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/azure-blob-storage).

#### MONITOR

* **Execuções concluídas:** adicionamos a unidade de tempo à coluna “Tempo decorrido” da tabela de execuções de _pipelines_.

#### DOCUMENTAÇÃO

Visando melhorar nossa documentação, criamos o artigo abaixo:

* [Cápsulas Públicas](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/capsulas-publicas)





Nós também solucionamos um _bug_:

* **Execuções concluídas:** corrigimos um _bug_ no filtro de tempo do tipo “específico”, que fazia com que a data selecionada fosse travada na data atual.

## Novidades 02/08/2022

#### **COMPONENTES** <a href="#h_8f6b4d5b07" id="h_8f6b4d5b07"></a>

* **SECURE PDF:** agora é possível atribuir senhas e permissões de acesso específicas a arquivos em PDF. Acesse a [documentação sobre Secure PDF aqui](../../components/tools/secure-pdf.md).
* **SOAP V3:** lançamos uma nova versão para o componente SOAP que possibilita chamadas a WebServices que utilizem as tecnologias MTOM, WS-Security e retornem _responses_ do tipo _Multipart_. Além dessas tecnologias, o componente também suporta todas as funcionalidades presentes no SOAP V2. Acesse a [documentação sobre SOAP V3 aqui](../../components/web-protocols/soap-v3-beta.md).

#### **FUNÇÕES** <a href="#h_a00d0b9960" id="h_a00d0b9960"></a>

* **STRINGMATCHES:** a função recebeu uma atualização. Agora, é possível informar mais de um _patternFlag_ para a função. Acesse a [documentação sobre STRINGMATCHES aqui](../../build/double-braces/funcoes-double-braces/funcoes-de-string.md).

#### **MONITOR** <a href="#h_7c3ba15c3a" id="h_7c3ba15c3a"></a>

* **Execuções concluídas:** agora é possível copiar em um clique o nome do _pipeline_ ou o _pipeline key_ de cada execução exibida utilizando os novos botões adicionados. Além disso, espaços em branco serão desconsiderados ao realizar buscas nesta página.
* **Pipeline metrics**: realizamos uma melhoria no _layout_ da página para prevenir cliques acidentais entre o _dropdown_ de seleção de _pipelines_ e o seletor do período de tempo.

#### **CONTAS** <a href="#h_b249caa189" id="h_b249caa189"></a>

Criamos uma funcionalidade que permite que um usuário com permissão de apenas leitura tenha acesso à visualização de detalhes na página de Contas ao clicar no ícone de olho.

![](<../../.gitbook/assets/rn (2).png>)

#### **CHAVES DE API** <a href="#h_4e1196e031" id="h_4e1196e031"></a>

Criamos uma funcionalidade que permite que um usuário com permissão de apenas leitura tenha acesso à visualização de detalhes na página de Chaves de API ao clicar no ícone de olho.

![](<../../.gitbook/assets/rn2 (1).png>)

#### **DOCUMENTAÇÃO** <a href="#h_28bc8c5457" id="h_28bc8c5457"></a>

Visando melhorar nossa documentação, criamos o artigo abaixo:

* [Intellisense](../../build/double-braces/intellisense.md)
