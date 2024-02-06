---
description: >-
  Saiba mais sobre os termos de uso antes de utilizar as funcionalidades de IA
  oferecidas pela Digibee.
---

# Termos de uso para funcionalidades de IA

## Sobre este documento

Este documento descreve os vários recursos baseados em IA que a Digibee oferece em seus produtos e serviços. As funcionalidades de IA descritas abaixo incluem capacidades atuais e futuras. A Digibee utiliza várias soluções para treinar modelos de IA, desde modelos proprietários até LLMs de terceiros, como OpenAI. A OpenAI não usa dados enviados e gerados por sua API para treinar modelos OpenAI ou melhorar a oferta de serviços da OpenAI. Para saber mais sobre como a OpenAI usa dados para melhorar o desempenho do modelo, leia este artigo: [_How your data is used to improve model performance_](https://help.openai.com/en/articles/5722486-how-your-data-is-used-to-improve-model-performance).

Como todas as funcionalidades são baseadas em cálculos de probabilidade, não podemos garantir respostas precisas, embora nos esforcemos pela precisão. Todas as ações tomadas pelo usuário com base nas sugestões do nosso modelo ficam a critério e responsabilidade do usuário. Todos os dados utilizados para treinar os modelos criados pela Digibee ou fornecidos por subprocessadores terceirizados são anonimizados para proteger a privacidade dos usuários e empresas.

Veja abaixo como as funcionalidades de IA processam dados e treinam modelos de IA.

### AI Assistant

O AI Assistant da Digibee foi desenvolvido para melhorar a experiência do usuário, fornecendo respostas em tempo real a perguntas sobre o conteúdo do nosso extenso portal de documentação. Conteúdo adicional, como os materiais de aprendizagem do Digibee Academy, pode ser adicionado a este recurso no futuro.

O AI Assistant usa o [portal de documentação da Digibee](https://docs.digibee.com/documentation/), que já está disponível online, como base de conhecimento principal. Após uma consulta do usuário, o AI Assistant recupera informações de nossa base de conhecimento por meio de pesquisas de similaridade e depende de modelos OpenAI para gerar uma resposta final ao usuário. Nesse caso, todas as entradas de dados são fornecidas pelo usuário, o que é determinado pelo gestor do contrato do cliente, e a saída pode fornecer resultados inesperados. Nos apoiamos nas consultas dos usuários para aprimorar as funcionalidades atuais ou futuras, incluindo o conteúdo disponível em nossa base de conhecimento.

O AI Assistant já está disponível para todos os usuários e _realms_.

### Ferramentas de importação de integração

A Digibee oferece ferramentas de importação que convertem vários formatos de diferentes fornecedores em formatos legíveis pela Digibee. A ferramenta MuleSoft Translator permite a conversão perfeita do código de integração XML da MuleSoft em um arquivo JSON traduzido para executar integrações na Digibee Integration Platform. Esta ferramenta atualmente oferece suporte à tradução para os conectores mais comumente usados ​​na MuleSoft.

Para os tradutores, contamos atualmente com processos que combinam modelos proprietários e de terceiros, neste caso os da OpenAI. Toda a entrada de dados é feita pelo usuário, designado pelo gestor de contrato do cliente ou pelos funcionários da Digibee, agindo em nome do cliente com seu pleno conhecimento e consentimento.

As ferramentas de importação de integração estão atualmente em fase alfa e estão disponíveis apenas internamente.

### Gerador de Documentação de Pipeline com IA

O Gerador de Documentação de Pipeline com IA da Digibee agiliza o processo de criação de documentação abrangente para _pipelines_ de integração gerados por IA. Ele analisa os campos de configuração, mapeamento de dados, transformações, componentes e conexões do _pipeline_ para criar documentação detalhada. Esta documentação descreve o processo de integração, as transferências de dados, a lógica aplicada e as dependências, e inclui diagramas ilustrativos. Essa funcionalidade de IA reduz significativamente o tempo e o esforço necessários para criar e manter a documentação e ajuda na solução de problemas, na colaboração e na conformidade.

Para esta funcionalidade contamos com processos que combinam modelos proprietários e OpenAI. Neste caso, os dados do _pipeline_ (flowSpec) são usados ​​como dados de entrada que são processados ​​pelos nossos modelos. A solicitação é acionada pelo usuário, designado pelo gestor de contrato do cliente ou pelos funcionários da Digibee, agindo em nome do cliente com seu pleno conhecimento e consentimento.

O Gerador de Documentação de Pipeline com IA está disponível para todos os clientes que contrataram a Digibee após 27 de novembro de 2023. Caso o cliente não queira esse recurso, deverá enviar uma solicitação em nosso canal de suporte para desativar a funcionalidade. Clientes com contratos assinados antes de 27 de novembro de 2023 deverão enviar uma solicitação através do suporte para ativar a funcionalidade.

Se você quiser saber mais sobre o Gerador de Documentação de Pipeline com IA, leia nosso artigo [Documentação de pipelines com IA](../build/pipelines/pipeline-documentation-with-ai.md).

### Capacidades futuras de IA

À medida que a tecnologia de IA evolui, a Digibee planeja introduzir recursos de IA mais avançados. Nosso canvas alimentado por IA será capaz de sugerir componentes, fluxos, subfluxos, métodos de transformação e lógica com base nas fontes de dados e _endpoints_ selecionados pelo usuário. Os recursos de IA também poderiam identificar possíveis gargalos no fluxo de trabalho e fazer sugestões para otimização do desempenho, além de poder receber instruções do usuário em linguagem natural para projetar e modificar _pipelines_. Para estas funcionalidades, utilizamos apenas modelos proprietários e garantimos que não há contato com subprocessadores externos que sejam especificamente responsáveis ​​por fornecer capacidades de IA.
