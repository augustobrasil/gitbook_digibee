# Outubro

<figure><img src="../../.gitbook/assets/header_realeasenews_october.gif" alt=""><figcaption><p>Image do header de novidades ou release notes de outubro</p></figcaption></figure>

## Novidades 24/10/2023

## Nova marca da Digibee Integration Platform

Como vocês viram e sentiram, a Digibee está evoluindo e crescendo rapidamente. Com isso, o nosso website, logotipo e a nossa marca devem evoluir e crescer também. Temos o prazer de anunciar o lançamento da nossa nova identidade e marca.

Leia mais sobre [as mudanças na marca da Digibee](https://www.digibee.com/pt/news/digibee-announces-new-brand/).&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FOD1TyNFqNRyjII5xLaLh%2FRebrand%20Video_v7.mp4?alt=media&token=7e7e8b95-50d9-4766-8e69-6b038d7e066a" %}
Vídeo da nova marca e identidade visual da Digibee
{% endembed %}



## Componentes

* **Novos parâmetros para o Stream XML File Reader (General Availability):** atualizamos o componente com a adição de dois novos parâmetros: **Remove whitespaces** e **Coalesce**. Saiba mais na [documentação do Stream XML](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-xml-file-reader).
* **JSLT (General Availability):** o componente está em fase General Availability e disponível para todas as pessoas usuárias. Saiba mais na [documentação do JSLT](https://docs.digibee.com/documentation/v/pt-br/components/tools/jslt).



## Monitor — Alertas (Beta)

Nossos alertas de notificação de Monitor foram promovidos da fase Beta Restrito para Beta e estão disponíveis para todas as pessoas usuárias. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

Com essa feature, é possível **criar alertas para comportamentos inesperados com base nas métricas do pipeline**, individualmente ou por realm.&#x20;

Você ainda pode configurar para receber alertas por e-mail, [Telegram](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-telegram), [Webhook](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-through-a-webhook) e [Slack](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts/how-to-configure-alerts-on-slack).&#x20;

Saiba mais na[ documentação sobre Alertas](https://docs.digibee.com/documentation/v/pt-br/monitor/alerts).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2F5GtWcopwxQ42e6IM1ZDF%2Fmonitor%20notification%20alerts.mp4?alt=media&token=790d1200-c2cb-4cbc-a0aa-ff487b57f0a9" %}
Video da feature Alertas em Monitor
{% endembed %}



## Single Sign-On via Provedor de Identidade (Beta)

Agora, você pode configurar seu Provedor de identidade na Digibee Integration Platform. Isso permite habilitar o Single Sign-On (SSO) para fazer a autenticação de seus usuários.&#x20;

Você pode habilitar o login de três formas: apenas com o SSO, apenas pela Digibee Integration Platform ou por ambas as opções.

A Digibee Integration Platform aceita autenticação federada para gestão de grupos e permissões junto ao seu Provedor de Identidade.

Esta _feature_ está em fase Beta e disponível para todas as pessoas usuárias. Entenda mais sobre o [Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

Saiba mais na [documentação sobre Provedores de Identidade](https://docs.digibee.com/documentation/v/pt-br/administration/identity-provider-integration).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2Fe2Td4cjBZrGmvFtRl9Dd%2FIdentity%20provider.mp4?alt=media&token=5d1cbd1a-a7f9-4e55-b35f-0e643c7a6789" %}
Video da feature de single sign-on via Provedores de Identidade
{% endembed %}



## Canvas — Syntax highlight de Double Braces (General Availability)

Agora, ao usar expressões Double Braces em campos de texto do formulário de configuração de componentes que suportam Double Braces, a sintaxe do código é destacada, facilitando a leitura das expressões e a identificação de erros.&#x20;

Saiba mais sobre [Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FyEf665VHKsj7BGxMXEkj%2FDouble%20Braces%20syntax%20highlight%20(1).mp4?alt=media&token=199fb40d-7123-44df-b441-f2459a28a8cb" %}
Video da feature de destaque de sintáxe no código em double braces
{% endembed %}



## Pipeline Engine v2 — Pipeline time to First Byte (Beta Restrito)

O Pipeline time to First Byte é a nova melhoria exclusiva do Engine v2 que reduz o tempo médio de inicialização da primeira requisição do pipeline em 50% (estimado).&#x20;

Saiba mais na [documentação do Pipeline Engine v2](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine/digibee-integration-platform-pipeline-engine-v2).

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FG6acEefrsw18bA894UW5%2FPipeline%20Time%20to%20First%20Byte%20(Restricted%20Beta)_1.mp4?alt=media&token=ef880fef-c8c2-4930-b0ac-c68aa1969622" %}
Vídeo da feature de Pipeline time to fisrt byte na Engine v2
{% endembed %}







### Nós também solucionamos um bug:

* **Componentes** — **Maximum timeout para triggers:** corrigimos um bug que permitia que triggers fossem configurados com um valor de maximum timeout acima do limite.



***

## Novidades 10/10/2023

## Componentes

* **Componente Memcached (General Availability):** criamos um novo componente que usa o sistema de memória distribuída Memcached para construir integrações e fazer operações que necessitem de armazenamento temporário de dados. Saiba mais na [documentação do Memcached.](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/memcached)

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F4523BaA7JfghHEYBbLWY%2Fuploads%2Fq4FbmVecUxHWh0Hwq9B8%2Fmemcached.mp4?alt=media&token=e28840f2-6a0f-4894-a45a-aa089bdb7090" %}
Vídeo do componente Memcached
{% endembed %}



## Novo curso no Digibee Academy - Event-driven architecture - Building scalable integrations

Com o novo curso do Digibee Academy, você aprenderá a:

* Aplicar o padrão Publish-Subscribe para comunicação assíncrona nos pipelines;
* Desacoplar a técnica de transmissão de eventos para facilitar modificação, teste e implantação (manutenção);
* Aplicar princípios de escalabilidade intermediários a avançados;
* Acionar vários processos por meio de paralelismo (processamento paralelo).



## Títulos das páginas na aba do navegador

Agora, as abas do navegador mostram os títulos das páginas que a pessoa usuária está acessando na Digibee Integration Platform. Essa melhoria deixa a navegação mais fácil e intuitiva, além de aumentar a eficiência de pessoas usuárias que executam mais de uma tarefa ao mesmo tempo.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MkqXsI0cPgzRnwxNhnH%2Fuploads%2FDtr35kLTrC3VYnGLv8u3%2FPage_title.mp4?alt=media&token=cd47cd15-852c-46d2-938d-d894045bd284" %}
Vídeo da feature de títulos na aba do navegador
{% endembed %}

###

### Nós também solucionamos alguns bugs:

* **Canvas - Erro ao executar pipeline sem nenhum componente conectado:** solucionamos o bug que retornava um “error” no Painel de execução ao executar um pipeline sem nenhum componente conectado.&#x20;
* **Canvas - Página em branco ao abrir a configuração do Object Store no modo debug:** solucionamos o bug onde, ao abrir as configurações do componente Object Store dentro do modo debug, a página ficava em branco.
* **Cápsulas - Aba Parâmetros não aparece no Painel de execução da Cápsula:** solucionamos o bug onde a aba Parâmetros não aparecia no Painel de execução de uma Cápsula.
* **Componentes - Atualização de full file path:** componentes que manipulam arquivos agora são padronizados para permitir o uso do nome do arquivo (file name), ou caminho completo do arquivo (full file path) nos parâmetros especificados.
* **Componentes - SFTP:** corrigimos um bug onde, o componente sobrescrevia um arquivo quando a operação Upload era usada, mesmo se a opção “Overwrite File on Upload” não estivesse habilitada.
* **Componentes - E-mail V2:** corrigimos um bug que impedia o acesso a um provedor de contas sem autenticação ao usar o componente.
* **Componentes - For Each (Engine V2):** corrigimos um bug que afetava a configuração da rota de execução do componente.
