# Setembro

<figure><img src="../../.gitbook/assets/header_realeasenews_September.gif" alt=""><figcaption><p>Image do header de novidades ou release notes de agosto</p></figcaption></figure>

## Novidades 19/09/2023

## Página de Regras de autenticação (Beta)

Mudamos o nome do nosso menu de Acessos via IdP para Provedor de identidade. Além disso, a feature Acessos via IdP agora se chama Regras de autenticação. Para acessá-la, vá em Provedor de Identidade e então clique em Regras de autenticação.

Essa feature está atualmente em fase beta. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).\


{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FDKNkAczE11RGD2xLHyjd%2FAuthentication%20rules%20page.mp4?alt=media&token=c81d120f-088f-4f51-b5b7-1e5032f60377" %}
Vídeo da página de regras de autenticação
{% endembed %}

## Aprimoramento de precisão numérica no Engine v2 (Beta restrito)

Os números decimais de ponto flutuante transmitidos no pipeline de um componente agora podem ser representados com mais precisão com todas as casas decimais originais.

Saiba mais na [documentação sobre Pipeline Engine v2](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).\
\
Essa feature está em beta restrito e disponível apenas para clientes específicos. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).



## Monitor - Alertas por realm - múltiplos pipelines (Beta restrito)

Agora é possível configurar um alerta para todos os pipelines de um realm de uma só vez, e, quando configurado, o sistema pode enviar uma notificação assim que atingirem o limite especificado para a métrica escolhida.

Saiba mais na [documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).

Essa feature está em beta restrito e disponível apenas para clientes específicos. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fx9qfx23iB7noWg8oHMD2%2FAlerts%20by%20realm.mp4?alt=media&token=1d85bbab-5ea2-4238-b903-51de929a3cc4" %}
Vídeo da feature de alertas por realm
{% endembed %}

## Monitor - Pipeline metrics em ferramentas de monitoramento externo (Beta restrito)

Esta feature foi criada para permitir que as pessoas usuárias integrem facilmente métricas de pipeline em ferramentas de monitoramento centralizadas via API de Métricas. No momento, Datadog e Prometheus estão disponíveis.

Essa feature está em beta restrito e disponível apenas para clientes específicos. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).\


## Run - Modifique e rastreie implantações de pipeline associadas à Globals (General Availability)

Esta é uma nova feature desenvolvida pelo time de Run. Ela dá às pessoas usuárias uma visão clara e abrangente das alterações feitas nas variáveis de Globals, permitindo que elas rastreiem todos os pipelines implantados associados à determinada Global.\
Além disso, os pipelines implantados que não possuem Globals atualizadas são destacados com uma mensagem informativa nos cards.

Saiba mais na [documentação sobre Modifique e rastreie implantações de pipelines associadas à Globals](https://docs.digibee.com/documentation/v/pt-br/configurations/conceitos-basicos/modify).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2Flg4def07nvsopzw47ux6%2Faa%20Modify%20and%20track%20pipeline%20deployments%20associated%20with%20Globals.mp4?alt=media&token=b888c4bd-9c88-4a22-8b93-d29b36fe1811" %}
Vídeo da feature de modificação e rastreamento de implantações de pipeline associadas à Globals
{% endembed %}

## Modos de design e debug no canvas (Beta Restrito)

O canvas agora tem dois modos: design e debug. No modo design, o fluxo é criado normalmente. Ao executar o fluxo, o modo debug é ativado e a pessoa usuária pode ver o caminho da execução, conferir os inputs e outputs de cada componente, navegar entre iterações de loops, e mais.&#x20;

Saiba mais na documentação sobre [Modos de design e debug](https://docs.digibee.com/documentation/v/pt-br/build/new-canvas-beta-restricted/design-and-debug-mode-restricted-beta).

Essa feature está em beta restrito e disponível apenas para clientes específicos. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FZybCQfDZx7nfDiXmXV1G%2FDesign%20and%20Debug%20Mode_1.mp4?alt=media&token=d97037f2-44d3-407a-a408-a0c1aa2db69c" %}
Vídeo da feature Design and debug mode no canvas
{% endembed %}

\
\


### Nós também solucionamos alguns bugs:

* **Canvas - Timestamp dos logs da execução:** solucionamos o bug em que o timestamp dos logs apareciam imediatamente após a execução com o valor três horas atrasado.&#x20;
* **Componentes - LDAP:** corrigimos o bug onde a pessoa usuária não podia listar todos os registros existentes no servidor LDAP.
* **Componentes - AES Cryptography:** corrigimos o bug que impedia a pessoa usuária de selecionar contas tipo Secret-type ao usar o componente.
* **Componentes - JSLT:** corrigimos o link para a documentação no formulário de configuração do componente



***

##

## Novidades 05/09/2023

## Componentes

* **Melhoria do Object Store (General Availability):** as mensagens de erro de configuração inválida de index do componente [Object Store](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/object-store) agora exibem o nome do object store onde o erro ocorreu. Essa melhoria facilita a identificação e solução de problemas.&#x20;
* Adicionamos o suporte a [credenciais dinâmicas](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/suporte-a-credenciais-dinamicas-beta-restrito) (Beta Restrito) ao [componente Kafka](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/kafka).&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fv2CNaKkAkKY92RqjTIyH%2Fsupport%20dynamic%20accounts_1.mp4?alt=media&token=54fa5a72-6835-46e7-8727-f2fda1c0ff59" %}
Vídeo de suporte a credenciais dinâmicas no componente Kafka
{% endembed %}

## Alertas de Monitor - Nova métrica: Execuções de pipeline por instância (Beta Restrito)

Esta métrica determina a quantidade de execuções por segundo de um pipeline por instância, e ao usá-la para criar um alerta, é possível determinar uma notificação quando essa taxa estiver fora do intervalo definido.

Note que uma **instância (ou réplica)** é a menor parte em um servidor, onde se encontram os pipelines. Quando você faz a implantação dentro da página de Run, é possível escolher quantas instâncias (réplicas) deseja implantar.

Saiba mais na [documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).

\
A feature Alertas está em fase beta restrito e disponível somente para clientes específicos. Se você deseja ter acesso a esta _feature_, entre em contato com o suporte ou com seu CSM. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).



## Alertas de Monitor - Novo canal: Slack (Beta Restrito)

Agora a pessoa usuária tem a opção de enviar alertas de notificação usando o Slack, além de e-mail, Telegram e um webhook. A pessoa usuária deve instalar o aplicativo Webhooks de entrada no Slack e ativar a opção na Digibee Integration Platform.

Saiba mais na[ documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).



A _feature_ Alertas está em fase Beta Restrito e disponível somente para clientes específicos. Se você deseja ter acesso a esta feature, entre em contato com o suporte ou com seu CSM. Entenda mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fv3OtMFDF10j5F0P3j4B9%2FPipeline%20Execution%20per%20Instance%20and%20Slack.mp4?alt=media&token=7f8d4e92-d842-4d93-953e-a6d1df0a90dc" %}
Vídeo da métrica execuções de pipeline por instância e notificações de alertas via Slack
{% endembed %}

## Novo canvas em Cápsulas (Beta)

O ambiente de criação de Cápsulas (chamado de “canvas”) recebeu uma atualização e agora dá à pessoa usuária a mesma experiência de criar um Pipeline.&#x20;

Isso significa que funções que já existiam nos pipelines agora também estão presentes na criação de Cápsulas, como, por exemplo, o [flow tree](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/pipeline-navigation#flow-tree), a [busca](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/pipeline-navigation#campo-de-busca), e a [função Linter](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/validacao-de-construcao-do-pipeline). Além disso, agora, Cápsulas e Pipelines são compatíveis e é possível copiar uma estrutura criada em um dos canvas e colar no outro.&#x20;

Saiba mais na [documentação sobre Cápsulas](https://docs.digibee.com/documentation/v/pt-br/build/capsulas).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FAGlgpCzk4kByiOCYEbw5%2FCapsule-transition-to-the-new-canvas.mp4?alt=media&token=f87d1f62-3c2a-42d1-ba0f-2493a9774e31" %}
Vídeo da transição do ambiente de criação de Cápsulas para o novo canvas
{% endembed %}



## Atualização nos botões de controle do canvas (General Availability)

Tanto em Pipelines quanto em Cápsulas, os botões de controle do canvas estão com novas cores e localizados no canto inferior direito da página. Junto com a atualização no posicionamento e design, também adicionamos um novo botão que permite abrir e fechar o minimapa a qualquer momento.\


Saiba mais sobre os [botões de controle do canvas](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/pipeline-navigation).&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2FyAldK4NVAtWqf4As5A4a%2FUpdate-in-canvas-control-buttons.mp4?alt=media&token=6e1165fc-735a-45be-aa89-92495ee80183" %}
Vídeo sobre os novos botões de controle do canvas
{% endembed %}







### Nós também solucionamos alguns bugs:

* **Canvas - Atalho minimapa:** solucionamos o bug em que o minimapa não era ocultado ao executar o atalho CTRL+Shift+M no Windows.
* **Canvas - Busca por triggers:** solucionamos o bug em que, ao buscar por um trigger dentro do canvas, o trigger não aparecia nos resultados.
* **Canvas - Abrir página inicial em nova aba:** solucionamos o bug onde não aparecia a opção de abrir a página inicial da Digibee Integration Plataform em uma nova aba ao clicar com o botão direito no logo da Digibee dentro do canvas de Pipelines e Cápsulas.
* **Componentes - Google Storage:** corrigimos o bug no componente que impedia o upload de arquivos se a pessoa usuária não tivesse a permissão para remover arquivos do bucket. Agora, a pessoa usuária pode fazer o upload através do componente, mesmo que não possua essa permissão.
* **Componentes - Lista de accounts/SOAP V3:** corrigimos o bug que impedia o acesso de contas do tipo Certificate Chain e NTLM ao usar o componente SOAP V3. Agora, essas contas podem ser acessadas corretamente.
* **Run - Atualização de informações e alertas nos cards dos pipelines:** atualizamos as informações e os alertas que aparecem nos cards, colocando um prazo para expirar após 7 dias, tendo assim um tempo limite para continuar aparecendo no card do pipeline.
