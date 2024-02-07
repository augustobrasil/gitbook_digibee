# Janeiro

## Novidades 24/01/2023

### NOVO CANVAS (BETA)

* **Validação de construção de **_**pipeline**_**:** implementamos dois novos alertas de validação de construção de _pipelines_ que ajudam a identificar e corrigir problemas comuns referentes à utilização do componente [Session Management](../../components/structured-data/session-management.md) mais rapidamente. Para saber mais, leia o artigo [Validação de construção de pipeline](../../build/canvas/canvas-building-validation.md#session-management).
* **Campo de busca:** melhoramos a _feature_ de busca do novo Canvas. Agora, também é possível buscar por qualquer valor definido em qualquer campo dos formulários de configuração dos componentes utilizados no _pipeline_. Para saber mais, leia o artigo [Navegação em um pipeline](../../build/pipelines/pipeline-navigation.md#campo-de-busca-beta).

**IMPORTANTE:** ao utilizar o novo Canvas, você automaticamente faz sua adesão ao programa Beta e concorda com os termos de uso. Para mais informações sobre versões beta, leia a documentação [Programa beta](../../general/programa-beta.md).



### COMPONENTES

* **Suporte Apache Hive para DB V2 e Stream DB V3:** atualizamos nossa base de bancos de dados suportados para inclusão do Apache Hive (acesso somente por meio do _driver_ Hive JDBC Connector 2.6.17 for Cloudera Enterprise). O cliente deve entrar em contato com o time de suporte Digibee para providenciar a ativação do _driver_ JDBC licenciado. Para saber mais, leia o artigo [Bancos de dados suportados](../../plataforma/bancos-de-dados-suportados.md).

### &#x20; MONITOR

* **Visão geral:** você pode agora especificar as datas de começo e fim (incluindo horas) do relatório da página de visão geral.

<figure><img src="../../.gitbook/assets/git monitor.gif" alt=""><figcaption></figcaption></figure>

###

### DIGIBEE ACADEMY

* **Novo atalho:** agora, você pode acessar o Digibee Academy diretamente da Digibee Integration Platform. Basta clicar no botão de ajuda no canto superior direito e depois em Digibee Academy.

<figure><img src="../../.gitbook/assets/gif academy.gif" alt=""><figcaption></figcaption></figure>







Nós também solucionamos alguns _bugs_:

* **Seletor de ambiente:** solucionamos o _bug_ na página de Run que impedia de fechar o menu após a seleção do ambiente.
* _**Cards**_** com marcações de alerta na lateral:** solucionamos o _bug_ na página de Run que mostrava alerta na lateral do _card_, mesmo sem conter erro no _pipeline_.
* **Intervalo **_**auto refresh**_**:** solucionamos o _bug_ no seletor de _auto refresh_ da página de Run que sobrepunha os elementos da página.
* **Trigger Scheduler:** solucionamos o _bug_ que salvava incorretamente a configuração do Trigger Scheduler no novo Canvas.
* **JSON Transformer:** solucionamos o _bug_ que salvava incorretamente a configuração do componente JSON Transformer no novo Canvas.
* **Choice:** solucionamos o _bug_ que impedia que um _pipeline_ que continha o componente Choice fosse executado corretamente no novo Canvas.
* **Novo Canvas:** solucionamos o _bug_ que salvava incorretamente um _pipeline_ no novo Canvas e, por consequência, causava falhas no Canvas V1 após um _downgrade_.

\
