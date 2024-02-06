---
description: >-
  Saiba quais são as funções de data associadas aos Double Braces e como
  utilizá-las.
---

# Funções de data

As funções foram criadas para:

* acelerar ainda mais a criação das suas integrações
* diminuir a complexidade dos seus _pipelines_
* simplificar conversões e transformações dos dados durante o fluxo dos seus _pipelines_

As funções de data realizam tratamento, geração e conversão de datas e estão disponíveis para componentes que suportam expressões com _Double Braces_. Para saber como passar informações para os componentes utilizando esse recurso, clique [aqui](./).

{% hint style="info" %}
**Importante:** [confira a documentação SimpleDateFormat da Oracle](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html) para obter mais inormações sobre formatos de data e como utilizá-los em funções como FORMATDATE.
{% endhint %}

## FORMATDATE <a href="#formatdate" id="formatdate"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para formatar data e horário (incluindo a possibilidade de tratar o seu _locale_ e _timezone_).

### **Sintaxe**

{% code overflow="wrap" %}
```
FORMATDATE(valor, "formato-da-origem", "formato-do-destino", "locale-origem"?, "timezone-origem"?, "locale-destino"?, "timezone-destino"?)
```
{% endcode %}

Os itens indicados com "?" podem ser definidos com valor _null_.

* **definição de formato da data:** dd/MM/yyyy. Também é possível definir apenas a palavra 'timestamp'.
* o valor será sempre convertido com ISO Zoned Date/Time.

### **Valor de entrada:**

```
{
"date": "10/10/2010 11:59:59",
"date_no_time": "30/10/2010",
"time_no_date": "11:12:13",
"timestamp_date": 1564670039000,
"date_time_utc" : "2012-10-01T09:45:00.0000000+00:00"
}
```

### **Exemplos de conversões:**

```
{

"timezone_conversion": {{ FORMATDATE(message.date, "dd/MM/yyyy HH:mm:ss", "dd/MM/yyyy HH:mm:ss z", null, "GMT-3", null, "UTC") }},

"simple_date": {{ FORMATDATE(message.date_no_time, "dd/MM/yyyy", "MM/dd/yyyy") }},

"simple_time": {{ FORMATDATE(message.time_no_date, "HH:mm:ss", "ss:mm:HH") }},

"date_from_timestamp": {{FORMATDATE(message.timestamp_date, "timestamp", "dd/MM/yyyy HH:mm:ss")}},

"simple_date_to_timestamp": {{ FORMATDATE(message.simple_date, "dd/MM/yyyy", "timestamp") }},

"iso_date_time": {{FORMATDATE(message.timestamp_date, "timestamp", null)}} ,

"date_month_name_pt_br": {{ FORMATDATE( NOW(), "timestamp", "dd/MMMM/yyyy", null, null, "pt-BR", null) }},

"date_time_utc" : {{FORMATDATE(message.date_time_utc, "yyyy-MM-dd'T'HH:mm:ss.SSSSSSS+SS:SS", "dd/MM/yyyy HH:mm:ss")}}

}
```

## NOW <a href="#now" id="now"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para retornar o valor _double_ de um número inteiro.

### **Sintaxe**

```
NOW()
```

```
{

"now": {{ NOW() }},

"currentDate": {{FORMATDATE(NOW(), "timestamp", "yyyyMMdd", null, "GMT-3") }},

"currentTime": {{FORMATDATE(NOW(), "timestamp", "HHmmss", null, "GMT-3") }},

"tomorrow": {{ FORMATDATE( TOLONG( SUM(NOW(),86400000)), "timestamp", "yyyyMMdd") }},

"time5minBefore": {{ TOLONG( SUBTRACT( NOW(), TOLONG("300000"))) }}

}
```

O retorno dessa função será a data atual em milissegundos.

## SUMDATE <a href="#sumdate" id="sumdate"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função retorna a soma ou subtração de uma determinada data e hora dada uma unidade de tempo.

### **Sintaxe**

```
SUMDATE(milliseconds:number, unit:string, value:string)
```

● **milliseconds:** _timestamp_

● **unit:** unidade de tempo (valores aceitos: hora, minuto, segundo, dia, mês e ano)

● **value:** valores de data e hora a serem adicionados

● **zoneId:** zona da data informada (padrão: UTC)

As zonas aceitas (UTC) são:

* Australia/Darwin
* Australia/Sydney
* America/Argentina/Buenos\_Aires
* Africa/Cairo
* America/Anchorage
* America/Sao\_Paulo
* Asia/Dhaka
* Africa/Harare
* America/St\_Johns
* America/Chicago
* Asia/Shanghai
* Africa/Addis\_Ababa
* Europe/Paris
* America/Indiana/Indianapolis
* Asia/Kolkata
* Asia/Tokyo
* Pacific/Apia
* Asia/Yerevan
* Pacific/Auckland
* Asia/Karachi
* America/Phoenix
* America/Puerto\_Rico
* America/Los\_Angeles
* Pacific/Guadalcanal
* Asia/Ho\_Chi\_Minh

Digamos que você precise obter a data e hora somando à ela 10 segundos. Você pode fazer o seguinte:

```
{
"test": {{ SUMDATE (1599368565518, "SECOND", 10) }}
}
```

O resultado esperado será:

```
{
1599368565528
}
```

## TOISODATE <a href="#toisodate" id="toisodate"></a>

Utilizando _Double Braces_, você pode combinar a função com o acesso ao elemento do JSON de entrada de um componente.

A função é aplicada para converter data e horário para ISO Date (incluindo a possibilidade de tratar o seu _locale_ e _timezone_).

### **Sintaxe**

```
TOISODATE(valor, "formatSource", "formatDestination", "locale"?, "timezone"?)
```

Os itens indicados com "?" podem ser definidos com valor _null_.

* **definição do formato da data:** dd/MMMM/yyyy HH:mm:ss. Também é possível definir apenas a palavra 'timestamp'.
* Se o _timezone_ não for definido, será utilizado o UTC.

### **Valor de entrada:**

```
{
"date": "10/10/2010 11:59:59",
"date_with_tz": "10/10/2010 11:59:59 GMT-03:00",
"localized_date_with_tz": "10/Outubro/2010 11:59:59 GMT-03:00",
"timestamp_date": "1564670039000",
"date_no_time": "30/09/2018"
}
```

### **Exemplos de conversões:**

```
{

"forced_utc_no_locale": {{TOISODATE(message.date, "dd/MM/yyyy HH:mm:ss", null, "UTC")}},

"inferred_tz_no_locale": {{TOISODATE(message.date_with_tz, "dd/MM/yyyy HH:mm:ss z")}},

"localized_date_with_tz": {{TOISODATE(message.localized_date_with_tz, "dd/MMMM/yyyy HH:mm:ss z", "pt-BR")}},

"date_generated_from_timestamp": {{TOISODATE(message.timestamp_date, "timestamp")}},

"iso_datetime_from_date_only": {{TOISODATE(message.date_no_time, "dd/MM/yyyy", null, "GMT-3")}}

}
```

## DIFFDATE <a href="#h_7295ffcbca" id="h_7295ffcbca"></a>

Essa função permite que você calcule a diferença de tempo entre duas datas.

### **Sintaxe**

```
DIFFDATE(timestamp1, timestamp2, "timeUnit")
```

* As datas a serem utilizadas devem estar no formato _timestamp_.
* O parâmetro _timeUnit_ aceita apenas os valores: _year_, _month_, _day_, _hour_, _minute_, _second_ e _millisecond_.
* O cálculo aplicado será: _timestamp2_ - _timestamp1_

### **Valores de entrada**

```
{
"timestamp1": "1550458800000",
"timestamp2": "1613617200000"
}
```

### **Exemplos de aplicações**

```
{

"years": {{ DIFFDATE(message.timestamp1, message.timestamp2, "year") }},

"months": {{ DIFFDATE(message.timestamp1, message.timestamp2, "month") }},

"hours": {{ DIFFDATE(message.timestamp1, message.timestamp2, "hour") }}

}
```

**Obs.:** Se a função receber 2 datas que tenham uma diferença menor que 1 com base na unidade de tempo informada, o resultado será 0. Se o parâmetro _timestamp1_ for maior que _timestamp2_, a função retornará a diferença negativa.

Conheça também as funções:

* [de comparação](funcoes-de-comparacao.md)
* [numéricas](funcoes-numericas.md)
* [condicionais](funcoes-condicionais.md)
* [de arquivo](funcoes-de-arquivo.md)
* [de JSON](funcoes-de-json.md)
* [matemáticas](funcoes-matematicas.md)
* [de _string_](funcoes-de-string.md)
* [de utilidades](double-braces-funcoes-de-utilidades.md)
