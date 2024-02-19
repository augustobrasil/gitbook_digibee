# Fevereiro

## Novidades 06/02/2024

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fva1demKBl0Ex0cPROZcr%2Fheader_realeasenews_February.gif?alt=media&token=19f38c4a-b9eb-4d9e-978c-fa4c233ba0c3" %}
Image do header de novidades ou release notes de fevereiro
{% endembed %}



## Monitor — Página Visão Geral (General Availability)

Mudamos o filtro Específico dos calendários na página Visão Geral que agora pode ser usado da mesma forma que os demais calendários em Monitor na Digibee Integration Platform.

Saiba mais na [documentação de Visão Geral](https://docs.digibee.com/documentation/v/pt-br/monitor/dashboards).

\


## Monitor — Filtro na página Pipeline logs (Beta)

Adicionamos o novo filtro Ordenar por que permite classificar os pipeline logs em ordem crescente (asc) ou decrescente (desc) de acordo com o timestamp.

Saiba mais na [documentação de Pipeline Logs](https://docs.digibee.com/documentation/v/pt-br/monitor/pipeline-logs).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FLqR47CK4UGKPE18pDiUN%2FNew%20filter%20on%20Pipeline%20Logs%20page%20BETA.mp4?alt=media&token=b976245c-9a26-46cc-9549-2bd9497e795c" %}
Video da feature do novo filtro na página de Pipeline logs
{% endembed %}

##

## Globals — Categorias e validação de Globals (General Availability)

Agora, ao criar uma nova [Global](https://docs.digibee.com/documentation/v/pt-br/settings/globals), é possível escolher entre uma lista de categorias e cada uma tem critérios de validação específicos.&#x20;

A categoria Other é a mais versátil, permitindo que você inserira qualquer valor. Porém, ao selecionar essa categoria, você será alertado a não adicionar dados sensíveis.&#x20;

Essa melhoria agiliza a criação de Globals, ao mesmo tempo que garante a conformidade com as melhores práticas de segurança de dados.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FdOnVJsJY2650KGSo4YDy%2FGlobals%20categories%20and%20validation%20GA.mp4?alt=media&token=233ed6ce-5794-4e14-9eef-df81eb9c0c4c" %}
Video da feature de categoria de globals
{% endembed %}

##

## Políticas — Relatório de status de conformidade (Beta)

Na [página de Políticas](https://docs.digibee.com/documentation/v/pt-br/governance/policies), agora é possível visualizar mais detalhes ao clicar no cartão que mostra o número de pipelines conformes e não conformes com as políticas.&#x20;

Os detalhes incluem o nome do pipeline e o problema, permitindo uma visão mais ampla dos pipelines não conformes e facilitando sua correção.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FtmwLf8lKDhS4orTEkRVj%2FCompliance%20Status%20Report%20%20BETA.mp4?alt=media&token=83cb66fb-c910-4167-9056-877f822e14f2" %}
Vídeo da feature de relatório de status de conformidade&#x20;
{% endembed %}



## Basic Auth (_General Availability_)

A _feature_ _Basic Auth_, que permite criar um método de autenticação para os _triggers_ Rest, HTTP e HTTP FIle, foi atualizada da fase beta e agora está disponível para todos os clientes.\
Saiba mais sobre _Basic Auth_ na [documentação de _Consumers_ (Chaves de API)](https://docs.digibee.com/documentation/v/pt-br/settings/api-keys-consumers).





### Nós também solucionamos alguns bugs:

* **Administração — Calendário com formatação incorreta na página de Auditoria:** corrigimos o bug onde o calendário estava sendo exibido com formatação incorreta ao selecionar um filtro específico na página de Auditoria.
* **Grupos — Mensagem incorreta na página de Grupos:** corrigimos o bug que mostrava uma mensagem incorreta ao aplicar um filtro na página e não encontrar nenhum resultado.&#x20;
* **Usuários — Redefinição de senha acessível a qualquer pessoa usuária:** corrigimos o bug que permitia que qualquer pessoa usuária redefinisse a senha da conta, independentemente da configuração do realm.
* **Cápsulas — Configurações da Cápsula não é salva em tempo real:** corrigimos o bug onde as configurações da Cápsula não eram salvas automaticamente, sendo necessário fechar e reabrir a Cápsula para aplicar as alterações.
* **Cápsulas — Publicação da Cápsula não permitida:** corrigimos o bug que impedia a publicação da Cápsula, mesmo quando a configuração estava correta.&#x20;
* **Cápsulas — Estilo de fonte diferente no primeiro campo do formulário de salvar a Cápsula:** corrigimos o bug onde o primeiro campo do formulário de salvar a Cápsula tinha um estilo de fonte diferente dos demais campos.
