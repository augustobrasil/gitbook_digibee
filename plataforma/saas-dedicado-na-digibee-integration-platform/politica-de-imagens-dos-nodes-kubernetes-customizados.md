# Política de Imagens dos Nodes Kubernetes Customizados

## **Política de Imagens dos Nodes Kubernetes Customizadas**

Imagens personalizadas para nós do Kubernetes podem incluir configurações específicas, software adicional ou modificações necessárias para atender aos requisitos específicos do cliente. As imagens personalizadas podem ser criadas pelos clientes a partir de uma imagem base fornecida pelo fornecedor da nuvem ou a partir de uma imagem personalizada fornecida pelo próprio cliente.

{% hint style="info" %}
A Digibee não atua na manutenção ou criação dessas imagens customizadas e não é responsável por quaisquer problemas relacionados a elas.
{% endhint %}

Ao usar imagens personalizadas, o cliente é responsável por:

* Criar e manter a imagem personalizada.
* Atualizar e gerenciar o software e as configurações incluídas na imagem.
* Garantir a compatibilidade de imagem personalizada com a Digibee Integration Platform e seus componentes.

## **Considerações para manutenção de imagens personalizadas**

Como a Digibee não cria ou mantém imagens personalizadas, é importante que os clientes estejam cientes das possíveis implicações. Algumas considerações incluem:

* A Digibee não é responsável por problemas de desempenho, segurança ou compatibilidade resultantes do uso de imagens personalizadas.
* Os clientes devem estar cientes de que o uso de agentes de monitoramento, segurança ou outros recursos que consomem recursos adicionais podem afetar o desempenho da Digibee Integration Platform.
* A responsabilidade pela atualização, correção e manutenção geral das imagens personalizadas é exclusivamente do cliente.

{% hint style="danger" %}
É importante estar ciente de que **usar imagens personalizadas de nós do Kubernetes pode resultar em tempo de inatividade para a Digibee Integration Platform**, uma vez que ela é certificada para trabalhar em um ambiente Kubernetes padrão. Se, após uma atualização de imagem, o cliente apresentar problemas na imagem customizada, isso pode levar à perda de nós do Kubernetes e, consequentemente, gerar impactos de longo prazo na performance e disponibilidade da Plataforma.
{% endhint %}
