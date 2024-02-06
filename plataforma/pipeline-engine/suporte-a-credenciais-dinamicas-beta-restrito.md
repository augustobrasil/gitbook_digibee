---
description: >-
  A nova versão do Pipeline Engine fornece um novo recurso que permite a
  configuração das credenciais dinamicamente em cada execução do pipeline.
---

# Suporte a Credenciais Dinâmicas (Beta Restrito)

{% hint style="info" %}
Atualmente essa _feature_ está na fase de [Beta Restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta) e encontra-se disponível apenas para clientes específicos.
{% endhint %}

Na versão atual do Pipeline Engine da Digibee Integration Platform, a configuração das contas é feita de forma estática, não sendo possível alterá-las em _Runtime_. Isso pode atrasar processos em alguns cenários. Por exemplo: receber um certificado de um _endpoint_ e autenticar em uma API REST ou receber um _token_ de autenticação efêmero para autenticação dinâmica em um SFTP.\
\
Agora, os clientes que utilizam pipelines multiuso na Digibee Integration Platform podem alterar as configurações de suas credenciais na tela de Runtime, por meio do novo [componente Store Account.](https://docs.digibee.com/documentation/v/pt-br/components/tools/store-account-beta-restrito)

Com a nova funcionalidade, a Digibee simplifica o gerenciamento de credenciais, proporcionando maior agilidade e segurança em todas as etapas do seu fluxo de trabalho. **Agora será possível oferecer suporte a credenciais dinâmicas para clientes Digibee que usam o Engine v2.**

### **Arquitetura**

A funcionalidade de contas dinâmicas permite adaptar as configurações da conta às necessidades específicas de cada componente, maximizando a eficiência de suas integrações e processos. Esta atualização está disponível como uma nova configuração de parâmetro para os seguintes componentes da Digibee Integration Platform:

* [SAP](https://docs.digibee.com/documentation/v/pt-br/components/untitled/sap)
* [SFTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/sftp)
* [FTP](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/ftp)
* [REST v2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/rest-v2)
* [SOAP v3 ](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/soap-v3-beta)
* [DB v2](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2)
* [Kafka](https://docs.digibee.com/documentation/v/pt-br/components/queues-and-messaging/kafka)

Os novos parâmetros de configuração estão disponíveis nas documentações de cada um dos seus respectivos componentes.

{% hint style="info" %}
Para sua segurança, **nunca** armazene credenciais abertamente em qualquer lugar, nem salve-as no Object Store.
{% endhint %}

### **Como usar credenciais dinâmicas nos **_**pipelines**_

Para adicionar suas credenciais dinâmicas ao pipeline no Canvas, basta seguir estas etapas:

1. **Arraste** o componente Store Account da lista de componentes para o Canvas.
2. **Selecione** o tipo de conta que você quer registrar.
3. **Insira** as credenciais necessárias.
4. Clique **salvar** e **executar.**&#x20;

Suas credenciais agora estão disponíveis dinamicamente em cada execução de pipeline, prontas para serem referenciadas por outros conectores.

### **Como usar credenciais dinâmicas nos componentes da Digibee Integration Platform**

É muito simples usar credenciais dinâmicas em componentes:

1. **Ative** a opção **Use Dynamic Accounts** no componente desejado (consulte a lista de componentes acima).
2. **Insira** o nome da conta criada anteriormente com o componente **Store Account** no campo **Account Name.**
3. O componente agora está pronto para autenticar usando essa credencial.

### Usando Double Braces&#x20;

Para usar o escopo da conta no corpo das solicitações em componentes como REST V2 e SOAP v3, basta registrar a credencial `{{ account.custom-1.password }}` usando o componente **Store Account**. Dessa forma, você pode facilmente utilizar essas informações em suas operações.\
\
Por exemplo, uma conta do tipo BASIC foi criada usando o Store Account e o nome dado a ela foi **account-test.** Bastará informá-lo assim: `{{account.account-test-password }}.`



{% hint style="warning" %}
O uso do componente Store Account em cenários paralelos, como execução paralela ou For Each, **não é recomendado** na fase de Beta Restrito.
{% endhint %}
