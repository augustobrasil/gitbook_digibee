---
description: Saiba mais sobre o sistema de versionamento de pipelines.
---

# Versionamento de pipelines

Os _pipelines_ da Digibee utilizam um sistema de versionamento de dois níveis. **Exemplo:** v.1.2, _Major_ = 1, _Minor_ = 2. O primeiro número em uma versão refere-se à _Major ("versão principal"),_ o segundo à _Minor ("versão secundária'')._

### Majors

Versões _Majors_ são as versões principais de um _pipeline_. Os sistema de versionamento permite criar novas versões _Major_ sem modificar as versões _Major_ geradas anteriormente. Cada versão _Major_ possui seu respectivo [Histórico de versões](historico-de-versoes-de-pipelines.md), que contém todas as versões Minors vinculadas a ela.&#x20;

Uma nova versão _Major_ só pode ser criada a partir de uma versão _Major_ já existente. Para isso, clique em **Nova versão** → **Nova versão principal** no _card_ do _pipeline_.

{% hint style="info" %}
**Nota:** Você pode implementar várias versões _Major_ de um _pipeline_ simultaneamente.
{% endhint %}

### Minors

As versões _Minor_ são as versões secundárias de um _pipeline_. Essas versões contemplam as alterações realizadas em uma mesma versão _Major_.

Por padrão, toda vez que um _pipeline_ é modificado e salvo, a Digibee Integration Platform automaticamente cria uma nova versão _Minor_.&#x20;

**Exemplo:** Se você implantar a última versão _Minor_ de um _pipeline_ e posteriormente a alterar, uma outra versão _Minor_ é gerada para que a versão implantada seja preservada.

{% hint style="info" %}
**Nota:** Você não pode implementar várias versões _Minor_ de um mesmo _pipeline_ simultaneamente.
{% endhint %}
