---
description: >-
  Entenda como a Digibee Integration Platform processa as mensagens de cada
  componente em um fluxo.
---

# Processamento de mensagens

Um fluxo é uma sequência de componentes interconectados que se comunicam entre si por meio do processamento de mensagens. O processamento de mensagens entre componentes ocorre em três etapas:

* O componente recebe a mensagem do componente anterior (mensagem de **entrada**).
* O componente executa algum processamento, que pode ou não utilizar as informações da mensagem recebida.
* O componente envia a mensagem para o próximo componente (mensagem de **saída**).

As mensagens estão sempre no formato JSON.

## Exemplo

Um _pipeline_ é construído usando um [**REST **_**Trigger**_](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger), que é solicitado e passa o parâmetro recebido (`"type": "revenue"`) para o próximo componente - um [_**Object Store**_](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/object-store) chamado “Deletar tudo”. Um componente após o outro finaliza sua execução e aciona o próximo entregando a mensagem resultante do seu processamento.

<figure><img src="../../.gitbook/assets/imagem1 (1).png" alt=""><figcaption></figcaption></figure>

Se você optar por enviar mensagens apenas no formato JSON, a manipulação e a transformação serão facilitadas, independentemente de você usar componentes de transformação ou expressões de _Double Braces_. Estas expressões devem fazer referência a elementos da mensagem de entrada para produzir mensagens de saída.

Aprenda mais sobre [_Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces), uma linguagem de expressão desenvolvida pela Digibee Integration Platform.
