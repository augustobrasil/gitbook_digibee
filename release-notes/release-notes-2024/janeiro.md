# Janeiro

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FRyQWmbReJSDUILpYWOnz%2Fheader_realeasenews_january.gif?alt=media&token=e2f82a26-17e1-41b8-ba50-53e949d62127" %}
Image do header de novidades ou release notes de janeiro
{% endembed %}

## Novidades 23/01/2024

## Componentes

* **Salesforce (Beta Restrito):** lançamos um novo componente que permite a pessoa usuária realizar operações na plataforma Salesforce. Ele está disponível para clientes específicos em Beta Restrito. Saiba mais na [documentação do componente Salesforce](https://docs.digibee.com/documentation/v/pt-br/components/enterprise-applications/salesforce-restricted-beta).
* **Rate Limit para os triggers REST, HTTP e HTTP File (General Availability):** a funcionalidade estava suspensa temporariamente, mas agora está disponível para todas as pessoas usuárias. Saiba mais na documentação do [REST Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger), [HTTP Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger) ou [HTTP File Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger).

\


## Coleção e grupo default em Cápsulas (Beta)

Agora, é possível criar Cápsulas em uma [coleção](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/how-to-use-capsules/how-to-create-a-capsule-collection) e [grupo](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/how-to-use-capsules/how-to-create-a-capsule-group) default, sem precisar criar uma coleção e um grupo separadamente para salvar a Cápsula. Além disso, a novidade permite [mover Cápsulas entre diferentes coleções e grupos](https://docs.digibee.com/documentation/v/pt-br/build/capsulas/how-to-use-capsules/how-to-change-a-capsule-collection-or-group).&#x20;

Essa melhoria não só economiza tempo, mas também simplifica o processo de criação de Cápsulas.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FtmsVTrRMSwPnWoD16c8S%2FDefault%20collection%20and%20group%20in%20Capsules%20BETA.mp4?alt=media&token=b07b6092-3a34-4621-b817-e33649d7b6b3" %}
Video da feature de coleção e grupo default em Cápsulas
{% endembed %}



## Novas permissões para Políticas (Beta)

Adicionamos duas novas permissões para a funcionalidade de Políticas: POLICY:UPDATE e POLICY:READ.&#x20;

Com POLICY:UPDATE, é possível editar as configurações da política na página Políticas.&#x20;

Já com POLICY:READ, é possível ver, mas não editar, as configurações da política na página Políticas.

Saiba mais na [documentação de Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FdUe8RATmpEpJ6KwKHIZN%2FNew%20permissions%20for%20the%20Policies%20feature%20UPDATE.mp4?alt=media&token=b6ebb8f7-b6c2-4667-9a17-9ecca3eedcf0" %}
Video da feature de novas permissões para Políticas
{% endembed %}

\
\


### Nós também solucionamos alguns bugs:

* **Componentes — REST Trigger:** corrigimos o bug que causava um comportamento incorreto ao configurar os CORS Headers usando o trigger.
* **Componentes — SSH Remote Command:** corrigimos o bug que causava um erro no componente após um determinado número de execuções.
* **Build — Criador do Projeto não consegue acessá-lo:** corrigimos o bug que não adicionava o usuário que criava o Projeto como membro dele, impossibilitando que ele o acessasse depois de salvá-lo.
* **Canvas — Erro ao executar pipeline sem componente conectado ao trigger:** corrigimos o bug que exibia um erro ao executar o pipeline quando não tinha nenhum componente conectado ao trigger.
* **Administração — Página de Auditoria com duas barras de rolagem:** corrigimos o bug que mostrava duas barras de rolagem na página de Auditoria.
* **Administração — Página de Auditoria com registros a mais por página:** corrigimos o bug que fazia com que a página de Auditoria exibisse mais registros do que o número indicado na paginação.
* **Configurações — Não é possível editar Campo em Modelo multi-instância:** corrigimos o bug que impossibilitava editar os valores do Campo em Modelo multi-instância. Agora é possível remover e adicionar valores novos.
* **Configurações — Nome “undefined” no Modelo multi-instância:** corrigimos o bug que salvava o nome do Modelo multi-instância corretamente na lista, mas ao abrir o modelo para configurar uma instância o nome era exibido como “undefined”.

