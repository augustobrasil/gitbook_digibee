# Setembro

## Novidades 13/09/2022

#### MONITOR

* Pipeline logs: ao realizar uma busca, os espaços em branco antes ou depois de um texto nos campos de busca desta página serão ignorados.



#### SIMULAÇÃO DE INTEGRAÇÃO DE GRUPOS&#x20;

Criamos uma nova funcionalidade, e partir de agora, os clientes que queiram ativar a autorização integrada em seus realms, conseguem testar o funcionamento das integrações de grupos Digibee com Grupos de Provedores de Identidade (IdP), simulando o login via IdP de um usuário teste.

IMPORTANTE: essa funcionalidade está em Beta restrito, ou seja, disponível apenas para clientes que tenham interesse em ativar a autorização integrada em seus realms.

Para saber mais, leia a nossa documentação sobre [como simular integrações de grupos](https://docs.digibee.com/documentation/v/pt-br/administration/integracao-de-provedor-de-identidades/integracao-dos-grupos-idp-com-grupos-digibee#como-simular-uma-integracao).

####

#### DOCUMENTAÇÃO

Visando melhorar nossa documentação, criamos o artigo abaixo:&#x20;

* [Resolução de problema de exibição do avatar do usuário](https://intercom.help/godigibee/pt-BR/articles/6545115-problema-com-a-imagem-do-avatar-do-usuario).





Nós também solucionamos alguns _bugs_:

* **Provedor OAuth:** corrigimos o _bug_ que impedia, em alguns cenários, o cadastro de novos Provedores OAuth na fase Beta.
* **Pipeline logs:** corrigimos o _bug_ onde o _timestamp_ dos _logs_ no modal de detalhes do log estava em um fuso horário diferente daquele exibido na página de _pipeline logs_. Agora, o _timestamp_ do modal foi ajustado para ser igual ao da página de _pipeline logs_.
* **Cápsulas:** corrigimos o _bug_ que impedia a ação de copiar Cápsulas entre _pipelines_ e em _pipelines_ que possuem uma Cápsula em seu fluxo quando a Cápsula não existia no _realm_ em que foi colado.
* **Cápsulas**: corrigimos o problema de uso incorreto de parâmetros por Cápsulas, especificamente quando tínhamos mais de uma Cápsula no mesmo _pipeline_ e cada uma usava configurações diferentes.
* **Parallel Execution:** corrigimos o _bug_ que impedia o uso de valores iguais na descrição do componente Parallel Execution e nas condições do componente Choice.
* **SOAP V3 (Beta):** corrigimos o _bug_ que impedia a realização de chamadas SOAP em _pipelines_ implantados.

\


