# Fevereiro

## Novidades 23/02/2023

### NOVO CANVAS (BETA)

A performance do Novo Canvas foi melhorada! Agora, a renderização aumentou em até 82% se comparada às semanas anteriores, facilitando a abertura de pipelines, navegação entre níveis, e ações como arrastar e copiar e colar componentes.



### COMPONENTES

* **CSV to Excel:** fizemos uma melhoria no componente e agora o usuário pode definir uma senha para proteger o arquivo de saída Excel, usando os novos parâmetros "Set Password" e "Password". Leia a [documentação CSV to Excel](https://docs.digibee.com/documentation/v/pt-br/components/files/csv-to-excel) para saber mais.&#x20;
* **Zip File:** atualizamos o componente e agora o usuário pode definir um charset quando utilizar a operação "Decompress". Leia [a documentação Zip File](https://docs.digibee.com/documentation/v/pt-br/components/files/zip-file) para saber mais.
*   **Suporte NTLM para SOAP V3**: atualizamos o componente para permitir o acesso a um serviço SOAP com autenticação NTLM (NT Lan Manager). Essa opção pode ser selecionada pelo parâmetro “Account” do [SOAP V3](../../components/web-protocols/soap-v3-beta.md). Leia a [documentação sobre Contas](../../settings/accounts/) para saber mais.\
    \


    <figure><img src="https://lh4.googleusercontent.com/CBy-XSGD8dJGzS-ruh_SFO_GYRRxmL4-odWbKhXtmMWIa0oGFeg6NhutY3t34AYro1LfocmBFMGP4-GZeMxsm4fVAXb093Pzx2oPesB8KmKm5xyGEG4BYxSL8ZPZTS2mKokzkFotVYgWR-iGjpChPc0" alt=""><figcaption></figcaption></figure>

### MONITOR

### Visão geral&#x20;

*   Agora, você pode fechar o calendário do filtro de tempo específico usando o ícone X, além de clicar fora dele\


    <figure><img src="https://lh3.googleusercontent.com/sBaiNIexf1D4orULXCfudIKvsGu41TDrSKoeIwAuzn4Hq1qRovU-z9Vcw8_zcNJPGoGngqlseAQ_5RWssB-lXQh-M6hZ5EA_yNc_YGpmuYBnsbvdGYh3ZrZsIsxxGDDpqKwGt4PrY-Qv-BCiVbijQtI" alt=""><figcaption></figcaption></figure>

\


* Você também pode filtrar pipelines por nome ou palavra-chave.

**IMPORTANTE:** ao utilizar esta funcionalidade você automaticamente faz sua adesão ao programa Beta e concorda com os termos de uso. Para mais informações sobre versões beta, leia a [documentação Programa beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).\
\


<figure><img src="https://lh5.googleusercontent.com/J05tAfmThiDVlwwqOIhmR3Dv-cHobTNiAPEHQaAu8mQaQvLr9dkBUy39qIswJRLm2oGwszy4CphZyOdwbFAd-qX4uu7cCN6GFM1Cjdl8M4wySmZiUKYK9PKWHWTUN-NVfYZ5FYDwu45mJwk11hpMYlk" alt=""><figcaption></figcaption></figure>

* **Métricas de pipeline:** alteramos o comportamento do filtro de tempo específico para realizar uma nova pesquisa quando você clica em CONFIRMAR.



**DIGIBEE ACADEMY**

Adicionamos um novo botão para acessar o Digibee Academy diretamente do Canvas, no menu de ajuda, na parte superior direita da página.

<figure><img src="https://lh6.googleusercontent.com/ixBojh3I7yKXAGgfQs2cLCDE49P9zA3io5zk2FjBRlnZGlvqwKxuoLyQwfNE-RM6WzTlc68gRmpZqXxKyitNYCCh73cJFSxpyjVJCk7xcbMoefVKM1PlJf6GzCqjUJgXE9Ap4NPu1JKIIo6Vsv6OCS8" alt=""><figcaption></figcaption></figure>

### RUN

**Documentação de solução do erro de Out of Memory:** disponibilizamos junto ao alerta [Out of Memory](https://intercom.help/godigibee/pt-BR/articles/6948555-solucionando-erros-de-out-of-memory-na-implantacao) um link que leva o usuário para a documentação de causas e soluções para esse tipo de erro, ajudando a solucioná-lo mais rápido.

<figure><img src="https://lh4.googleusercontent.com/0TPEy1WE9IRTz_pu4QAMbH4mvT3yVBXnsO1w_oc19hcdGQqO5DANWHfewGBaI0E6ryK4XDLSDkypAlJFxL6DWx5a_FlCn_3rVNgx5ZNRmvl5raG0dwE-jD-EAKupaAYZJUV6nZ5jPAW-wu9zx6Sfq4g" alt=""><figcaption></figcaption></figure>

\


Nós também solucionamos alguns bugs:

* **Execuções concluídas e pipeline logs:** solucionamos o bug no filtro de tempo específico dessas páginas que fazia com que o parâmetro "de" mudasse quando o parâmetro "até" era alterado.



**Alertas de validação no Novo Canvas (Beta)**

* Solucionamos o bug onde o alerta era exibido para componentes de Session Management do tipo Global, quando deveria ser exibido apenas para os do tipo Local.
* Solucionamos o bug onde o alerta sobre problemas na construção de pipelines aparecia sobre o test mode e não em cima de seu componente.
* Solucionamos o bug onde a borda do alerta permanecia aparente mesmo após a resolução do problema durante a construção de pipelines.
* Solucionamos o bug onde o alerta para o Session Management não era exibido corretamente quando existe um componente de subnível entre diferentes Sessions.



**Novo Canvas (Beta)**

* Solucionamos o bug onde pipelines que utilizavam o trigger Scheduler e sofriam implantação, não tinham as informações da implantação mostradas em Run.
* Solucionamos o bug onde o componente Validator JSON Schema não persistia às configurações no Novo Canvas.
* Solucionamos o bug onde uma página branca era apresentada quando o usuário tentava visualizar as informações de um trigger configurado anteriormente.
* Solucionamos o bug quando um componente For Each que também tinha um componente de Throw Error em seu fluxo, sempre apresentava um erro de execução.
* Solucionamos o bug que não persistia componentes colados do Canvas antigo para o Novo Canvas.
* Solucionamos o bug que às vezes removia componentes soltos ao levar um pipeline do Canvas antigo para o Novo Canvas.
* Solucionamos o bug que impedia o componente Parallel de manter sua estrutura, causando erros de execução no pipeline.
* Solucionamos o bug que causava o recarregamento da página quando um trigger era configurado.
* Solucionamos o bug que impedia a paleta de componentes ser reaberta com o atalho CMD+P ou CTRL+P.
* Solucionamos o bug que mostrava o ícone de um trigger no lugar de uma Cápsula na estrutura do Flow Tree.
* Solucionamos o bug que às vezes removia componentes colados em um subnível.



**Cápsulas:**&#x20;

* Corrigimos o texto do botão ARQUIVAR, que mostrava de maneira errada o texto CRIAR.
* Solucionamos o bug que, durante a criação de uma Cápsula, removia parte de sua configuração ao acessar a aba de Contrato.



**Formulário de configuração de componentes:** solucionamos o bug onde os campos de checkbox dos formulários não persistiam ao salvar a configuração do componente.



**Visão geral:** solucionamos o bug que impedia a atualização dos dados nesta página quando os usuários a atualizavam.



**Pipeline metrics**

* Solucionamos o bug que impedia os usuários de selecionar datas no filtro de horário específico desta página.
* Solucionamos o bug em que os gráficos nesta página mudavam quando os usuários passavam o cursor do mouse sobre eles.
* Solucionamos o bug que fazia com que o gráfico de tempo de resposta do pipeline exibisse dados em segundos, e não em milissegundos, como mostra o título.



**Componentes**

* **RabbitMQ trigger:** solucionamos o bug que impedia o consumo de novas mensagens após erros de conexão sucessivos a um broker RabbitMQ. Essa melhoria permite que o trigger RabbitMQ libere corretamente os recursos nele alocados se houver falha de conexão com o servidor Rabbit.
* **Zip File:** solucionamos o bug que gerava um erro na descompactação de arquivos tipo .zip.

\
