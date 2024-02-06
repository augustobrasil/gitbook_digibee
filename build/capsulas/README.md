---
description: >-
  Saiba mais sobre as Cápsulas, recurso que permite criar fluxos de integração
  que podem ser encapsulados e reutilizados na Digibee Integration Platform.
---

# Cápsulas

## O que são Cápsulas?

Cápsulas são um conjunto de componentes configurados que são encapsulados para serem reutilizados na construção de _Pipelines_. Por permitirem modularizar a lógica de negócios, fica mais fácil gerenciar, manter e atualizar partes individuais do sistema, além de diminuir o tempo de construção do _pipeline_.

É como se os componentes disponíveis na plataforma fossem átomos e as Cápsulas são moléculas que agrupam os átomos em tarefas mais complexas para resolver um problema específico.

## Como usar as Cápsulas?

Para usar uma Cápsula, siga estas etapas:

* [Crie uma coleção](how-to-use-capsules/how-to-create-a-capsule-collection/)&#x20;
* [Crie um grupo](how-to-use-capsules/how-to-create-a-capsule-group.md)
* [Configure uma Cápsula](how-to-use-capsules/how-to-configure-a-capsule.md)
* [Construa uma Cápsula](how-to-use-capsules/how-to-build-a-capsule.md)
* [Teste uma Cápsula](how-to-use-capsules/how-to-test-a-capsule.md)
* [Salve uma Cápsula](how-to-use-capsules/how-to-save-a-capsule.md)
* [Publique uma Cápsula](how-to-use-capsules/how-to-publish-a-capsule.md)

## Possíveis dúvidas sobre as Cápsulas

<details>

<summary>Quais são as soluções oferecidas pelas Cápsulas?</summary>

A essência das Cápsulas é fornecer ao mercado integrações prontas, testadas e validadas para obter uma melhor conexão interna ou externa de forma documentada. Elas permitem que uma empresa modernize sua TI e que suas empresas parceiras utilizem ofertas com segurança e simplicidade.

Por exemplo, imagine uma empresa onde existem múltiplos fluxos de dados relevantes para todas as áreas – autenticação, solicitações de clientes, consultas de inventário, entre outras. Para estes fluxos de dados é possível criar _pipelines_ que distribuem os serviços, mas também é necessário documentar, catalogar e manter o _pipeline_ implantado.

Ao fazer os fluxos de qualquer parte de um _pipeline_ mais acessíveis, você pode definir metas de negócios mais amplas. É por isso que desenvolvemos esta funcionalidade que reúne fluxos e os torna reutilizáveis ​​e auto documentados, assim como nossos componentes principais. Desta forma, os fluxos tornam-se mais fáceis de utilizar e familiares em toda a sua organização – basta consultar a paleta de componentes.

As Cápsulas contêm os componentes principais da Digibee Integration Platform, o que significa que possuem todas as funcionalidades que esses componentes oferecem.\


</details>

<details>

<summary><strong>Quem pode criar Cápsulas?</strong></summary>

As Cápsulas podem ser criadas por você, se você tiver as [permissões necessárias](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso), e também pela Digibee e seus parceiros para disponibilização para uso.

Ao criar uma Cápsula, você pode especificar os parâmetros, a documentação, a interface e também as instruções de uso. A liberdade de criar Cápsulas vem com todos esses recursos e a documentação fica no próprio componente.

</details>

<details>

<summary><strong>Posso utilizar Cápsulas no meu ecossistema de parceiros e clientes?</strong></summary>

Sim. É possível ter Cápsulas com pronta integração entre o sistema da empresa e seu parceiro. As Cápsulas também podem ser reutilizadas por outros parceiros com casos de uso semelhantes.

Por exemplo, um banco pode utilizar uma Cápsula para microcrédito com os sistemas POS (_Point of Sale_) de diferentes redes de farmácias.

</details>

<details>

<summary><strong>As Cápsulas são seguras para compartilhar meus dados confidenciais?</strong></summary>

Sim. A Digibee Integration Platform possui uma variedade de recursos para proteger seus dados em tráfego e armazenados quando somos responsáveis ​​por eles.

Como as Cápsulas estão incorporadas ao _Pipeline_ de uma organização, elas são executadas isoladamente, mesmo dentro da sua própria organização. Além disso, as Cápsulas funcionam em ambiente compartilhado e nunca individualmente.

</details>

<details>

<summary><strong>As Cápsulas são compatíveis com as necessidades de informação do meu legado?</strong></summary>

Sim. As Cápsulas consistem nos componentes _core_ da Digibee Integration Platform usados nos _pipelines_, e portanto têm todas as funcionalidades que esses componentes oferecem.

</details>

<details>

<summary><strong>As Cápsulas auxiliam na migração de sistemas para nuvem?</strong></summary>

Sim. Quando acontece a migração para a nuvem, é muito importante ter estratégias de convivência com os _on-premises_. Por exemplo, ao incorporar Cápsulas nesta estratégia, é possível desenvolver soluções que registem dados _on-premises_, na nuvem ou ambos.

Além disso, a Digibee Integration Platform possui uma ampla gama de Cápsulas disponíveis para soluções nativas em nuvem.

</details>

<details>

<summary><strong>A Digibee Integration Platform fornece suporte para expandir meu sistema de negócios com Cápsulas?</strong></summary>

Sim. A Digibee Integration Platform conta com uma equipe de Delivery especializada em Cápsulas que apoia todos os clientes na criação e desenvolvimento de projetos para qualquer empresa, incluindo a criação de Cápsulas públicas (criadas a pedido da empresa).

</details>

<details>

<summary><strong>Qual o limite de uso de Cápsulas em meus </strong><em><strong>pipelines</strong></em><strong>?</strong></summary>

A plataforma não estabelece limites quantitativos sobre os componentes que podem ser utilizados no _pipeline_, sejam eles componentes principais ou Cápsulas. Porém, o _pipeline_ possui limites, como número de execuções simultâneas, tempo limite e capacidade controlada na implantação quando SMALL, MEDIUM ou LARGE é selecionado.

</details>

<details>

<summary><strong>Por que é necessário informar um contrato de saída nas Cápsulas?</strong></summary>

Como as Cápsulas são componentes reutilizáveis ​​em _pipelines_, usamos o contrato de saída da especificação JSON Schema para garantir que _pipelines_ tenham clareza e segurança nas informações de resposta. Além disso, o contrato de saída também oferece suporte à automação de versionamento das Cápsulas.

</details>

<details>

<summary><strong>Como eu sei quais Cápsulas foram criadas pela Digibee?</strong></summary>

As Cápsulas criadas pela Digibee são marcadas com um selo de certificação (ícone de _checkmark_). Veja abaixo como identificá-las:

![Cápsula marcada com um selo de certificação da Digibee.](<../../.gitbook/assets/cápsula-certificada (3).png>)

</details>

<details>

<summary><strong>As Cápsulas podem ser publicadas para outros clientes?</strong></summary>

Não. As Cápsulas possuem um conjunto de permissões gerenciadas pela Digibee. Essas permissões determinam quais usuários podem tornar uma Cápsula pública.

</details>

<details>

<summary><strong>Os parceiros clientes podem publicar Cápsulas públicas?</strong></summary>

Não. Esta configuração ainda não está disponível, mas está em análise para possibilidades futuras.

</details>

<details>

<summary><strong>Cápsulas com a mesma funcionalidade sendo utilizadas por diferentes clientes ficam restritas?</strong></summary>

Sim. As Cápsulas são restritas à empresa específica que as utiliza.

</details>

<details>

<summary><strong>Como funciona o processo de atualização das Cápsulas em meus </strong><em><strong>Pipelines</strong></em><strong>?</strong></summary>

A Digibee Integration Platform nunca faz alterações diretas na estrutura ou informações de _pipelines_ implantados. Portanto, o uso de Cápsulas funciona com [versionamento](versionamento-de-capsulas.md).

Ao adicionar uma Cápsula ao _pipeline_, você a vincula à versão “_Major_” ou “_Minor_” da Cápsula. A versão "_Fix_" não está vinculada porque o _pipeline_ sempre obtém automaticamente a versão "_Fix_" mais recente quando uma nova implantação é feita ou quando o [Painel de execução](../new-canvas-beta-restricted/execution-panel.md) é executado na tela do _pipeline_.

Conforme mencionado na[ documentação de versionamento de Cápsulas](versionamento-de-capsulas.md), a versão "_Fix_" só é alterada se a alteração não afetar o _pipeline_. _Pipelines_ não são afetados ou atualizados por versões "_Major_" ou "_Minor_" de uma Cápsula que faz parte de sua compilação. Para utilizar esta Cápsula, um Analista de Integração responsável pelo _Pipeline_ deverá aplicá-la manualmente.

</details>

<details>

<summary><strong>Como posso controlar o acesso às Cápsulas na minha organização?</strong></summary>

Você pode usar um conjunto de permissões que permitem controlar funções específicas para gerenciar totalmente o ciclo de vida de suas Cápsulas. Leia mais na [documentação de Papéis](https://docs.digibee.com/documentation/v/pt-br/administration/new-access-control/papeis-do-controle-de-acesso).&#x20;

</details>

<details>

<summary><strong>Por que não posso usar os componentes Object Store, Digibee Storage e Relationship dentro de uma Cápsula?</strong></summary>

Esses componentes são recursos nativos do seu domínio. Portanto, eles são automaticamente autorizados para o contexto controlado da região. Como uma Cápsula pode ser criada para uso por outros domínios, não é possível autorizar o acesso aos dados desses componentes dentro da Cápsula.

</details>
