---
description: >-
  Aprenda mais sobre a função Linter, que permite validar a construção de
  pipelines e cápsulas no canvas.
---

# Linter: Validação de construção do canvas

O canvas exibe alertas durante a construção de _pipelines_ e cápsulas que ajudam os desenvolvedores a identificar e corrigir problemas comuns mais rapidamente.

![](<../../.gitbook/assets/\[PT] linter-1.gif>)

## Localizar problemas

Para cada componente que apresenta um problema durante a criação do fluxo, o canvas exibe um alerta com detalhes e informações. Muitas das validações têm o propósito de aviso e não demandam correções nem são intrusivas no processo de criação do seu fluxo.

## Alertas

Os problemas validados durante a construção do _pipeline_ ou cápsula são divididos em **Erros** e **Avisos**. Essa divisão de alertas ajuda o desenvolvedor a entender o nível de gravidade do problema apontado pelo canvas.

### Erros

Os alertas de **Erro** apontam falhas graves na construção do _pipeline_ ou cápsula. Eles devem ser corrigidos ou não será possível salvar o projeto

O canvas exibe erros da seguinte categoria:

* Estrutura: erros estruturais que impedem o processamento do fluxo de integração.

### Avisos

Os alertas de **Aviso** exibem pontos de melhoria na construção do _pipeline_ ou cápsula.

O canvas exibe avisos da seguinte categoria:

* Boas práticas: hábitos de construção que tornam seu _pipeline_ ou cápsula mais saudável, e podem facilitar futuras manutenções e melhorias.

## Lista de alertas

Para cada problema encontrado durante a construção de _pipelines_ ou cápsulas, um alerta é mostrado em seu componente de origem e em uma lista. Os alertas são divididos seguindo as categorias acima e é possível visualizar quantos alertas de cada tipo há separadamente.

A partir da lista é possível:

* Visualizar a imagem e nome do componente com problema junto a uma descrição e link para a documentação com orientações sobre como resolvê-lo.
* Esconder os alertas temporariamente clicando no ícone de olho.
* Navegar entre os sub-níveis até o componente com erro clicando no ícone de alvo.
* Abrir o formulário de configuração do componente para editá-lo clicando no ícone de engrenagem.

![](<../../.gitbook/assets/\[PT] linter-2.png>)

Para visualizar a lista, clique no botão **Problemas**, representado por um ícone de alerta na barra de tarefas do lado esquerdo.&#x20;

## Corrigir problemas

Todas as validações do canvas apresentam informações que te ajudam a corrigir o problema. Passe o mouse sobre o ícone de alerta para que as informações sejam exibidas. Desse modo, você poderá lê-las e verificar a aplicabilidade de cada sugestão no seu _pipeline_ ou cápsula.

Esta página lista todos os possíveis alertas desenvolvidos até agora, contendo detalhes e informações de como você pode corrigir e aprimorar seu fluxo.

### Choice

1. **O componente Choice precisa ter um "when" configurado (estrutura)**

O **Choice** permite o desvio de fluxo dentro de um _pipeline_ ou cápsula. Para utilizar esse componente corretamente, é necessário configurar suas condicionais "_**when**_". Cada _**when**_ define uma condição que realiza um desvio no fluxo para uma linha de execução específica. É necessário ter pelo menos 1 condição _**when**_ configurada.

Desse modo, defina pelo menos uma condição _**when**_ para evitar a interrupção do fluxo.

2. **O componente Choice precisa ter um "otherwise" configurado (estrutura)**

O **Choice** permite o desvio de fluxo dentro de um _pipeline_ ou cápsula. Para utilizar esse componente corretamente, é necessário configurar seu comando "_**otherwise**_". O _**otherwise**_ é o comando a ser executado quando nenhuma das condições _**when**_ é atendida. É necessário ter 1 condição _**otherwise**_ configurada.

Portanto, defina o comando _**otherwise**_ a ser executado caso nenhuma das condições _**when**_ for considerada verdadeira.

### Componentes de subfluxo

Os seguintes problemas se referem aos componentes que permitem a estruturação de[ _subpipelines_](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/subpipelines), ou seja, subfluxos do _pipeline_ ou cápsulas. _Subpipelines_ são estruturados a partir dos seguintes componentes:

* ​[Block Execution](https://docs.digibee.com/documentation/v/pt-br/components/logic/block-execution)​
* ​[Do While](https://docs.digibee.com/documentation/v/pt-br/components/logic/do-while)​
* ​[For Each](https://docs.digibee.com/documentation/v/pt-br/components/logic/for-each)​
* ​[Retry](https://docs.digibee.com/documentation/v/pt-br/components/logic/retry)​
* ​[Stream Excel](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-excel)​
* ​[Stream File Reader](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-file-reader)​
* ​[Stream File Reader Pattern](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-file-reader-pattern)​
* ​[Stream JSON File Reader](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-json-file-reader)​
* ​[Stream XML File Reader](https://docs.digibee.com/documentation/v/pt-br/components/files/stream-xml-file-reader)​​
* ​[Stream DB V3](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stream-db-v3)​

1. **O OnProcess precisa ter ao menos um componente conectado (estrutura)**

O OnProcess define um dos subfluxos do pipeline. Estruture e conecte o _subpipeline_ OnProcess para que o fluxo não seja interrompido.

2. **O OnException precisa ter ao menos um componente conectado (boas práticas)**

O OnException é o _subpipeline_ onde é implementado o fluxo que trata uma exceção na execução do OnProcess. Estruture e conecte o subfluxo OnException para que o fluxo não seja interrompido.

{% hint style="info" %}
Essa regra não se aplica ao componente Block Execution.
{% endhint %}

3. **Existe ao menos um problema dentro de OnProcess (estrutura)**

O OnProcess define um dos subfluxos do _pipeline_ ou cápsula. Verifique os problemas do _subpipeline_ OnProcess para prosseguir com a criação do seu fluxo.

4. **Existe ao menos um problema dentro de OnException (estrutura)**

O OnException é o _subpipeline_ onde é implementado o fluxo que trata uma exceção na execução do OnProcess. Verifique os problemas do subfluxo OnException para prosseguir com a criação do seu _pipeline_ ou cápsula.

### Parallel

1. **O componente Parallel precisa ter ao menos uma execução configurada (estrutura)**

O **Parallel** permite a configuração de linhas de execução paralelas dentro do fluxo. Conecte o **Parallel** a outro componente para evitar a interrupção do fluxo.

{% hint style="info" %}
O **Parallel** deve ser sempre seguido por outro componente para que o fluxo possa ser executado.
{% endhint %}

2. **O componente Parallel deve ter ao menos duas execuções configuradas (boas práticas)**

O **Parallel** permite a configuração de uma ou mais linhas de execução paralelas dentro do fluxo. Como boa prática, recomendamos que utilize o **Parallel** apenas quando seu fluxo precisar de duas execuções ou mais ocorrendo simultaneamente.

### Triggers

1. **Trigger não configurado. Para implantar o pipeline, configure o trigger (estrutura)**

O _trigger_ define como a execução do _pipeline_ será iniciada. Para configurar o _trigger_, selecione uma das opções disponibilizadas pela Digibee Integration Platform. A seguir, conecte-o ao início do fluxo para implantar o _pipeline_ posteriormente. Para mais informações, acesse a [documentação dos _triggers_](https://docs.digibee.com/documentation/v/pt-br/components/triggers).​

{% hint style="info" %}
Você pode salvar o pipeline mesmo sem configurar o trigger. No entanto, não será possível implantá-lo.
{% endhint %}

### Componentes descontinuados

1. **Versão do componente descontinuada. Existe uma versão nova deste componente (boas práticas)**

A versão do componente que você está tentando utilizar foi descontinuada. Isso significa que há uma nova versão incrementada e melhorada disponível para uso.

**Exemplo:** O componente **SOAP** possui três versões, [**SOAP V1**](https://docs.digibee.com/help-center/v/pt-br/components/web-protocols/soap-v2/soap-v1), [**SOAP V2**](https://docs.digibee.com/help-center/v/pt-br/components/web-protocols/soap-v2) e [**SOAP V3**](https://docs.digibee.com/help-center/v/pt-br/components/web-protocols/soap-v3). Recomendamos a versão mais atual do componente, a **SOAP V3**.

{% hint style="info" %}
A versão descontinuada do componente ainda pode ser utilizada. No entanto, é importante informar que incrementos e melhorias são feitos na última versão do componente.
{% endhint %}

### Cápsulas

1. **Esta Cápsula não pode ser usada aqui porque ela não existe neste realm (estrutura)**

A cápsula que você está tentando utilizar não existe no _realm_ no qual você está operando. Você precisa apagá-la ou substituí-la por outro componente, fluxo ou uma cápsula existente neste realm.

### Session Management

1. **O campo não foi declarado anteriormente (boas práticas)**

Não foi possível utilizar o campo (operação GET) porque o mesmo não foi declarado (operação PUT) anteriormente.

2. **O campo foi declarado, mas não está sendo usado (boas práticas)**

O campo foi declarado anteriormente (operação PUT), mas não está sendo utilizado.

Configure um novo componente **Session Management** para utilizar (operação GET) ou deletar (operação DELETE) o campo declarado anteriormente.
