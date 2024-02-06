---
description: Conheça o trigger e saiba como utilizá-lo.
---

# HL7 Trigger (Beta Restrito)

{% hint style="info" %}
Este componente está atualmente em fase beta restrito e está disponível apenas para clientes específicos.
{% endhint %}

O **HL7 Trigger** recebe mensagens no formato HL7 de sistemas _healthcare_ para a Digibee Integration Platform. O protocolo de comunicações HL7 ([Health Level 7](https://info.hl7.org/orientation-station)) é usado na indústria de _healthcare_ para trocar dados entre diferentes sistemas e dispositivos médicos. Você também pode [saber mais sobre o **componente HL7** na nossa documentação](https://docs.digibee.com/documentation/v/pt-br/components/industry-solutions/hl7-beta-restrito).

Dê uma olhada nos parâmetros de configuração do trigger:

* **HL7 Pipeline Name:** nome do _pipeline_.
* **HL7 Message Charset:** _charset_ para a mensagem HL7 recebida pelo _trigger_.
* **Maximum Timeout (in ms):** limite de tempo antes da expiração, em milisegundos.&#x20;
* **Filter from Header (MSH-3):** valor de um _header_ específico. Este campo é obrigatório e atualmente aceita apenas _headers_ MSH-3.

## HL7 Trigger em ação

### Saída

```
{
  "body": "<CONTEUDO_DA_MSG_HL7>"
}

```

Exemplo de mensagem (anonimizada):

{% code overflow="wrap" %}
```
{
  "body": "MSH|^~\\&|TESTE|SFCT|RAPP|RFCT|20080312181835||ADT^A01|0D23ACC3-17CD-4FF4-BE66-AD4A6572079E|P|2.4\rEVN|A01|20080312181835\rPID|1||722347^^^^MR||PATIENT^TEST||19581221|F|||HIGH STREET 91^^SAINT PAUL^MN^55175^USA||(123)456-78-90^^PH|(844)955-17-21^^PH\rPV1|1|I|P166^R8^B4|R|||728625^WRIGHT^AMANDA^^MD^DR\rDG1|1|I9|472|CHRONIC PHARYNGITIS AND NASOPHARYNGITIS||A"
}

```
{% endcode %}
