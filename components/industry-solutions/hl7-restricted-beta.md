---
description: Conheça o componente e saiba como utilizá-lo.
---

# HL7 (Beta Restrito)

{% hint style="info" %}
Atualmente, este componente está na fase beta restrito e está disponível apenas para clientes específicos.
{% endhint %}

O componente **HL7** envia informações para sistemas de _healthcare_ pelo protocolo de comunicações HL7 ([Health Level 7](https://info.hl7.org/orientation-station)), um padrão da indústria de _healthcare_ para trocar dados entre diferentes sistemas e dispositivos médicos.

Dê uma olhada nos parâmetros de configuração do componente:

* **Host:** _host_ do servidor HL7.
* **Port:** _port_ do servidor HL7. O protocolo MLLP geralmente utiliza a _port_ 2575.
* **Connect Timeout (ms):** limite de tempo para a conexão da plataforma ao servidor (em milisegundos).
* **HL7 Message:** campo da mensagem que contém os dados a serem usados. Este campo suporta expressões _Double Braces_.
* **HL7 Message Charset:** charset para a mensagem HL7.
* **Advanced Settings:** se a opção estiver ativada, você pode acessar as seguintes configurações:
  * **Connection Pool:** número de _connection pools_ disponíveis.
  * **Enable Retries:** se a opção estiver ativada, irá permitir novas tentativas se a execução falhar.
  * **Number of Retries:** define o número de novas tentativas se a execução falhar.
  * **Time to Wait Between Retries (in ms):** define o intervalo de tempo entre as tentativas (em milisegundos).
* **Fail on Error:** se a opção estiver ativada, a execução do _pipeline_ com erro será interrompida; do contrário, a execução do _pipeline_ continua, mas o resultado vai mostrar um valor falso para a propriedade "_success_".

## Fluxo de mensagens

### Saída

Ao executar um componente HL7, a seguinte estrutura JSON será gerada:

```
{
	"success":true,
	"exitCode":200
}

```

* **success:** se “true”, a operação foi executada com sucesso; se “false”, a operação falhou.
* **exitcode:** código de saída.
