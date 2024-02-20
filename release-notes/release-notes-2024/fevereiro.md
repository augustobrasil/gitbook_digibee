# Fevereiro

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fva1demKBl0Ex0cPROZcr%2Fheader_realeasenews_February.gif?alt=media&token=19f38c4a-b9eb-4d9e-978c-fa4c233ba0c3" %}
Image do header de novidades ou release notes de fevereiro
{% endembed %}

##

## Novidades 20/02/2024

## Componentes

* **JSON Path Transformer V2 (General Availability):** lançamos uma nova versão do componente que permite a pessoa usuária receber qualquer entrada válida JSON e fazer filtros e extrações de dados de uma expressão. Essa versão do componente também suporta expressões Double Braces.\
  Saiba mais na [documentação do componente JSON Path Transformer V2.](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-path-transformer-v2)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FqKa3JsMsCxfAlMcS4Pbn%2Fjson-path-transformer-v2%20GA.mp4?alt=media&token=2c1a2320-96b7-47bb-8104-1af1599271f0" %}
Vídeo da nova versão do componente JSON Path Transformer V2
{% endembed %}

##

## Auditoria — Exportação de registros de auditoria (General Availability)

Fizemos uma melhoria na página de Auditoria que permite que você exporte um arquivo CSV com os registros de auditoria com um único clique.&#x20;

Com essa melhoria, você pode ter mais informações sobre os registros de auditoria, salvá-los localmente em seu computador e também usar uma ferramenta externa para ler os registros.&#x20;

Saiba mais na [documentação de Auditoria](https://docs.digibee.com/documentation/v/pt-br/administration/audit).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FlbBQ31QRkbcNHMZD46Lc%2Fsensitive-fields-policy%20GA.mp4?alt=media&token=6402620b-619e-420e-8f3a-bf263eeab0ea" %}
Vídeo da feature de exportar logs de auditoria
{% endembed %}



## Nova política — Campos sensíveis (Beta)

A política de campos sensíveis é uma nova feature que permite configurar campos sensíveis para o realm como uma política. Agora, você pode gerenciar esses campos sensíveis para todos os pipelines em um único lugar.&#x20;

O campo sensível é um mecanismo que já existe nos pipelines na Digibee Integration Platform. Com ele você pode configurar para algumas informações serem escondidas nos logs do pipeline, como IDs, endereços e números de bancos.&#x20;

Saiba mais na [documentação sobre Campos sensíveis](https://docs.digibee.com/documentation/v/pt-br/governance/policies/sensitive-fields).



{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FnFokzKNFkJ0sECdYVO7m%2Fsensitive-fields-policy%20BETA.mp4?alt=media&token=30cb7963-990b-4466-bafe-d031ac5b9580" %}
Vídeo da feature de políticas de campos sensíveis
{% endembed %}

##

## Digibee Academy — Nova página do Digibee Academy no Portal de Documentação

O time do [Digibee Academy](https://digibee.academy/) agora tem uma página própria no Portal de documentação, tanto em [inglês](https://docs.digibee.com/documentation/about-digibee-academy) quanto em [português](https://docs.digibee.com/documentation/v/pt-br/about-digibee-academy).

Lá você encontra um panorama dos cursos e treinamentos que oferecemos e todos os benefícios de se tornar estudante do Academy. Além disso, não perca a oportunidade de baixar nosso [Guia do Academy](https://digibee.academy/class-materials/Guidebook/Guidebook\_Digibee%20Academy\_PT.pdf) para obter informações detalhadas sobre nossos treinamentos!

\


### Nós também solucionamos alguns bugs:

* **Canvas — Página em branco no canvas ao abrir o formulário de um componente**: corrigimos o bug que fazia com que a área do canvas ficasse em branco ao abrir o formulário de configuração dos componentes.
* **Cápsulas — Abas incorretas na prévia do formulário de configuração de Cápsulas:** corrigimos o bug que exibia abas incorretas na prévia do formulário de configuração de Cápsulas.
* **Canvas — Melhoria na experiência de copiar e colar dentro do canvas:** corrigimos o bug que selecionava textos da página do canvas e os componentes de forma simultânea, impedindo a ação de colar de funcionar corretamente.&#x20;
* **Canvas — Ajustes na performance do canvas:** realizamos melhorias e ajustes gerais de performance na interação com o canvas, visando proporcionar uma experiência mais fluida, o que também pode impactar positivamente na experiência de copiar e colar.
* **OAuth — Animação de clique no indicador de etapas nas configurações do provedor OAuth:** corrigimos o bug em que uma animação era exibida ao clicar no indicador de etapas nas configurações do provedor OAuth, mesmo quando não era possível interagir com as etapas.
* **Componentes — Cassandra DB:** corrigimos um bug que causava um erro na conversão do tipo de dado ao usar expressões Double Braces no componente.
* **Componentes — Precisão numérica (Engine V2):** corrigimos um bug que causava um comportamento incorreto na utilização da feature de precisão numérica no Engine V2.



***



## Novidades 06/02/2024

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
