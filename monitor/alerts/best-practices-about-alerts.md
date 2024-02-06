---
description: Aprenda boas práticas de uso de alertas, incluindo convenções de nomenclatura.
---

# Boas práticas sobre alertas

## O que são as boas práticas

As boas práticas são dicas para ajudá-lo a organizar e entender seus alertas. A lista de alertas exibe informações como o nome do alerta, o _pipeline_ e o _status_. No entanto, quando os alertas são notificados, apenas o nome é exibido. Seguindo as práticas para nomear alertas, você poderá identificar o tipo de alerta mais rapidamente.

## Práticas recomendadas para nomear alertas

Ao criar alertas, inclua as seguintes informações no nome do alerta:

* Nome do _realm_
* Nome do _pipeline_ (em uma única palavra)
* Tipo de métrica (somente as primeiras letras, por exemplo, “MEF” para “Mensagens em Fila”)
* Ambiente do _pipeline_ (test ou prod)
* Versão do _pipeline_
* Gravidade do alerta (baixo, médio ou alto)

{% hint style="info" %}
Separe cada item usando apenas hífens (-). Nenhum outro caractere é permitido.
{% endhint %}

Veja abaixo como a estrutura deve ficar e um exemplo prático:

**Estrutura:** realm-pipeline-metrica-ambiente-versao-gravidade

**Exemplo:** digibee-projetoxpto-MEF-prod-v1-médio

\
