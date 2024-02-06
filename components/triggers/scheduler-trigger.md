---
description: >-
  Saiba mais sobre o Scheduler Trigger e como usá-lo na Digibee Integration
  Platform.
---

# Scheduler Trigger

Quando um pipeline é configurado e publicado com qualquer variável do **Scheduler Trigger**, é criada uma função para executar o processo em pausas predefinidas. Isso é feito seguindo uma [expressão cron](https://pt.wikipedia.org/wiki/Crontab) definida nas configurações deste tipo de trigger.

## Variáveis do Scheduler Trigger

O **Scheduler Trigger** possui 4 tipos. São elas:&#x20;

* **5-Minute Scheduler:** possui uma pré-configuração de 5 minutos. Quando você implanta um _pipeline_ com essa variável, as execuções ficam programadas para cada 5 minutos.
* **30-Minute Scheduler:** possui uma pré-configuração de 30 minutos. Quando você implanta um _pipeline_ com essa variável, as execuções ficam programadas para cada 30 minutos.
* **Midnight Scheduler:** possui uma pré-configuração para ser acionada sempre à meia-noite. Quando você implanta um _pipeline_ com essa variável, as execuções ficam programadas para meia-noite.
* **Custom Scheduler:** não possui pré-configuração, permitindo que você customize uma _cron expression_. Quando você implanta um _pipeline_ com essa variável, as execuções ficam programadas de acordo com a _cron expression_ que você especificou.

{% hint style="warning" %}
O **Midnight Scheduler** não permite configurar o fuso horário. Dessa forma, a execução acontece à meia-noite do fuso horário UTC, que pode ser diferente do seu fuso horário. Se precisar configurar o Fuso Horário, você pode usar o **Custom Scheduler** e então definir as informações de recorrência à meia-noite em seus parâmetros.
{% endhint %}

## Parâmetros&#x20;

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.



<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Cron Expression</strong></td><td>Expressão que define segundos, minutos, horas e a recorrência da execução em dias de um <em>pipeline</em>. <br><br><a href="https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html">Leia o artigo</a> para mais informações sobre o formato das expressões. <br><br><a href="http://www.cronmaker.com/;jsessionid=node0yg1luk7x2ff1wkkgg3300x42224447.node0?0">Acesse a página</a> para saber como construir as expressões.  </td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Time Zone</strong></td><td>Define sob qual <em>Time Zone</em> o <em>pipeline</em> será executado. Se nenhum <em>Time Zone</em> for definido, o padrão seguido será UTC (por exemplo, 12h UTC corresponde a 9h no fuso horário de São Paulo).</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>Tempo limite para que o <em>pipeline</em> processe informações antes de retornar uma resposta (padrão = 30000, limite = 900000). Em milissegundos. Se o processamento exceder essa duração, a execução é encerrada.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Retries</strong></td><td>Número máximo de tentativas em caso de falha na execução.</td><td>0</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>Se ativado, permite o reenvio da mensagem em caso de falha do <em>Pipeline Engine</em>. <br><br>Consulte o <a href="https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine">artigo sobre o Pipeline Engine </a>para obter mais detalhes.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Allow Concurrent Scheduling</strong></td><td>Indica se o <em>pipeline</em> deve seguir a regra, isto é, iniciar a execução mesmo que existam execuções prévias em processamento. </td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Informações adicionais sobre parâmetros

### **Allow Concurrent Scheduling**

Se um _pipeline_ estiver configurado para executar a cada 3 minutos e uma execução anterior levar 4 minutos, este parâmetro determina se a próxima execução começa ou aguarda a execução em andamento.  Nesse caso temos cenários diferentes:

* **se habilitado:** a execução seguinte acontece simultaneamente com a atual.
* **se desabilitado**: a execução seguinte, além das demais, não será iniciada até que a execução anterior seja finalizada.

## Scheduler Trigger em Ação <a href="#h_f67ca55d12" id="h_f67ca55d12"></a>

Esse _trigger_ pode ser usado em alguns casos em que é necessário buscar dados de sistemas que não têm capacidade de enviar os dados para a Digibee utilizando HTTP, REST, HTTP File, Kafka, RabbitMQ e JMS. Alguns desses cenários são:

* buscar arquivos em diretórios SFTP, FTP, S3, Google Cloud Storage, etc.;
* buscar informações diretamente em bancos de dados (nesse caso, recomendamos a utilização do componente **Stream DB** com paginação);
* executar chamadas de verificação de status em _endpoints_ da Digibee Integration Platform que não têm capacidade de sensibilizar os _pipelines_ através de _webhooks_.

Veja a seguir como o _trigger_ se comporta em determinada situação e a sua respectiva configuração:&#x20;

**Cenário: Pipeline executado a cada 30 segundos, sem sobreposição usando uma fonte de dados estática**

Observe como configurar um _pipeline_ com o **Scheduler Trigger** para ser executado automaticamente a cada 30 segundos sem que aconteça uma sobreposição de execuções. Também será configurado um _Timeout_ de 2 minutos e que siga o _Time Zone_ de São Paulo (UTC-3).

Primeiramente, crie um novo _pipeline_ e configure o _trigger_. A configuração pode ser feita da seguinte forma:

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Agora observe como configurar um [MOCK](../tools/json-generator.md) no _pipeline_ para que ele seja o provedor de dados que o _endpoint_ retorna ao final. Coloque o componente indicado, conecte-o ao _trigge_r e configure-o com o seguinte JSON:

```
{
    "data": {
        "products": [
            {
                "name": "Samsung 4k Q60T 55",
                "price": 3278.99
            },
            {
                "name": "Samsung galaxy S20 128GB",
                "price": 3698.99
            }
        ]
    }
}
```

Feito isso, a cada vez que o _pipeline_ for executado, o JSON definido como resposta será retornado automaticamente.
