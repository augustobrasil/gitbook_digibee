---
description: Aprenda a fazer o download de logs de uma execução de um pipeline.
---

# Download dos logs de execução de pipeline

{% hint style="info" %}
**Informações importantes:**

* Para acessar Download dos _logs_ de execução de _pipeline_ e usar todas as _features_ deste artigo, você precisa ter a permissão EXPORT:READ. Aprenda mais na[ documentação sobre Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).
* Os grupos padrão Support, Developers e Governance Manager já possuem a permissão, mas se preferir pode adicionar o papel de sistema ao seu grupo de acesso.
{% endhint %}

É possível fazer o download dos _logs_ de uma execução de _pipeline_ específica associada a uma chave de execução de _pipeline_ específica no formato CSV na página de **Execuções concluídas** em Monitor.

Uma **chave de execução de um **_**pipeline**_ é um identificador único de cada execução de um _pipeline_.

Para usar a _feature_, siga os passos abaixo:

1. Acesse a página de **Execuções concluídas**.
2. No ícone de caixa dentro da coluna **Ações**, clique em **Download dos logs de execução**.
3. Na caixa de confirmação (_pop-up_), clique em **Download dos **_**logs**_** da chave de execução do **_**pipeline**_ e logo em **Fazer download** para obter um arquivo CSV de até 5MB.

<figure><img src="../../.gitbook/assets/Download Logs PT.gif" alt=""><figcaption></figcaption></figure>

O arquivo CSV contém a seguinte informação:

* timestamp
* realm
* pipelineKey
* pipelineName
* logLevel
* logMessage

Agora também é possível personalizar o separador por caracteres de escolha do usuário, limitado a um caractere por vez, sendo o padrão **“;”** (ponto e vírgula). Note que quando abrir o arquivo no leitor de CSV, será necessário selecionar o mesmo separador de caractere exportado para seu funcionamento correto.
