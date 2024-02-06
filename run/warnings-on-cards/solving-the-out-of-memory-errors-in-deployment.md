---
description: >-
  Saiba mais sobre as possíveis causas de erros de “Out of memory” na
  implantação de pipeline e como corrigi-los com base no tipo de erro.
---

# Solucionando erros de “Out of memory” na implantação

Ao implantar um _pipeline_, alguns dos erros mais comuns que podem ocorrer é a falta de memória, “_Out of memory”_. Este artigo é principalmente sobre como identificar corretamente o erro e corrigi-lo.

## Identificando os erros de _Out of memory_ <a href="#h_db3c123681" id="h_db3c123681"></a>

O erro “_Out of Memory”_ ocorre quando o _pipeline_ tenta consumir mais memória do que foi alocada durante a implantação.

A primeira etapa para resolver esse problema é encontrar sua causa analisando os _logs_ de execução do _pipeline_ com falha. Pode ter ocorrido uma sobrecarga de memória no _pipeline_ por:

* fazer consultas em uma grande quantidade de dados sem paginação em uma solicitação _HTTP_, um banco de dados ou ao baixar e ler um arquivo na memória;
* executar muitas execuções simultâneas;
* usando o componente _Session Management_ para armazenar dados e não limpá-lo após a leitura.

{% hint style="info" %}
**Nota:** Verifique a data da última implantação. Se for mais antigo que a última versão, execute uma reimplantação para atualizar o _pipeline_.
{% endhint %}

## Corrigindo os erros <a href="#h_50d5c5a0ad" id="h_50d5c5a0ad"></a>

Agora que você já sabe como identificar o que pode estar causando os erros listados anteriormente, saiba como resolver cada problema com uma ação específica.

### Atualize o _Pipeline Engine_ para a versão mais recente <a href="#h_ea6971c9d7" id="h_ea6971c9d7"></a>

Para atualizar [_Pipeline Engine_](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine) para uma possível nova versão, a primeira coisa que você precisa fazer é reimplantar o _pipeline_ (reciclagem do _pipeline_). [Para obter mais informações, consulte Reimplantando um _pipeline_](https://docs.digibee.com/documentation/v/pt-br/run/reimplantando-um-pipeline).

Isso pode acontecer porque a _Digibee Integration Platform_ atualiza regularmente sua infraestrutura. Parte desta atualização é reciclar os computadores que oferecem suporte à infraestrutura. [Saiba mais sobre reciclagem de _pipelines_ em Alerta nos _pipelines_ em _Run_.](https://docs.digibee.com/documentation/v/pt-br/run/como-os-alertas-funcionam-nos-pipelines-em-run)

### Grande quantidade de dados sem paginação <a href="#h_221443454e" id="h_221443454e"></a>

Os erros de _“Out of memory”_ também podem ser resolvidos por paginação e/ou uma arquitetura orientada a eventos. A paginação permite que você processe dados em partes, em vez de tudo de uma só vez. [Para obter mais informações sobre paginação, consulte Exemplos de paginação.](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/exemplos-de-paginacao)

Implementar uma arquitetura orientada a eventos significa usar o _pipeline_ principal para recuperar dados e criar um _loop_ que passa por esses dados e chama um segundo _pipeline_ que possui um [_event trigger_](https://docs.digibee.com/documentation/v/pt-br/components/triggers/event-trigger).

Dessa forma, você divide a carga de memória e cria um fluxo de integração escalável que funciona com conjuntos de dados pequenos e grandes. [Para saber mais sobre Arquiteturas orientadas a eventos, consulte este artigo.](https://docs.digibee.com/documentation/v/pt-br/tutoriais-e-melhores-praticas/arquitetura-orientada-a-eventos)

Após os ajustes necessários no _pipeline_, reimplante novamente no ambiente de teste.

### Executando muitas execuções simultâneas <a href="#h_541d6886d1" id="h_541d6886d1"></a>

Os consumidores compartilham a memória disponível no contêiner. Ou seja, quanto mais consumidores, menos memória disponível para cada um. É recomendável adicionar novas réplicas a esse _pipeline_ para fluir o processo.

Um _pipeline SMALL_ com 2 réplicas tem o dobro do desempenho de processamento e escalabilidade e assim por diante. As réplicas não apenas fornecem mais poder de processamento e escalabilidade, mas também garantem maior disponibilidade - se uma das réplicas falhar, haverá outras para assumir. [Para obter mais informações sobre esses conceitos, consulte _Pipeline Engine_](https://docs.digibee.com/documentation/v/pt-br/plataforma/pipeline-engine#arquitetura-de-operao)_._

Após fazer os ajustes necessários no _pipeline_, reimplante-o no ambiente de teste. Se o erro persistir, aumente o Tamanho da implantação do _pipeline_.

### Não limpar o componente _Session Management_ <a href="#h_d1208234ed" id="h_d1208234ed"></a>

Limpe o componente _Session Management_ para salvar os dados depois de lê-los. Esta é uma boa prática para reduzir o risco de sobrecarga de memória e de falta de memória. Para realizar esta ação, deve-se configurar a função _DELETE_ nas operações do componente.

Assim, após o componente enviar a mensagem como resposta final, é possível limpar os dados armazenados após a leitura com a operação _DELETE_ caso este componente seja a última etapa do _pipeline_. [Para saber mais sobre o componente _Session Management_, consulte este artigo.](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/session-management)
