---
description: >-
  Saiba mais sobre o Canvas, ambiente de construção de pipelines da Digibee
  Integration Platform que permite o rápido desenvolvimento de integrações
  simples e complexas.
---

# Canvas

O Canvas é o ambiente de construção de _pipelines_ da Digibee Integration Platform. Através dele, você consegue desenvolver integrações simples ou complexas arrastando e soltando componentes pré-configurados com rapidez e precisão.

## Configurações do _pipeline_

Para criar seu pipeline, acesse a página _Build,_ clique em **Criar**, e selecione a opção _**Pipeline**_.

Antes de partir para a construção do fluxo, é preciso configurar o _pipeline_. Para isso, clique no botão **Configurações** representado pelo ícone de engrenagem no canto superior direito do Canvas.

No formulário **Configuração do **_**pipeline**_, se necessário, configure os seguintes campos:

* **Descrição**: descrição do _pipeline_.
* **“É multi-instância?”**: ative esta opção caso o _pipeline_ a ser criado seja multi-instância. Para saber mais sobre essa funcionalidade, leia o [artigo Multi-instância](https://docs.digibee.com/documentation/v/pt-br/configurations/multi-instancia).
* **Campo sensível:** campos de dados que devem ser ofuscados nos [_logs_ do _pipeline_](../../monitor/pipeline-logs.md) com o conjunto de caracteres "\*\*\*". O caractere especial hífen \[-] é permitido no nome do campo sensível. Outros caracteres especiais, acentos e cedilha \[ç] não são permitidos.&#x20;

{% hint style="info" %}
Se você configurar campos sensíveis na configuração do _pipeline_, eles se aplicam apenas a este _pipeline_ específico. Se deseja configurar campos sensíveis para todos os _pipelines_ no seu _realm_, por favor, consulte a documentação da [Política de campos sensíveis](../../governance/policies/sensitive-fields.md).
{% endhint %}

* _**InSpec**_**:** entrada do fluxo do _pipeline_.
* _**OutSpec**_**:** saída do fluxo do _pipeline_.

<figure><img src="../../.gitbook/assets/01 - Pipeline Configuracao.jpeg" alt="Formulário de configuração do pipeline com campos específicos para configurar o pipeline. "><figcaption></figcaption></figure>

Após configurar o _pipeline_, você poderá partir para a construção do fluxo.

## Crie um fluxo

Todo _pipeline_ é composto por um _trigger_ e por pelo menos um componente, que devem ser conectados entre si para que possam estabelecer um fluxo de integração. No Canvas você consegue organizar e configurar o _trigger_ e os componentes do seu _pipeline_ de acordo com a sua necessidade de negócio.

### _Trigger_ <a href="#h_d80b42e462" id="h_d80b42e462"></a>

O primeiro passo para criar um fluxo é escolher um _trigger_. O _trigger_ é o elemento que define como a execução do _pipeline_ será iniciada - através de uma chamada externa, em resposta a um evento ou via agendamento, por exemplo.&#x20;

Para defini-lo, passe o mouse sobre o _trigger_ e clique no botão **Configurações** representado pelo ícone de engrenagem. Escolha entre as opções listadas e configure o _trigger_.

<figure><img src="../../.gitbook/assets/02 - Trigger port.gif" alt="Lista de triggers disponíveis para configurar. "><figcaption></figcaption></figure>

Depois que configurar o _trigger_, clique em **Confirmar** para salvar as alterações.

{% hint style="warning" %}
Se você fechar a janela antes de clicar em **Confirmar**, todas as alterações serão perdidas.
{% endhint %}

### Componentes <a href="#h_eadc6e7b3f" id="h_eadc6e7b3f"></a>

Os componentes representam etapas do fluxo e são escolhidos de acordo com as suas necessidades de negócio. Combine todas as etapas do processo de integração que deseja realizar utilizando a lista de componentes à direita do Canvas.

<figure><img src="../../.gitbook/assets/03 - Componentes.gif" alt=" Componentes arrastados para o fluxo e conectados um ao outro."><figcaption></figcaption></figure>

Para excluir uma linha conectora ou um componente específico do fluxo, clique no botão **Remover** representado pelo ícone de lixeira e confirme clicando novamente no ícone de **X**.

<figure><img src="../../.gitbook/assets/04 -.gif" alt="Conexão entre componentes sendo deletada do fluxo. "><figcaption></figcaption></figure>

Para configurar o componente a ser utilizado, clique no botão **Configurações** representado pelo ícone de engrenagem para acessar o formulário de configuração.

No exemplo abaixo, é possível visualizar o formulário do [componente Google Drive](../../components/file-storage/google-drive.md).

<figure><img src="../../.gitbook/assets/05 - Google drive port.gif" alt="Formulário para configurar o componente Google Drive."><figcaption></figcaption></figure>

​Depois que configurar o trigger, clique em **Confirmar** para salvar as alterações.

{% hint style="warning" %}
Se você fechar a janela antes de clicar em **Confirmar**, todas as alterações serão perdidas.
{% endhint %}

Para saber mais a respeito de cada componente disponível em nossa lista, acesse a nossa [documentação de Componentes](https://docs.digibee.com/documentation/v/pt-br/components/).

### Documentação de componentes e _triggers_

Componentes e _triggers_ têm um campo chamado _**Documentation**_ no final do seu formulário de configuração. Você pode usar esse campo para explicar o propósito do componente ou _trigger_, ou adicionar qualquer outra informação que possa ser útil para o projeto. O campo _**Documentation**_ ajuda com resolução de problemas e colaboração do time.

### Navegação em um _pipeline_ <a href="#h_497047ccf4" id="h_497047ccf4"></a>

Além das funcionalidades apresentadas neste artigo, o Canvas conta com outras relacionadas à experiência de navegação no _pipeline_. Para saber mais, leia o artigo [Navegação em um _pipeline_](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/navegacao-em-um-pipeline-beta-restrito).

### Validação de construção do _pipeline_ <a href="#h_3e6ea3319e" id="h_3e6ea3319e"></a>

O Canvas exibe alertas durante a construção de _pipelines_. Esses alertas ajudam os desenvolvedores a identificarem e corrigirem problemas comuns mais rapidamente. Para saber mais, leia o artigo [Validação de construção do _pipeline_](https://docs.digibee.com/documentation/v/pt-br/build/pipelines/validacao-de-construcao-do-pipeline).

### Teste o _pipeline_ <a href="#h_e277eac4b9" id="h_e277eac4b9"></a>

Usando o Painel de execução, você pode executar e testar seu _pipeline_ diretamente da área de desenvolvimento. Utilize essa funcionalidade sempre que quiser avaliar o fluxo de integração, depurar e solucionar problemas. Para saber mais sobre essa funcionalidade, leia o artigo [Painel de execução](https://docs.digibee.com/documentation/v/pt-br/build/new-canvas-beta-restricted/execution-panel).

### Salve o _pipeline_ <a href="#h_3b2d142001" id="h_3b2d142001"></a>

Por fim, após construir seu fluxo de integração, clique em **Salvar** no canto superior direito da tela e defina um nome, uma descrição (opcional) e o projeto no qual o _pipeline_ estará alocado.

<figure><img src="../../.gitbook/assets/06 - Salvar - crop.gif" alt="Formulário com informações do pipeline a ser preenchido antes de salvar. "><figcaption></figcaption></figure>

{% hint style="warning" %}
Caso seu _pipeline_ esteja apresentando alertas do tipo **Erro**, o botão **Salvar** ficará bloqueado, impedindo que você o salve.
{% endhint %}
