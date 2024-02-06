---
description: >-
  Aprenda como configurar seus fluxos de integração para alertá-lo em caso de
  erro.
---

# Como construir fluxos de integração que enviam notificações de erro

Você pode usar a aba Monitor da Digibee Integration Platform para monitorar seus fluxos de integração. No momento, não há uma funcionalidade nas páginas do Monitor para notificar os usuários quando um erro ocorre nos seus fluxos de integração, no entanto, você pode construir fluxos de integração que lhe notificam quando um erro ocorre. Aqui está como você pode fazer isso.

## Canais de notificação

Se você quiser que as notificações acerca de erros no seu fluxo de integração sejam emitidas por email, use o componente [EMAIL V2](https://docs.digibee.com/documentation/v/pt-br/components/web-protocols/email-v2) ou uma cápsula que tenha um propósito similar, como a send-email-alert. Inclua informações no corpo do email que serão úteis quando você estiver solucionando um problema, como por exemplo :

* Nome do pipeline
* Pipeline key
* Dados da requisição
* Dados da resposta
* Timestamp (data e hora nas quais o erro ocorreu)
* Parte do pipeline onde o erro ocorreu
* Código do erro

Você também pode enviar os dados do erro para um IT Service Management Tool (ITSM), como o ServiceNow ou o BMC Remedy usando um componente que se comunique com serviços externos, como o [SOAP V3](../components/web-protocols/soap-v3-beta.md) ou o [REST V2](../components/web-protocols/rest-v2.md). Se você utilizar esse método, você deve definir o conteúdo da requisição POST de acordo com o formato exigido pelo sistema escolhido.

## Como enviar alertas individuais de erros

Para enviar um alerta de erro toda vez que um erro ocorrer, adicione o componente ou cápsula escolhido, dentre os mencionados acima, aos pontos do seu fluxo de integração nos quais é provável que um erro ocorra, como por exemplo ao validar dados ou ao fazer requisições a serviços externos ou bancos de dados.

No exemplo seguinte, utilizamos um componente [EMAIL V2](../components/web-protocols/email-v2.md) para enviar uma notificação de erro toda vez que uma requisição à API REST fracassa.

Você pode usar arquitetura orientada a eventos para enviar notificações periódicas acerca de erros que aconteceram durante um certo período de tempo no seu fluxo de integração. Para fazer isso:

1. **Use o componente** [**Object Store**](../components/structured-data/object-store.md) **em seus pipelines de regra de negócio para armazenar dados de erro cada vez que um erro ocorre em seus pipelines**
2. **Crie um pipeline com um** [**Schedule Trigger**](../components/triggers/scheduler-trigger.md) **que recupera os dados de erros do banco de dados do Object Store e os envia como uma notificação**

Se você quiser enviar os dados de erros como um arquivo CSV, siga esses passos:

1. **Usando o componente** [**Object Store**](../components/structured-data/object-store.md)**, faça uma requisição ao banco de dados responsável por armazenar dados de erro**
2. **Adicione um componente** [**JSON Generator** ](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-generator)**para armazenar a propriedade “data” (dados) do output da requisição**
3. **Converta os dados para o formato CSV usando o componente** [**JSON to CSV V2**](../components/tools/json-to-csv-v2.md)
4. **Salve o arquivo CSV usando o componente** [**File Writer**](../components/files/file-writer.md)
5. **Envie o arquivo CSV como um anexo usando o componente** [**EMAIL V2**](../components/web-protocols/email-v2.md)
