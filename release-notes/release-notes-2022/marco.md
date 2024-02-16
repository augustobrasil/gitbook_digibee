# Março

## Novidades 29/03/2022

#### **AUDITORIA**

Adicionamos a capacidade de filtrar os logs de auditoria pelo _status_ da requisição.

#### **CONTROLE DE ACESSOS**

Alteramos para 30/04/2022 a data limite para a adesão dos clientes ao novo modelo de controle de acessos.

#### **ARTIGOS**

Visando melhorar nossa documentação, atualizamos e criamos os artigos abaixo:

* [Relacionamento](../../settings/relacionamento.md)
* [File Writer](../../components/files/file-writer.md)

Nós também solucionamos alguns _bugs_:

* **Grupos:** corrigimos o erro que não mantinha a associação de membros a grupos quando o usuário clicava na aba permissões.
* **Configuração de Cápsulas: c**orrigimos o erro que impedia o carregamento da tela de configurações após arquivar o _header_ de uma cápsula.
* **Perfil**: corrigimos o erro que mostrava tela branca ao sair da plataforma à partir da tela de Administração.
* **Execuções concluídas:** corrigimos o erro que, ao abrir o detalhe de logs de um pipeline, requisições de outros pipelines se misturavam na mesma listagem.

## Novidades 15/03/2022

#### **MONITOR PIPELINES METRICS**

Para melhorar os dados apresentados e permitir uma análise mais detalhada de cada _pipeline_, diversas melhorias serão feitas na página de _Pipeline Metrics_.

A primeira delas é como visualizamos os dados dos gráficos:

1\. Consumo de Memória

2\. Consumo de CPU

Agora estes mostram o dado específico de cada réplica de um pipeline.

A segunda melhoria é no gráfico ‘Tamanho da Mensagem’ que separa o tamanho da mensagem de requisição (request) e mensagem de resposta (response).

Confira a documentação completa dos [gráficos de Pipeline Metrics](../../monitor/pipeline-metrics.md) aqui.

#### **AUDITORIA**

Para auxiliar na governança e no mapeamento de ações, toda e qualquer operação realizada dentro da Digibee Integration Platform é armazenada em segurança e apresentada no submenu ‘Auditoria’, localizado na página de Administração da Plataforma.

Nos últimos dias, melhoramos a experiência de consulta nos registros em Auditoria, trazendo o campo status:

* **Status:** o status da ação. Este parâmetro permite identificar ações executadas com sucesso e ações que apresentaram erros em sua execução.

Para saber mais, leia a [documentação completa de Auditoria](../../administration/auditoria.md).

#### **GRUPOS DIGIBEE - INTEGRAÇÃO COM PROVEDORES DE IDENTIDADE**

Agora, você pode gerenciar usuários com seu provedor de identidade corporativo (IdP) e usar os serviços de _Active Directory_ de gerenciamento de identidade e acesso para autenticar usuários quando entrarem na Digibee Integration Platform.

Para permitir isso, criamos uma seção dedicada chamada Integração de Grupos onde clientes, que possuem seu IdP configurado, possam realizar integrações entre grupos do Provedor de Identidade e grupos de acesso criados na Digibee Integration Platform seguindo as políticas de controle de acesso por papéis e grupos para obter benefícios como:

* Maior flexibilidade e escalabilidade ao conceder ou fazer mudanças de permissões para grande volume de usuários;
* Centralizar o gerenciamento de autorização de acesso no lado do cliente;
* Reduzir os riscos de segurança a partir dos benefícios da autenticação de identidade fornecida pelo IdP.

**IMPORTANTE:** para configurar seu provedor de identidade, contate o time de suporte através do chat dentro da Plataforma.

Leia o artigo [Integração com Provedor de Identidade](../../administration/identity-provider-integration/) para saber como configurar seu provedor de identidade.

Leia o artigo sobre [Integração dos grupos IdP com grupos Digibee](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/) para saber tudo sobre como fazer suas integrações pela Digibee Integration Platform.

#### **COMPONENTES**

* **Base64:** realizamos uma melhoria no componente. Agora é possível implementar o _decode_ de conteúdos binários (arquivos). A nova opção _IS BINARY_ informa se o _payload_ a ser realizado _decode_ é um conteúdo binário.
* **TRIGGER HTTP, REST E HTTP FILE:** Adicionamos a capacidade de configurar _headers_ de resposta estáticos ou dinâmicos (usando _double braces_) nos triggers.\
  Leia o artigo completo sobre [HTTP Trigger](../../components/triggers/http-trigger.md), [REST Trigger](../../components/triggers/rest-trigger.md) e [HTTP File Trigger](../../components/triggers/http-file-trigger/http-file-trigger-uploads.md).
* **Hash:** adicionamos a operação _Hash File_ ao componente, que possibilita a geração de _hash's_ MD5 de arquivos.\
  Leia o artigo completo sobre o componente HASH aqui.

#### **TRIGGERS**

* **Trigger Midnight Scheduler**: adicionamos a possibilidade de selecionar um fuso horário.

#### **ARTIGOS**

Visando melhorar nossa documentação, atualizamos e criamos os artigos abaixo:

* [Object Store](../../components/structured-data/object-store.md)
* [Transformações com JOLT](../../components/tools/transformer-jolt/transformacoes-com-jolt.md)

Nós também solucionamos alguns _bugs_:

* **Pipeline Metrics:** corrigimos o erro que, ao invés de mostrar os dados de Consumo de CPU em porcentagem, mostrava em fração. Ex: 20% era mostrado como 0,20.
* **Pipeline Metrics:** corrigimos o erro que não apresentava intervalos sem dados coletados.
* **Plataforma:** corrigimos o erro que apresentava a opção de ‘criar’ qualquer objeto mesmo se o usuário não tivesse permissão.

## Novidades 03/03/2022

#### HISTÓRICO DE VERSÕES DE PIPELINE (BETA) <a href="#h_155638b98e" id="h_155638b98e"></a>

Evoluímos o histórico de versões de pipelines. Essa evolução traz informações mais detalhadas a respeito de cada versão _Minor_ de um pipeline com base em sua versão _Major_. Agora, é possível saber quem editou pela última vez cada versão e quando ela foi alterada, além de saber se determinada versão está implantada e em qual ambiente (test ou prod). Essas informações otimizam a experiência dos usuários da Digibee Integration Platform no que se refere à organização e ao desenvolvimento de versões de _pipelines_.

Também é possível realizar diferentes ações no próprio histórico de versões, como editar a última versão _Minor_ do _pipeline_, visualizar e criar uma nova versão a partir de uma versão existente, e arquivar uma versão específica.\
Leia a [documentação completa de histórico de versões de pipelines](../../build/pipelines/historico-de-versoes-de-pipelines.md).

\
**IMPORTANTE**: A informação referente a quem editou uma versão será apresentada apenas nas versões criadas a partir de 1 de fevereiro de 2022. Versões criadas antes desta data não possuem dados de usuários em seus históricos e exibirão o valor padrão "No data". Pipelines criados antes do dia 15 de fevereiro de 2021 não possuem a informação de data de alteração e apresentarão o valor padrão “31/12/1969”.

#### ARTIGOS <a href="#h_6020dd376d" id="h_6020dd376d"></a>

Visando melhorar nossa documentação, atualizamos e criamos os artigos abaixo:

* [Monitor: visão geral](../../monitor/dashboards.md)
* [Monitor: execuções concluídas](../../monitor/completed-executions/)
* [Monitor: pipeline logs](../../monitor/pipeline-logs.md)​

#### TRIGGERS HTTP, HTTP File e REST - CORS (BETA) <a href="#h_2cb75cb72b" id="h_2cb75cb72b"></a>

Agora, a Digibee Integration Platform oferece a opção de configurar parâmetros de CORS para o seu realm.

O Cross-Origin Resource Sharing (CORS) é um mecanismo que permite informar ao navegador quais origens tem a permissão para fazer requisições ao servidor.\
Esta funcionalidade está em Beta, e para configurá-la é preciso contatar o suporte através do chat da plataforma.

Para mais informações, leia a [documentação de configurações globais de CORS aqui](https://github.com/tharso-rossiter-monteiro/PT-BR/blob/master/release-notes/release-notes-2022/broken-reference/README.md).

​

Nós também solucionamos alguns _bugs_:

* **Account:** corrigimos o erro que impedia contas corporativas do tipo OAuth2 da Microsoft de serem autenticadas.
* **Cápsulas:** corrigimos o bug que trazia a tela de criação de Cápsulas em branco.
* **Componentes:** corrigimos o erro que impedia componentes de conectar com serviços que utilizavam TLSv1.0 e TLSv1.1. Esse erro acontecia apenas em _pipelines_ sob construção ou que foram implantados na última semana.
* **CSV to Excel e Stream Excel:** corrigimos o erro que impedia a execução destes componentes em _pipelines_ sob construção ou que foram implantados na última semana.

**IMPORTANTE:** Algumas de nossas funcionalidades terminaram o período Beta e agora estão disponíveis para todos os usuários. São elas:

* [digibeectl](../../plataforma/digibeectl/)
* [Criação de novas implantações](../../run/deployment/deployments.md)
* [API Keys (Consumers)](../../settings/api-keys-consumers.md)
