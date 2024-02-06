# Junho

## Novidades 06/06/2023

### COMPONENTES

* **JWT V2 (**_**General Availability**_**):** criamos uma nova versão do componente que suporta novos algoritmos JWS (_JSON Web Signature_) e JWE (_JSON Web Encryption_), além do uso de JWKs (_JSON Web Key_) ao invés de _Accounts_ nos parâmetros do componente. Saiba mais na [documentação do JWT V2](https://docs.digibee.com/documentation/v/pt-br/components/security-components/jwt-v2).\


### PROMOVENDO _PIPELINES_ IMPLANTADOS ENTRE AMBIENTES (Beta Restrito)

Agora, com apenas um clique, é possível promover um _pipeline_ implantado de um ambiente para outro de forma que ele seja implantado imediatamente. Esta _feature_ está em fase Beta Restrito, disponível para clientes específicos. Caso tenha interesse em participar, entre em contato com o seu CSM.



### HISTÓRICO DE IMPLANTAÇÃO DE _PIPELINE_ (_General Availability_)

Criamos uma nova página onde você pode encontrar o histórico de todos os _pipelines_ implantados. Além disso, cada _pipeline_ contém sua informação de histórico de implantação. A nova página está disponível para uso geral.

### &#x20;PÁGINA DE USUÁRIOS (_General Availability_)

A coluna de status na tabela de usuários agora exibe o valor “OK” para usuários que não estão arquivados e não precisam redefinir suas senhas. Antes, esse valor se chamava “Ativo”.



### INTEGRAÇÃO DE GRUPOS (_General Availability_)

Agora, as integrações de grupos arquivadas não podem mais ser editadas ou testadas.

### &#x20; CAMPO DE BUSCA NA PÁGINA DE VISÃO GERAL DE MONITOR (_General Availability_)

Adicionamos um campo de busca para te ajudar a achar _pipelines_ pelo nome ou parte do nome. Esta _feature_ estava em fase Beta e foi promovida para _General Availability_.

### &#x20; DIGIBEE ACADEMY 2.0

Nossa plataforma de e-learning foi **redesenhada** com uma interface mais intuitiva e amigável, levando a uma experiência superior e melhores resultados de aprendizagem.

Na plataforma você também encontrará:

* **Digibee AI Assistant:** uma ferramenta baseada em IA para respostas em tempo real a perguntas sobre o conteúdo da Digibee Integration Platform.
* **Nosso novo curso:** Level Up Your Pipelines Working with Files, entre muitos outros.
* **Nova seção de Webinars:** gravações de sessões ao vivo para aprimorar ainda mais suas habilidades!

[Acesse agora o Digibee Academy](https://digibee.academy/).

**Importante:** Você deve atualizar sua senha no primeiro acesso para fazer login. Mas não se preocupe, seu progresso anterior não será perdido.\


<figure><img src="https://downloads.intercomcdn.com/i/o/757129956/fe5fbce71c8c70c6cd6706f9/2023-05-17+11-12-14.gif" alt=""><figcaption></figcaption></figure>

### &#x20; NOVO CANVAS (_General Availability_)

O Novo Canvas está em _General Availability_. Além disso, agora, o “Test mode” se chama “Painel de execução” para melhor refletir todas as suas funcionalidades.

Junto com a mudança de nome da _feature_, fizemos um _redesign_ do Painel de execução para fornecer uma melhor experiência de uso e aumentar a produtividade, tornando possível:

* Parar a execução do teste a qualquer momento;
* Formatar o JSON do _payload_ para facilitar a leitura;
* Buscar pelo JSONPath tanto na aba de Teste quanto na aba de Mensagens;
* Buscar por Mensagens ou Logs;
* Ver a contagem de Mensagens e Logs;
* Fazer o download ou copiar para a área de transferência o JSON de resposta.

Para saber mais sobre as novas _features_, leia o artigo [Painel de execução](https://docs.digibee.com/documentation/v/pt-br/build/novo-canvas-beta-restrito/painel-de-execucao-beta).









Nós também solucionamos alguns _bugs:_\
\
\
\


* **Novo Canvas - Erro não é direcionado para **_**OnException**_** do componente **_**For Each**_**:** corrigimos um _bug_ que ocorria quando uma execução passava por um fluxo que possuía um componente de _Throw Error_ em um _For Each_, e o erro não era direcionado para o _OnException_ do _For Each_.
* **Novo Canvas - Fluxos do **_**Choice**_** não aparecem:** corrigimos um _bug_ que removia ramificações do _Choice_ impedindo de fazer a implantação depois.
* **Novo Canvas - Erro ao copiar componente:** corrigimos um _bug_ que não copiava e colava componentes corretamente entre _pipelines_.
* **Novo Canvas - Campo Multi-instância:** corrigimos um _bug_ na interface do campo de Multi-instância no Painel de execução.
* **Novo Canvas - Step Name não exibido:** corrigimos um _bug_ em que, às vezes, o _Step Name_ dos componentes não era exibido.
* **Seleção de versão de implantação:** corrigimos um _bug_ no campo de seleção da versão do _pipeline_ onde sua versão de implantação arquivada não é mais exibida.
* **Link quebrado na página Acessos via IdP:** corrigimos um _bug_ na página Acessos via IdP em que o link para a documentação sobre regras de autenticação redirecionava a pessoa usuária para uma página inexistente.
* **Erro ao tentar redefinir senha:** agora, se uma pessoa usuária tentar redefinir sua senha para uma senha igual a uma das últimas três senhas definidas, uma mensagem é exibida dizendo que um erro ocorreu por conta disso. Antes, uma mensagem de erro genérica era exibida.
* **Erro no teste de integração de grupos:** corrigimos um _bug_ que impedia que os testes de integração de grupos funcionassem corretamente.
