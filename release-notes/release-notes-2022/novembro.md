# Novembro

## Novidades 08/11/2022

### **PÁGINA DE LICENCIAMENTO**

A partir de hoje, clientes licenciados no modelo _Subscription-based_ poderão acompanhar o seu consumo de _Pipeline subscriptions_ e _Runtime Units_ (RTUs) disponíveis no _realm_ de forma simples. Entre em Ajustes e acesse o menu lateral Licenciamento para visualizar o consumo sob Meu consumo.



### **PIPELINE LOGS**

Com os novos botões adicionados, você pode limpar os parâmetros de busca ou copiar o nome do pipeline, ou _pipeline key_, para cada log exibido em apenas um clique. Além disso, ao realizar uma busca nesta página, os espaços em branco nos campos de busca serão ignorados.

&#x20;

\
&#x20;\
&#x20; &#x20;

Nós também solucionamos alguns _bugs_:

* **Pipeline Executor:** corrigimos o _bug_ que limitava a performance do _thread pool_ do Pipeline Executor para que todos os tipos de _deploy_ sejam atendidos: _small, medium_ e _large_. É importante ressaltar que para funcionamento desta correção, é necessário fazer o _redeploy_ dos _pipelines_ que tenham o componente Pipeline Executor.
* **Histórico de **_**pipelines**_**:** corrigimos o _bug_ que impedia o usuário de arquivar uma versão antiga do _pipeline_ através da página de histórico de versões do _pipeline_.
* **Novo Canvas** **(beta restrito):** corrigimos o _bug_ que apresentava uma mensagem de erro e impedia o usuário de copiar e colar uma estrutura e salvar o _pipeline_.
* **Uso de Cápsulas no novo Canvas (beta restrito):** corrigimos o _bug_ que impedia o usuário de visualizar o formulário de uma Cápsula presente em um _pipeline_ no novo Canvas.
* **Aceite de termo de licença**: corrigimos o _bug_ onde o termo de licença não era exibido para o usuário.
