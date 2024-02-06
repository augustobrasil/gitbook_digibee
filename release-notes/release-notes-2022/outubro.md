# Outubro

## Novidades 25/10/2022

### **NOVO CANVAS**

Lançamos uma nova versão do Canvas, o ambiente de construção de _pipelines_ na Digibee Integration Platform. O novo Canvas traz melhorias significativas relacionadas à experiência de construção e navegação de _pipelines_, além dos seguintes recursos e funcionalidades:

* Alertas de validação durante a construção de um _pipeline_, que ajudam a identificar e corrigir problemas comuns mais rápido. Para saber mais sobre os tipos de alerta, leia o artigo [Validação de construção de pipeline](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/validacao-de-construcao-do-pipeline);
* Seta magnética, que facilita a conexão entre os componentes;
* Maior precisão ao inserir um componente ou fluxo em uma área específica do novo Canvas;
* Minimapa, que agiliza a navegação e a leitura durante a construção de um _pipeline_;
* _Auto pan_, que facilita a navegação ao arrastar componentes em _pipelines_ muito grandes.

Para saber mais, leia os artigos [Novo Canvas](https://docs.digibee.com/documentation/v/pt-br/build/novo-canvas-beta-restricted) e [Navegação em um pipeline](https://docs.digibee.com/documentation/v/pt-br/build/novo-canvas-beta-restricted/navegacao-em-um-pipeline-beta-restrito).

**IMPORTANTE:** o novo Canvas está em [Beta restrito](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta), ou seja, disponível apenas para clientes que queiram utilizá-lo em seus _realms_. Caso tenha interesse, entre em contato com seu ou sua customer success manager.

\
&#x20;

### **NOTIFICAÇÃO DE BLOQUEIO DE LOGIN**

Melhoramos a experiência de autenticação na Digibee Integration Platform. Agora, o usuário é notificado após realizar uma tentativa de login considerada suspeita.\




### **INTEGRAÇÃO DE MÚLTIPLOS **_**REALMS**_** A UM MESMO PROVEDOR DE IDENTIDADE**

A funcionalidade Integração de Provedor de Identidade com a Digibee Integration Platform agora permite que o cliente disponibilize aos seus usuários um login único para múltiplos _realms,_ a partir da mesma configuração.

**IMPORTANTE:** essa capacidade está disponível apenas para _realms_ existentes na mesma região, _cluster_ e instalação.\




### **SIMULAÇÃO DE INTEGRAÇÃO DE GRUPOS**

Agora, a _feature_ de simulação da integração de grupos está disponível. Essa _feature_ está em fase Beta e está disponível para _realms_ que já possuem a [_feature_ de integração de grupos](../../administration/identity-provider-integration/integration-of-idp-groups-with-digibee-groups/).



### DOCUMENTAÇÃO

Visando melhorar nossa documentação, criamos os artigos abaixo:

* [Problemas para fazer o login na Digibee Integration Platform](https://intercom.help/godigibee/pt-BR/articles/6618894-problemas-para-fazer-o-login-na-digibee-integration-platform)
* [Integração com provedor de identidades](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades)
* [Como integrar seu provedor de identidades](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/como-integrar-seu-provedor-de-identidades)

&#x20;

\
&#x20;\
&#x20; &#x20;

Nós também solucionamos alguns _bugs_:

**Execuções concluídas:**

* Solucionamos o bug em que o botão de busca na página de Execuções concluídas desaparecia quando o tamanho da tela do navegador era reduzido.
* Solucionamos o bug onde ao trocar o ambiente, os valores de _placeholder\*_ se sobrepunham aos valores inseridos, e o filtro de tempo assumia automaticamente o valor padrão de cinco minutos.

\*_placeholder_ é uma palavra ou frase temporariamente exibida em um campo, com o intuito de facilitar ao usuário a informação que ali deve ser inserida.





## Novidades **11**/10/2022

### **USUÁRIO COM LOGIN BLOQUEADO**

Agora, na página Usuários, o gestor de acessos pode visualizar o status “login bloqueado” para os usuários das quais as tentativas de login foram identificadas como suspeitas.

Além disso, o gestor de acessos com permissão para editar um usuário e os usuários que possuem permissão de somente leitura poderão ver o alerta de login bloqueado na aba Detalhes do usuário.



### **MONITOR**

* **Execuções concluídas**: os parâmetros de busca não serão mais apagados quando você trocar de ambiente na página de Execuções concluídas. Além disso, agora, ao clicar no botão LIMPAR, uma nova busca será feita sem os parâmetros inseridos anteriormente.



### DOCUMENTAÇÃO

Visando melhorar nossa documentação, criamos os artigos abaixo:

* [Problemas para fazer o login na Digibee Integration Platform](https://intercom.help/godigibee/pt-BR/articles/6618894-problemas-para-fazer-o-login-na-digibee-integration-platform)

&#x20;

\
&#x20;\
&#x20; &#x20;

Nós também solucionamos alguns _bugs_:

* **Movimentação de **_**pipelines**_**:** corrigimos um bug onde uma mensagem de sucesso era exibida mesmo quando havia falhas ao mover _pipelines_. Agora, se ao menos um dos _pipelines_ apresentar algum erro ao movê-lo, uma mensagem de falha será exibida, e nenhum _pipeline_ será movido. Caso todos os _pipelines_ sejam movidos corretamente, uma mensagem de sucesso será exibida.
* **Página de login:** agora, exibimos o link “Login com Provedor de Identidade” para _realms_ com autenticação integrada ativa.
* **Execuções concluídas e **_**Pipeline**_** logs:** corrigimos um _bug_ onde as URLs dessas páginas não possuíam informações sobre os parâmetros de busca usados.

\
