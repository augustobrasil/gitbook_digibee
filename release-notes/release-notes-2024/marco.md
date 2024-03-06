# Março

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fkvk4JXHMxkDHmihD1lN9%2Fheader_realeasenews_March.gif?alt=media&token=a1f7760b-e933-4877-a342-eb5828d11f60" %}
Image do header de novidades ou release notes de março
{% endembed %}

## Novidades 06/03/2024

## Componentes

* **Salesforce (Beta):** o componente foi atualizado [de Beta Restrito para Beta](https://docs.digibee.com/documentation/v/pt-br/general/programa-beta). O componente Salesforce permite que a pessoa usuária faça operações na plataforma Salesforce. Saiba mais na[ documentação do componente Salesforce](https://docs.digibee.com/documentation/v/pt-br/components/enterprise-applications/salesforce-restricted-beta).





## Run — Funções avançadas do histórico de implantação (Beta)

Gostaríamos de anunciar o lançamento das funções avançadas do histórico de implantação. Essa nova feature possibilita o acesso à visualização ou restauração de qualquer versão anterior de um pipeline implantado.&#x20;

Saiba mais na [documentação sobre funções avançadas do histórico de implantação.](https://docs.digibee.com/documentation/v/pt-br/run/deployment/como-utilizar-as-funcoes-avancadas-do-historico-de-implantacao)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FzPm4WXwVHIVlHJX1bOg1%2Fdeployment-history-advanced-functions%20(2).mp4?alt=media&token=4afa610a-3669-4128-9236-c2c4fa52a518" %}
Vídeo da feature de funções avançadas do histórico de implantação
{% endembed %}





## Administração — Novas permissões para gerenciamento de projetos (General Availability)

O papel Project Manager agora tem a permissão PROJECT:READ:ALL. Com essa nova permissão, as pessoas usuárias podem ver todos os projetos, independentemente de serem membros ou não.&#x20;

Essa atualização também adiciona permissões para o papel Pipeline Manager, para possibilitar a gestão de projetos. As permissões adicionadas são: PROJECT:CREATE, PROJECT:UPDATE e PROJECT:DELETE.

Saiba mais na [documentação de Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fc42UwjqSppXHU6hJbLSX%2FNew%20permissions%20for%20the%20management%20of%20projects.mp4?alt=media&token=25609064-dde8-4aaa-9ad9-fceb32fa7b28" %}
Vídeo da feature de novas permissões para gerenciamento de projetos&#x20;
{% endembed %}







### Nós também solucionamos alguns bugs:

\


* **Canvas — Linha conectora entre componentes não é deletada:** corrigimos o bug que impedia remover a linha conectora entre os componentes do canvas.
* **Componentes — Salesforce:** corrigimos o bug que causava erro ao utilizar as operações Query e Search.
* **Componentes — Digibee Storage:** corrigimos o bug que impedia o componente de escolher a melhor região de nuvem de acordo com o cliente.
* **Globals — Validação de Globals:** corrigimos o bug que fazia com que a validação das Globals do tipo URL e JDBC não funcionasse corretamente.
* **Globals — Limite de caracteres no valor de Globals:** corrigimos o bug que limitava os caracteres do valor da Global para 200. Agora, o novo limite é de 10.000 caracteres.
* **Contas — Erro na autenticação de contas: corrigimos** o bug que impedia a autenticação e re-autenticação de contas do tipo “oauth-2”.
* _**Run — Rollback:**_ corrigimos o bug onde o processo de rollback era afetado pelo carregamento quando executado múltiplas vezes, o que causava instabilidade. Agora, o rollback é concluído com sucesso.
* **Run — Diferenças entre cards de pipelines:** corrigimos o bug que causava diferença de altura entre cards de  pipelines em versão beta e os que estão em diferentes fases.&#x20;
* **Permissões de acesso:** corrigimos o bug que permitia que pessoas usuárias visualizassem o histórico de pipelines sem as permissões necessárias do time de projetos.&#x20;
* **Run — Remoção da implantação do ambiente errado ao promover um pipeline:** corrigimos o bug onde, ao promover o pipeline entre ambientes, a implantação era removida do ambiente errado. Agora, ao promover o pipeline para prod, a implantação em test é removida, e os detalhes em prod são exibidos.

\
