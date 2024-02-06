---
description: Exemplo de uso do componente.
---

# Email V1: Exemplos de uso (Descontinuado)

Digamos que você não esteja conseguindo adicionar valores ao _template_ de e-mail quando utiliza o componente _**Email V1**_.

Primeiramente, é preciso entender que o _template_ de e-mail aceita a utilização dos atributos do JSON de entrada no formato **${atributo}**. Logo, o "atributo" deve estar dentro de "params", resultando no seguinte JSON de entrada:

```
{   
    "atributo": "valorDoAtributo"
}
```

Em seguida, deve ocorrer a seguinte transformação:

```
{   
    "params": {      
        "atributo": "valorDoAtributo"   
    }
}
```

Esta seria a visualização no _template_ do e-mail:

_**Olá ${atributo}!**_

Também é possível adicionar _tags_ HTML ao _template_:

```
   <div>Olá ${atributo}!</div>
```

Dessa forma, a variável substituída no e-mail enviado seria visualizada da seguinte maneira:\
_**Olá valorDoAtributo!**_\


Clique [aqui](./) para ler o artigo completo sobre o componente _**Email V1**_.
