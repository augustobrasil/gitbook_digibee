# Novembro

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FmOLYncsEjAvgQflkh1an%2Fheader_realeasenews_november.gif?alt=media&token=9dfec902-dffa-4943-a54b-f451097c5ea6" fullWidth="true" %}
Image do header de novidades ou release notes de novembro
{% endembed %}

## Novidades 28/11/2023

## Componentes

* **Transformer (JOLT) V2:** criamos uma nova versão do componente que permite o uso de expressões Double Braces para configurar expressões JOLT. Saiba mais na [documentação do Transformer (JOLT) V2](https://docs.digibee.com/documentation/v/pt-br/components/tools/transformer-jolt-v2).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F7zzH5JV6I81I0qsdLpHK%2Ftransformer_jolt-v2_GA.mp4?alt=media&token=d9d1828c-35ca-40bc-8cdd-18a794f03f2e" %}
Video do componente Transformer (JOLT) V2
{% endembed %}



## Atualização do Message Broker no Pipeline Engine v2 (Beta Restrito)

Atualizamos o RabbitMQ, o message broker da Digibee Integration Platform, exclusivamente para o Pipeline Engine v2. Esta nova versão oferece mais resiliência e disponibilidade ao sistema de mensagens da Digibee Integration Plataform.

Saiba mais na [documentação do Pipeline Engine v2](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).



## ZTNA na Digibee Integration Platform (General Availability)

Agora o Zero Trust Network Access (ZTNA) é a principal tecnologia de conectividade da Digibee Integration Platform para novos clientes. Esse novo modelo está disponível em General Availability para todos os interessados.\
\
Saiba mais na [documentação do ZTNA](https://docs.digibee.com/documentation/v/pt-br/plataforma/zero-trust-network-access-na-digibee-integration-platform).



## Monitor — Download de logs de execução de pipeline (Beta)

Com nossa nova feature de download de logs de execução de pipelines, na página de Execuções concluídas em Monitor, as pessoas usuárias podem fazer o download dos logs de uma execução de pipeline específica, associada a uma chave de execução de pipeline específica no formato CSV.\


Uma **chave de execução de um pipeline** é um identificador único de um pipeline.



O arquivo CSV tem as seguintes informações:

* timestamp
* realm
* pipelineKey
* pipelineName
* logLevel
* logMessage

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F5nkjgIF8H5pPNRimF4eD%2FPipeline_execution_logs_download.mp4?alt=media&token=34d71ab2-0297-4ed8-b956-8d00cd9055af" %}
Video da feature de download de logs de execução de pipelines
{% endembed %}



## Monitor — Mudanças de textos

Para trazer mais clareza entre os dados e as informações disponíveis, mudamos alguns de textos na página de Monitor.&#x20;

Essas mudanças incluem o termo **Pipeline key (chave de pipeline)** e textos sobre **tempo de expiração de logs da execução e pipeline logs.**\


**Termo pipeline key:**

Na página Execuções concluídas, mudamos o termo **chave do pipeline (pipeline key)** para **chave de execução do pipeline (pipeline execution key)** porque cada chave se refere a uma execução de pipeline única, e não ao pipeline em si.&#x20;

Era possível associar de forma incorreta a chave de execução do pipeline com um dado de identificação do pipeline em si.\


**Texto sobre data de expiração:**

Ainda na página Execuções concluídas e ao ver os detalhes de uma execução, mudamos o texto de **Tempo para o histórico de logs expirar** para **Histórico de execuções concluídas expira em.**

Na página Pipeline logs, mudamos o texto de T**empo para o histórico de logs expirar** para **Histórico de pipeline logs expira em.**\


\
Documentação de pipelines com IA (General Availability)
-------------------------------------------------------

om esta nova funcionalidade, as pessoas usuárias podem criar documentação do fluxo do pipeline com um único clique usando tecnologias avançadas de IA. A documentação inclui a descrição do fluxo, os sistemas externos envolvidos, os eventos enviados dentro do pipeline e uma lista de variáveis globais e contas usadas no pipeline.

Saiba mais em [Documentação de pipelines com IA](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/pipeline-documentation-with-ai).

Esta funcionalidade está disponível para todos os clientes que assinaram um contrato com a Digibee após 27 de novembro de 2023. Se o cliente não desejar esta funcionalidade, ele deverá enviar uma solicitação em nosso canal de suporte para desativar a funcionalidade. Clientes com contratos assinados antes de 27 de novembro de 2023 devem enviar uma solicitação através do suporte para ativar a funcionalidade. Consulte os [Termos de uso para funcionalidades de IA](https://docs.digibee.com/documentation/v/pt-br/general/terms-of-use-for-ai-functionalities).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FjZE9e1gf3MHzVLCTBznX%2FPipeline%20documentation%20overview%20with%20AI.mp4?alt=media&token=790417bd-45e9-47cc-a994-8902f3cbc2d8" %}
Video da feature de documentação de pipelines com IA
{% endembed %}

\
Melhoria na performance do canvas de pipeline (Beta Restrito)
-------------------------------------------------------------

Fizemos uma melhoria na performance do canvas de pipeline para melhorar a usabilidade, navegação e tempo de resposta do canvas.&#x20;

\
Essa atualização está em beta restrito para todos os realms que tem acesso aos [modos de design e debug](https://docs.digibee.com/documentation/v/pt-br/build/new-canvas-beta-restricted/design-and-debug-mode-restricted-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FfrzqLtWdvJ24S5bf64zz%2FCanvas-performance-enhancement-.jpg?alt=media&token=650c500e-f72f-46f7-9276-24a65388ad59" %}
Video da melhoria de performance do canvas
{% endembed %}



## Digibee Academy — Webinar Advanced Security

Com nosso novo webinar sobre Advanced Security, você poderá desenvolver novas habilidades sobre pipelines com robustos recursos de segurança, componentes e práticas recomendadas do setor.

Os principais tópicos incluem:

* Avalie e mitigue riscos potenciais em qualquer projeto de integração, usando os recursos de segurança da Digibee Integration Platform
* Proteja APIs autenticando o cliente via JSON Web Token (JWT)
* Proteja seus dados com criptografia e seus componentes, usando dados “Hashed” para controle de duplicatas.



## Novo curso no Digibee Academy — Event-Driven Architecture: Modular Integration Patterns

Temos um novo curso disponível para você aprimorar seus conhecimentos rumo à independência em integração!

Neste curso, você aprenderá a:

* Gerenciar dados não integrados criando um pipeline de reprocessamento
* Criar um pipeline que gerencie e centralize os erros, além de tratar as exceções para obter pipelines com tolerância a falhas
* Identificar quando for necessário criar pipelines reutilizáveis ​​no contexto de arquitetura de microsserviços.

Acesse o [Digibee Academy](https://digibee.academy/) agora!\






### Nós também solucionamos um bug:

* **Campos InSpec e OutSpec não retêm dados — Canvas:** solucionamos o bug em que os dados dos campos InSpec e OutSpec nas configurações do pipeline não guardavam os dados depois de salvar o pipeline.\


***

## Novidades 14/11/2023

## Componentes

* **Dupla Autenticação para o SFTP (**_**General Availability**_**):** atualizamos o componente para oferecer suporte a dupla autenticação usando contas tipo _Basic_ e _Private key_ ao conectar com servidores SFTP. Saiba mais na [documentação do SFTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/sftp).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F4B1vw1QM1NGiWf5fFZia%2Fdouble_authentication_SFTP_GA.mp4?alt=media&token=ffec50f0-7c35-414c-86da-b23346d961bb" %}
Video da atualização do componente SFTP
{% endembed %}



## Capacidade e cotas (Beta)

Agora, também mostramos as cotas de uso da Digibee Integration Platform.

Cotas são limites técnicos, criados com base no uso médio da Digibee Integration Platform e aplicados em cada _realm_.

Diferentes recursos podem ser consumidos para execução das integrações entre sistemas, e as cotas podem ser locais ou globais.

Não temos um limite de uso, mas sim uma capacidade de uso. Isso quer dizer que, se você consumir um recurso além de sua capacidade, o desempenho de suas integrações pode ser afetado.

Saiba mais na [documentação de Capacidade e cotas](https://docs.digibee.com/documentation/v/pt-br/licensing/usage-limits).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FJ8w9LPZl5wxowlEc8xhl%2FCapacity_quotas_BETA.mp4?alt=media&token=29672c6d-baa4-4ec5-9bde-7228f9fcdcb1" %}
Video da feature capacidade e cotas
{% endembed %}

##

## Monitor — Alertas (Beta)

Nossos alertas de notificação de Monitor foram promovidos da fase Beta para _General Availability._

Essa _feature_ permite às pessoas usuárias criar alertas para comportamentos inesperados usando métricas do _pipeline_, individualmente ou por _realm_.

Você pode configurar as preferências de alertas para receber notificações por e-mail, [Telegram](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-telegram), [Webhook](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-through-a-webhook) e [Slack](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-slack).

Saiba mais na [documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).​

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FVStVpWZULkk7zKruDci1%2FAlerts_GA.mp4?alt=media&token=f9615e37-c12d-4f39-b9fa-8e623825a802" %}
Video da feature Alertas em Monitor
{% endembed %}



### Atualização do Message Broker no Pipeline Engine v2 <a href="#undefined" id="undefined"></a>

RabbitMQ, _message broker_ da Digibee Integration Platform, foi atualizado exclusivamente para Pipeline Engine v2. Esta nova versão oferece mais resiliência e disponibilidade ao sistema de mensagens da Plataforma.

Saiba mais na [documentação do Pipeline Engine v2](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).\
​​

### Digibee Academy — Pesquisa sobre preferências de aprendizado <a href="#undefined" id="undefined"></a>

\
Como parte do nosso compromisso de melhorar a sua experiência de aprendizado, convidamos você a participar de uma [pesquisa rápida sobre preferências de aprendizado](https://forms.gle/3TacHsppSeyqc5o39).&#x20;

Seus insights são muito importantes e suas respostas nos ajudarão a adaptar nosso conteúdo educacional para melhor atender às suas preferências.

A pesquisa estará disponível até 30 de novembro de 2023.



## Notificação de alteração de configurações de contas em _pipelines_ implantados (_General Availability_)

Agora, quando as pessoas usuárias visualizarem ou editarem os detalhes de uma conta na página de Contas, elas terão acesso a uma lista de _pipelines_ associados com a conta. Isso permite o rastreamento e a atualização dos _pipelines_ associados, quando necessário.

As pessoas usuárias também verão um aviso na página de Run de quaisquer _pipelines_ implantados, sempre que as contas forem editadas, facilitando o processo de reimplantação.

Leia mais na documentação [Monitore mudanças de contas em pipelines implantados.](https://docs.digibee.com/documentation/v/pt-br/settings/accounts/monitor-changes-to-account-settings-in-deployed-pipelines)\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FtyYVPQB2obVIwdeW2BMO%2Fnotification_changed_account_GA.mp4?alt=media&token=a4dd248c-52f1-4753-81c6-f1a5bba08ff5" %}
Video da feature de notificações ao mudar configurações em Contas associadas a pipelines
{% endembed %}





### Nós também solucionamos alguns _bugs:_ ​

* **SFTP — Componentes:** corrigimos os _bugs_ que causavam a sobrescrita dos arquivos ao usar as operações _Upload_ e _Move_, mesmo com o parâmetro “_Overwrite File on Upload_” desativado.
* **Página em branco no canvas:** corrigimos o _bug_ em que, ao abrir as configurações dos componentes FTP e SSH Remote Command, a página do canvas ficava em branco. Desativamos temporariamente a _feature_ de _syntax highlight_ de _Double Braces_ para resolver esse erro, porém, ela já está funcionando normalmente.

