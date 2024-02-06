---
description: >-
  Understand Double Braces functions offered in the Digibee iPaaS and how to use
  them. Review how Date functions allow users to treat, generate and convert
  dates.
---

# Date Functions

The functions were created to:

* speed up the creation of your integrations even more
* decrease the complexity of your pipelines
* simplify data conversions and transformations during the flow of your pipelines

The date functions treat, generate and convert dates and are available for components that support Double Braces expressions. To know how to provide information to the components using this resource, click [here](./).

{% hint style="info" %}
**Important:** [check the Oracle SimpleDateFormat documentation](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html) to obtain more information about date formats and how to use it in functions such as FORMATDATE.
{% endhint %}

## FORMATDATE <a href="#formatdate" id="formatdate"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to format date and time (including the possibility of treating your _locale_ and _timezone_).

### **Syntax**

```
FORMATDATE(value, "origin-format", "destination-format", "locale-origin"?, "timezone-origin"?, "locale-destination"?, "timezone-destination"?)
```

The items included with "?" can be defined with _null_ value.

* **date format definition:** dd/MM/yyyy. It's also possible to define the 'timestamp' word only.
* the value will be always converted with ISO Zoned Date/Time.

### **Input value:**

```
{
"date": "10/10/2010 11:59:59",
"date_no_time": "30/10/2010",
"time_no_date": "11:12:13",
"timestamp_date": 1564670039000,
"date_time_utc" : "2012-10-01T09:45:00.0000000+00:00"
}
```

### **Conversion examples:**

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

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to return double value from a whole number.

### **Syntax**

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

The return of this function will be the current date in milliseconds.

## SUMDATE <a href="#sumdate" id="sumdate"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function returns the sum or subtraction of a determined date and time given a time unit.

### **Syntax**

```
SUMDATE(milliseconds:number, unit:string, value:string)
```

● **milliseconds:** timestamp

● **unit:** time unit (accepted values: hour, minute, second, day, month and year)

● **value:** date and time values to be added

● **zoneId:** zone of the informed date (standard: UTC)

The accepted zones (UTC) are:

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

Let's say you need to obtain date and time adding 10 seconds to it. You can do the following:

```
{"test": {{ SUMDATE (1599368565518, "SECOND", 10) }}}
```

The expected result will be:

```
{1599368565528}
```

## TOISODATE <a href="#toisodate" id="toisodate"></a>

By using Double Braces, you can combine the function with the access to the input JSON element of a component.

The function is applied to convert date and time to ISO Date (including the possibility to treat your _locale_ and _timezone_).

### **Syntax**

```
TOISODATE(valor, "formatSource", "formatDestination", "locale"?, "timezone"?)
```

The items included with "?" can be defined with _null_ value.

* **definition of the date format:** dd/MMMM/yyyy HH:mm:ss. It's also possible to define the 'timestamp' word only.
* If the _timezone_ isn't defined, the UTC will be used.

### **Input value:**

```
{
"date": "10/10/2010 11:59:59",
"date_with_tz": "10/10/2010 11:59:59 GMT-03:00",
"localized_date_with_tz": "10/Outubro/2010 11:59:59 GMT-03:00",
"timestamp_date": "1564670039000",
"date_no_time": "30/09/2018"
}
```

### **Conversion examples:**

```
{

"forced_utc_no_locale": {{TOISODATE(message.date, "dd/MM/yyyy HH:mm:ss", null, "UTC")}},

"inferred_tz_no_locale": {{TOISODATE(message.date_with_tz, "dd/MM/yyyy HH:mm:ss z")}},

"localized_date_with_tz": {{TOISODATE(message.localized_date_with_tz, "dd/MMMM/yyyy HH:mm:ss z", "pt-BR")}},

"date_generated_from_timestamp": {{TOISODATE(message.timestamp_date, "timestamp")}},

"iso_datetime_from_date_only": {{TOISODATE(message.date_no_time, "dd/MM/yyyy", null, "GMT-3")}}

}
```

## **DIFFDATE** <a href="#h_46970753ed" id="h_46970753ed"></a>

This function allows you to calculate the difference of time between two dates.

### **Syntax**

```
DIFFDATE(timestamp1, timestamp2, "timeUnit")
```

* The dates that will be used must be in timestamp format.
* The _timeUnit_ parameter only accept the values: _year_, _month_, _day_, _hour_, _minute_, _second_ e _millisecond_.
* The calculation applied will be: _timestamp2_ - _timestamp1_

### **Input values:**

```
{
"timestamp1": "1550458800000",
"timestamp2": "1613617200000"
}
```

### **Application examples:**

```
{

"years": {{ DIFFDATE(message.timestamp1, message.timestamp2, "year") }},

"months": {{ DIFFDATE(message.timestamp1, message.timestamp2, "month") }},

"hours": {{ DIFFDATE(message.timestamp1, message.timestamp2, "hour") }}

}
```

**Obs.:** If the function receives 2 dates that have a difference lower than 1 based on the time unit given, the result will be 0. If the _timestamp1_ parameter is greater than _timestamp2_, the function will return the negative difference.

You can also read about these functions:

* [comparison](comparison-functions.md)
* [numerical](numerical-functions.md)
* [conditional](conditional-functions.md)
* [file](file-functions.md)
* [JSON](json-functions.md)
* [string](broken-reference)
* [utilities](double-braces-utilities-functions.md)
* [math](math-functions.md)
