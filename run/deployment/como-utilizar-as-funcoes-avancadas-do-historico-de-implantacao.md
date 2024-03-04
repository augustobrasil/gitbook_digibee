---
description: Restaure ou visualize um pipeline de qualquer versão implantada.
---

# Como utilizar as funções avançadas do histórico de implantação

{% hint style="info" %}
As funções avançadas do histórico de implantação estão atualmente em fase beta. Saiba mais sobre o[ Programa Beta](https://docs.digibee.com/documentation/v/pt-br/geral/programa-beta).
{% endhint %}

## Visão geral

As funções avançadas do Histórico de implantação permitem a execução de ações nos _pipelines_ implantados anteriormente. Essa funcionalidade tem duas opções disponíveis:

* Restaurar versão
* Exibir pipeline

Acesse o histórico de implantação dos _pipelines_ na página de Run. Ao entrar no submenu de funções avançadas você poderá visualizar todas as implantações de um _pipeline_ específico ou escolher qualquer implantação para restaurar.

## Como restaurar para qualquer versão implantada&#x20;

Siga estas etapas para restaurar um _pipeline_ para qualquer versão anterior:

1. Na página de Run, abra a aba **Histórico.**&#x20;
2. Selecione um _pipeline_ e clique na seta para abrir o painel lateral.
3. Escolha uma implantação disponível na seção **Histórico** do painel de informações.
4. Clique nos três pontinhos no canto superior direito do card do _pipeline_ para ver as opções do menu de funções avançadas.
5. Selecione a opção **Restaurar versão** para restaurar qualquer versão de _pipeline_ implantada.\


{% hint style="warning" %}
O uso da funcionalidade requer licenças da Plataforma Digibee.
{% endhint %}

6. A seguir, uma janela _pop-up_ se abrirá com as informações sobre o número de licenças disponíveis e as licenças necessárias para o uso da funcionalidade. Caso não haja licenças disponíveis, a ação não será executada.
7. Confirme a restauração da versão selecionada ao clicar no botão **Restaurar**. Do contrário, clique em **Cancelar**.
8. Depois de confirmar a restauração, o _pipeline_ selecionado será restaurado para sua versão anterior no ambiente em que estava alocado.

{% hint style="info" %}
Em caso de _bugs,_ a restauração não será executada e será exibida uma mensagem de erro.
{% endhint %}



## Como exibir um pipeline&#x20;

Siga estas etapas para visualizar um **pipeline** de uma versão anterior:

1. Repita as etapas (1-4) anteriores.
2. Selecione a opção **Exibir **_**pipeline**_ para visualizar a versão implantada diretamente no Canvas.
