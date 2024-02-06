---
description: >-
  Descubra mais sobre o componente Pipeline Executor e saiba como usá-lo na
  Digibee Integration Platform.
---

# Pipeline Executor

O componente **Pipeline Executor** realiza chamadas síncronas ou assíncronas a outros _pipelines_ já implantados. Utilizando abordagem síncrona, é possível obter o resultado do _pipeline_ chamado.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões _Double Braces_](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="332">Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Operation</strong></td><td>SYNC para chamadas síncronas ao <em>pipeline</em> e ASYNC para chamadas assíncronas ao <em>pipeline</em>.</td><td>SYNC</td><td><em>String</em></td></tr><tr><td><strong>Pipeline Name</strong></td><td>Nome do <em>pipeline</em> a ser chamado.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Version Major</strong></td><td>Versão <em>major</em> do <em>pipeline</em> a ser chamado.</td><td>1</td><td>Inteiro</td></tr><tr><td><strong>Payload</strong></td><td><em>Payload</em> a ser enviado no chamado do <em>pipeline</em>.</td><td>N/A</td><td>Qualquer</td></tr><tr><td><strong>Timeout</strong></td><td>Tempo máximo de execução do <em>pipeline</em> (em milissegundos).</td><td>20000</td><td>Inteiro</td></tr><tr><td><strong>Expiration</strong></td><td>Tempo de permanência da mensagem em fila ao tentar executar o <em>pipeline</em> (em milissegundos).</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver ativada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado mostrará um valor falso para a propriedade "success".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Fluxo de mensagens

### Entrada

Não se espera nenhum _payload_ específico na entrada desse componente. A entrada será configurada dinamicamente no campo **Payload** conforme a necessidade do _pipeline_ a ser chamado.

### Saída

```
{
   "operation": "SYNC",
   "pipelineName": "pipeline-example",
   "versionMajor": 1,
   "success": true,
   "payload": {},
   "pipelineResponse": {}
}

```

* **operation:** operação selecionada, SYNC ou ASYNC.
* **pipelineName:** nome do _pipeline_ chamado.
* **versionMajor:** versão _major_ do pipeline chamado.
* **success:** se a chamada foi feita com sucesso.
* **payload:** _payload_ utilizado para chamar o _pipeline_ configurado.
* **pipelineResponse:** resposta do _pipeline_ executado. Essa propriedade é retornada apenas na operação SYNC.

## Pipeline Executor em ação

Veja abaixo como o componente se comporta em determinadas situações e como é configurado em cada caso.

### Realizando uma chamada assíncrona

**Operation:** ASYNC

**Pipeline Name:** nome do _pipeline_ a ser chamado

**Version Major:** 1

**Payload:** {}

**Timeout:** 20000

**Expiration:** 30000

**Fail On Error:** _false_

No cenário acima, será feita uma chamada assíncrona ao _pipeline_ configurado e o fluxo atual seguirá normalmente sem esperar a resposta do _pipeline_ chamado. Você poderá ver a execução e os _logs_ da chamada desse _pipeline_ na tela de _logs_ da Digibee Integration Platform.

**Saída**

```
{
   "operation": "ASYNC",
   "pipelineName": "nome do pipeline a ser chamado",
   "versionMajor": 1,
   "success": true,
   "payload": {}
}
```

### Realizando uma chamada síncrona

**Operation:** SYNC

**Pipeline Name:** nome do _pipeline_ a ser chamado

**Version Major:** 1

**Payload:** {}

**Timeout:** 20000

**Expiration:** 30000

**Fail On Error:** _false_

**Saída**

```
{
   "operation": "SYNC",
   "pipelineName": "nome do pipeline a ser chamado",
   "versionMajor": 1,
   "success": true,
   "payload": {},
   "pipelineResponse": {}
}
```

Ao realizar implantações de _pipelines_ que utilizem o **Pipeline Executor**, esteja atento às configurações de execuções simultâneas tanto no _pipeline_ de origem como no de destino, especialmente quando o parâmetro **Operation** estiver configurado com o valor SYNC.

{% hint style="info" %}
Para evitar erros de enfileiramento de chamadas e _timeout_ ao _pipeline_ de destino, é recomendável que a mesma configuração de execuções simultâneas seja adotada para ambos os _pipelines_ (origem e destino).
{% endhint %}

#### Exemplos de _Red Flags_

pipeline1(Medium) <-> pipeline2(Small)\
pipeline1(Large) <-> pipeline2(Medium)\
pipeline1(Large) <-> pipeline2(Small)

#### Limite de Execuções Simultâneas por tipo de implantação

Small - max 10\
Medium - max 20\
Large - max 40

