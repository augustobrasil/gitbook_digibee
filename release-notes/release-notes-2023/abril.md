# Abril

## Novidades 18/04/2023

### COMPONENTES <a href="#undefined" id="undefined"></a>

* **Raw SQL Statement para DB V2 e Stream DB V3:** uma atualização nos componentes permite executar _queries_ dinâmicas por meio de _Double Braces_. Ao usar essa _feature_, é importante tomar as medidas de segurança necessárias para evitar instruções SQL indesejadas. Para saber mais, leia as documentações do [DB V2](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/db-v2) e [Stream DB V3](https://docs.digibee.com/documentation/v/pt-br/components/structured-data/stream-db-v3).
* **HL7 (Beta restrito):** criamos um novo componente que envia informações para sistemas de informação em saúde pelo protocolo de comunicações HL7 (Health Level 7), um padrão da indústria para troca de dados entre diferentes sistemas e dispositivos médicos. Atualmente, o componente está em [Beta restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta#h\_d59e60e1bd), disponível apenas para alguns _realms_. Para saber mais, leia a [documentação do HL7](https://docs.digibee.com/documentation/v/pt-br/industry-solutions/hl7-beta).

## HISTÓRICO DE IMPLANTAÇÃO DE _PIPELINE_ (Beta Restrito) <a href="#undefined" id="undefined"></a>

Criamos uma nova página onde você pode encontrar o histórico de todos os pipelines implantados. Além disso, cada pipeline contém sua informação de histórico de implantação. A página está em [Beta Restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta#h\_d59e60e1bd) e disponível apenas para alguns _realms_.









Nós também solucionamos alguns _bugs_ e implantamos as seguintes melhorias:

**MONITOR**

* Atualizamos os elementos visuais de interface na página de Visão geral.\


**INTEGRAÇÕES DE GRUPO (Beta)**

* Adicionamos a _tag_ "Beta" na página Integrações de grupo para indicar que esta _feature_ está liberada para todos os _realms_, e está em fase de melhoria. Saiba mais sobre o [programa Beta da Digibee aqui](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).

**NOVO CANVAS**

* **Linter** - alertas de validação: solucionamos o _bug_ que exibia um alerta no componente Session Management de maneira incorreta quando uma variável era declarada em um nível e utilizada em outro, dependendo do componente que antecedia o Session.
* **Busca no Novo canvas:** solucionamos o _bug_ que não retornava resultados quando o termo estava em um componente Choice ou Parallel.
* **Remoção de componentes:** solucionamos o _bug_ que permitia um componente ser removido e voltar ao menu Build sem confirmar as alterações no _pipeline_ e, sem de fato, remover o conteúdo.
* **Copiar componentes:** solucionamos o _bug_ que não permitia copiar componentes se o nome do _pipeline_ fosse copiado anteriormente.
* _**Trigger**_** com **_**ratelimit**_**:** solucionamos o _bug_ que mostrava uma página branca ao tentar abrir um _pipeline_ que continha um _trigger_ com _ratelimit_ configurado.
* **Paleta de Cápsulas:** solucionamos o _bug_ que não respeitava a quebra de linha da paleta de Cápsulas.\
  \

* **Contas** **do tipo OAuth 2:** solucionamos o _bug_ que permitia a criação de contas do tipo Oauth 2, mas não criava o token necessário para o uso nos _pipelines_, que posteriormente mostravam o erro _Nullpointer Exception_.











## Novidades 04/04/2023

### COMPONENTES <a href="#undefined" id="undefined"></a>

* _**Rate Limit**_** para triggers REST, HTTP e HTTP File:** uma atualização nos triggers permite alterar configurações de _Rate Limit_. Essa opção é útil para definir um limite de requisições feitas na API do usuário em um intervalo de tempo. Para mais informações, visite as documentações de [REST Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/rest-trigger), [HTTP Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-trigger) e [HTTP File Trigger](https://docs.digibee.com/documentation/v/pt-br/components/triggers/http-file-trigger).

### NOVO CANVAS (Beta) <a href="#undefined" id="undefined"></a>

* **Linter - Lista de Problemas:** agora o Novo Canvas conta com uma lista de todos os alertas (problemas e alertas) gerados pelo seu _pipeline_.\
  É possível navegar pelos componentes com alertas através da lista, esconder os alertas para otimizar a visualização do seu _pipeline_, e abrir o formulário de configuração dos componentes para uma edição mais rápida.\
  Também é possível saber exatamente quantos problemas e alertas foram gerados e onde eles se localizam dentro do fluxo. Saiba mais na [documentação sobre alertas de validação](../../build/new-canvas-beta-restricted/validacao-de-construcao-do-pipeline.md#h\_303cf6c6b1).

<figure><img src="https://lh6.googleusercontent.com/BQKwDs6aD3IdwdI_SIGTbCwdpXCA0VnbDUGyVdNsJoaWKjhFtndWuaTf459-MoCPu-JTL4EVgZ2rQzpT86SVnDnUUotMRx3CSo_Y15I3wF8F8TpNNtw8peae_jwqvKTPUXrPkIecAq60g_yYaX5XGYU" alt=""><figcaption></figcaption></figure>

* **Visualização do mini mapa:** desenvolvemos um atalho para esconder o mini mapa do Novo Canvas, otimizando assim a visualização de _pipelines_. Agora, utilize CTRL/CMD + SHIFT + M para alternar a visualização do Canvas com ou sem o mini mapa.









Nós também solucionamos alguns _bugs_:

**Novo Canvas (Beta):**

* Solucionamos o _bug_ que impedia o nome do pipeline de ser copiado usando CTRL + C.
* Solucionamos o _bug_ que não redirecionava o usuário à aba da Build ao clicar no ícone da Digibee.
* Solucionamos o _bug_ que impedia o pipeline de ser organizado utilizando o atalho CTRL + O.





.
