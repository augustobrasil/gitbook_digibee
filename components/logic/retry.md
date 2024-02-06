---
description: >-
  Descubra mais sobre o componente Retry e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Retry

O **Retry** permite novas tentativas de execução de passos definidos em um _subpipeline_**.**

## Parâmetros

Dê uma olhada nos parâmetros de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="296">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Maximum Number of Retries</strong></td><td>Número máximo de tentativas. A primeira tentativa também conta, então se o passo falhar na primeira execução e você deseja que seja feita uma nova tentativa, o valor nesse parâmetro deve ser igual a 2.</td><td>3</td><td>Inteiro</td></tr><tr><td><strong>Timeout Of The Whole Retry Operation</strong></td><td>Duração máxima da soma de todas as tentativas, incluindo a primeira (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>se a opção for ativada, a execução do <em>Retry</em> que atingir o número máximo de tentativas ou a duração máxima, terminará com erro e será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado da última tentativa será entregue ao próximo componente.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Definindo o subpipeline que é executado a cada tentativa <a href="#h_4da0771299" id="h_4da0771299"></a>

Para trabalhar com esse tipo de componente, é importante levar em consideração:

* **Subpipeline definido em onProcess:** _subpipeline_ a ser executado a cada nova tentativa.
* **Subpipeline definido em onException:** _subpipeline_ a ser executado sempre que uma tentativa resultar em falha.

Para entender melhor o funcionamento de _subpipelines_, leia a [documentação _Subpipelines_](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/subpipelines).

{% hint style="warning" %}
A cada nova tentativa, o primeiro passo do _subpipeline_ definido em _onProcess_ recebe a mensagem de saída do último passo processado. Portanto, dados a serem reutilizados nas novas tentativas devem ser devidamente tratados para que possam ser acessíveis durante as novas tentativas (exemplo.: manipulação dos dados através de componentes Session).
{% endhint %}

### Informando sucesso para uma execução do componente Retry <a href="#h_9121c6196f" id="h_9121c6196f"></a>

O **Retry** espera que uma propriedade `success` com o valor `true` seja informada no último passo do _subpipeline_ para que a execução seja considerada bem sucedida. Se um erro ocorrer ou se a propriedade `success` for informada com o valor `false` ou for inexistente, o **Retry** entenderá que uma nova tentativa deverá ser executada.

## Fluxo de mensagens <a href="#h_81aedec92e" id="h_81aedec92e"></a>

### Entrada <a href="#h_8d4b07ca16" id="h_8d4b07ca16"></a>

Qualquer estrutura é aceita.

### Saída <a href="#h_04df5cd8db" id="h_04df5cd8db"></a>

Mensagem de saída do último passo processado.

## Tratamento de Erros <a href="#h_a3bc434e27" id="h_a3bc434e27"></a>

Quando um erro ocorre durante o processamento do _subpipeline_ em _onProcess_, o _subpipeline_ em _onException_ será invocado se estiver definido.

No _onException_, é possível:

* ter acesso aos detalhes do erro que ocorreu durante o processamento da última tentativa.
* definir se o **Retry** continua as tentativas, informando uma propriedade `success` com o valor `false` ou não a definindo. Caso a propriedade `success` seja especificada com o valor `true`, então o **Retry** será finalizado com sucesso e nenhuma outra tentativa será executada.

## Cenários de utilização do componente Retry com tratamento de erros <a href="#h_a1cba176b1" id="h_a1cba176b1"></a>

### Propriedade Fail on Error habilitada e nenhum subpipeline definido em onException <a href="#h_200edda8f2" id="h_200edda8f2"></a>

* o _pipeline_ será interrompido após todas as tentativas;
* um erro será emitido a partir do componente **Retry**;
* nenhum outro componente será invocado após o **Retry**.

### Propriedade Fail on Error habilitada e um subpipeline definido em onException <a href="#h_389b2ed99a" id="h_389b2ed99a"></a>

* o _pipeline_ será interrompido após todas as tentativas;
* o _subpipeline_ definido em _onException_ será executado após cada tentativa;
* um erro será emitido a partir do componente **Retry**;
* nenhum outro componente será invocado após o **Retry**.

### Propriedade Fail on Error desabilitada e nenhum subpipeline definido em onException <a href="#h_a006162471" id="h_a006162471"></a>

* o _pipeline_ não será interrompido após todas as tentativas;
* nenhum erro será emitido a partir do componente **Retry**_;_
* o próximo componente será invocado recebendo a mensagem de saída do **Retry**.

### Propriedade Fail on Error desabilitada e um subpipeline definido em onException <a href="#h_aad3137ee2" id="h_aad3137ee2"></a>

* o _pipeline_ não será interrompido após todas as tentativas;
* o _subpipeline_ definido em _onException_ será executado após cada tentativa;
* nenhum erro será emitido a partir do componente **Retry**_;_
* o próximo componente será invocado recebendo a mensagem de saída do **Retry**_._

{% hint style="warning" %}
Caso um componente de erro (como Throw Error ou Assert) seja utilizado dentro do _subpipeline_ em _onProcess_ ou um erro ocorra, então o Retry será finalizado e o erro será propagado para o _pipeline_. Além disso, sempre que a propriedade `success` for definida com valor `true` no último passo do _subpipeline_ em _onException_, a execução do componente Retry também será concluída, independentemente da propriedade Fail on Error estar ativa.
{% endhint %}
