---
description: Conheça o trigger e saiba como utilizá-lo.
---

# Email Trigger

{% hint style="info" %}
Este trigger suporta apenas o protocolo IMAP, sem anexos.
{% endhint %}

O **Email Trigger** permite o recebimento dos dados de uma conta de e-mail no _pipeline_.&#x20;

## Parâmetros

Dê uma olhada nos parâmetros de configuração do _trigger_. Parâmetros suportados por [expressões _Double Braces_](../../build/double-braces/) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th width="239">Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Especifique a conta para que o <em>trigger</em> acesse o e-mail correto.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Ação a ser executada pelo <em>trigger</em>. As opções são: <em>Mark as Read</em>, <em>Move to Another Folder</em> e <em>Delete</em>. Veja mais sobre as operações na seção abaixo.</td><td><em>Mark as Read</em></td><td><em>String</em></td></tr><tr><td><strong>Hostname</strong></td><td>nome do <em>host</em> do servidor IMAP (por exemplo, imap.uol.com).</td><td>imap.gmail.com</td><td><em>String</em></td></tr><tr><td><strong>Port</strong></td><td>Número da porta.</td><td>993</td><td>Inteiro</td></tr><tr><td><strong>Email Folder</strong></td><td>Nome da pasta/caixa de entrada que o <em>trigger</em> deve ler (por exemplo, <em>inbox</em>). Nessa pasta não podem existir mais que 100 mensagens (lidas/não lidas).</td><td>inbox</td><td><em>String</em></td></tr><tr><td><strong>Destination Email Folder</strong></td><td>Aponte para qual pasta a mensagem deve ser movida. <br>Note que este campo aparece apenas quando é escolhida a opção <em>Move to Another Folder</em> em <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Maximum Timeout</strong></td><td>tempo máximo (em milissegundos) para o <em>pipeline</em> processar informação antes de retornar uma resposta. Limite: 900000.</td><td>30000</td><td>Inteiro</td></tr><tr><td><strong>Allow Redelivery Of Messages</strong></td><td>se ativada, a opção permite que as mensagens sejam entregues novamente caso o <em>Pipeline Engine</em> falhe.</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

## Campo Operation <a href="#h_7f01d390b4" id="h_7f01d390b4"></a>

* **Mark as Read:** selecione essa opção se, após processada, você deseja que a mensagem seja marcada como lida.
* **Move to Another Folder:** selecione essa opção se, após processada, você deseja que a mensagem seja movida para uma pasta pré-determinada. O destino é especificado no campo **Destination Email Folder**, que só aparece nas configurações quando _Move to Another Folder_ é selecionada.
* **Delete:** selecione essa opção se, após processada, você deseja que a mensagem seja excluída.

## Anexos <a href="#h_ed7b1075bc" id="h_ed7b1075bc"></a>

Caso haja algum anexo no corpo da mensagem recebida pelo _trigger_, ele vai baixá-las e disponibilizá-las dentro do diretório de execução do _pipeline_. Os nomes dos anexos estarão contidos dentro da propriedade `attachments` e essa propriedade será um _array_ de _strings_ contendo os nomes dos anexos.

Caso haja 2 anexos com o mesmo nome na mensagem, um identificador único será adicionado no nome do anexo baixado.

#### **Exemplo:**

Há 2 anexos com nome "file.csv" dentro da mensagem. Portanto, o conteúdo da propriedade `attachments` será:

```
{
"attachments": ["file.csv", "0072e485-8ba2-4f79-bba5-8068e37ee792_file.csv"]
}
```

O identificador varia a cada execução.

{% hint style="info" %}
**Nota:** Se você utilizar o Gmail como _host_ do servidor IMAP, será necessário autorizar o suporte de aplicações não seguras. Confira a [documentação externa do Google](https://support.google.com/accounts/answer/6010255?hl=pt-BR) para ver o passo-a-passo.
{% endhint %}

## Exemplo de uso&#x20;

Veja os parâmetros a serem configurados com o exemplo abaixo:

1\. Abra as configurações de _trigger_ e selecione o tipo **email**.

2\. Preencha os campos de configuração de acordo com as suas especificações. Para este exemplo, selecione a opção _Mark as Read_ em **Operation**.

3\. Clique em **Confirmar**.

4\. Continue a construção do _pipeline_.

5\. Conecte os seus componentes.

6\. Faça o _deploy_ do pipeline:

* Clique em **Run**, localizado na parte superior da tela.
* Selecione o ambiente, que pode ser **test** ou **prod**.
* Clique em **Criar**.
* Selecione o _pipeline_ com a sua versão e capacidade.
* Clique em **Implantar**.

7\. Quando for disparado, o _pipeline_ receberá um _payload_ similar ao seguinte:

```
{ 
 "textMessage": "",
 "htmlMessage": "Olá, Pedro\r\nAinda não recebi o relatório deste mês. 
     Você poderia enviá-lo até o final do dia?",
 "attachments": ["attachment_fileName1", "attachment_fileName2", 
     "attachment_fileName3"]
  "subject": "Relatório mensal",
  "from": ["Renato Peixe Junior <renato.peixe@gmail.com>"],
  "to": ["pedro.gomes@gmail.com"],
  "cc": [],
  "bcc": [],
  "replyTo": ["Renato Peixe Junior <renato.peixe@gmail.com>"],
  "sentDate": "2020-02-10T17:54:40Z[UTC]",
  "receivedDate": "2020-02-10T17:54:52Z[UTC]"
} 
```

* **data:** conteúdo da mensagem.
* **subject:** assunto da mensagem.
* **from:** e-mail do remetente.
* **to:** e-mail do destinatário.
* **cc:** destinatários em cópia.
* **bcc:** destinatários em cópia oculta.
* **replyTo:** e-mail de destino da resposta.
* **sentDate:** data de envio da mensagem.
* **receivedDate:** data de recebimento da mensagem.
