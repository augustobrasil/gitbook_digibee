---
description: >-
  Descubra mais sobre o componente Email V2 e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Email V2

O **Email V2** permite o envio de emails simples, no formato HTML ou até mesmo contendo anexos.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`.

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th width="186">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Necessário para o componente fazer a autenticação ao servidor de email a ser utilizado no envio, caso esse serviço de email seja requisitado na autenticação.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>SMTP Host</strong></td><td><em>host</em> SMTP do servidor de email. Ex.: (Gmail: smtp.gmail.com).</td><td><a href="http://smtp.gmail.com/">smtp.gmail.com</a></td><td><em>String</em></td></tr><tr><td><strong>SMTP Port</strong></td><td>Porta SMTP do servidor de email. Geralmente utiliza-se a porta 587, mas pode haver variação dependendo do servidor de email utilizado.</td><td>587</td><td>Inteiro</td></tr><tr><td><strong>From</strong></td><td>Remetente do email.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>To</strong></td><td>Destinatários do email. <br><br>Caso existam múltiplos destinatários, eles devem ser separados por vírgula. Ex: a@a.com,b@b.com,....</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>CC</strong></td><td>Destinatários que receberão a cópia do email. <br><br>Caso existam múltiplos destinatários, eles devem ser separados por vírgula. Ex: a@a.com,b@b.com,....</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>BCC</strong></td><td>Destinatários que receberão a cópia oculta do email. <br><br>Caso existam múltiplos destinatários, eles devem ser separados por vírgula. Ex: a@a.com,b@b.com,....</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Content</strong></td><td>Corpo do email. Aceita o uso de <em>templates</em> Freemarker para a geração de HTML dinâmicos.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td><em>Charset</em> que será utilizado no envio do corpo do email.</td><td>UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Subject</strong></td><td>Assunto do email.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Authenticated</strong></td><td>Se a opção estiver habilitada, é obrigatório passar uma conta com email e senha a serem utilizados para autenticação. <br><br>Se os envios não precisarem de autenticação, a opção deve ficar desabilitada.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Is Over SSL</strong></td><td>Se a opção estiver habilitada, o envio é feito via SSL.</td><td><em>True</em></td><td>Booleano</td></tr><tr><td><strong>Socket Port</strong></td><td>Se a opção <strong>Is Over SSL</strong> estiver habilitada, então é obrigatório informar qual porta será utilizada para trafegar a mensagem via SSL.</td><td>N/A</td><td>Inteiro</td></tr><tr><td><strong>Is Over TLS</strong></td><td>Se a opção estiver habilitada, o envio é feito via TLS.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Force TLSv1.2</strong></td><td>Define como obrigatória a conexão com o protocolo TLSv1.2.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Custom Attachments Specification</strong></td><td>Se a opção estiver habilitada, o formulário para adicionar anexos será ocultado e o envio em modo RAW poderá ser utilizado, por meio do qual você informa o <em>array</em> de anexos. <br><br>Mas se a opção estiver desabilitada, será utilizada a abordagem do formulário para a especificação de anexos.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Attachments</strong></td><td>Anexos da mensagem. A especificação ocorre via formulário.</td><td>N/A</td><td>Opções de <em>Custom Attachments Specification</em> / <em>Array</em> de Objetos</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>

{% hint style="warning" %}
No parâmetro **Attachments**, para adicionar imagens dentro do corpo do email, deve ser informado o prefixo "cid:" antes do nome da imagem. Ex.: \<img src"cid: image.png" />
{% endhint %}

## Fluxo de mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### Entrada <a href="#entrada" id="entrada"></a>

Esse componente não espera nenhuma mensagem de entrada específica, somente se for informada uma expressão em _Double Braces_ em algum dos seus campos.

### Saída <a href="#sada" id="sada"></a>

Ao executar um componente **Email V2**, a seguinte estrutura de JSON será gerada:

```
{
    "from": "a@a.com",
    "to": "a@a.com,a@a.com.br",
    "cc":"a@a.com,a@a.com.br",
    "bcc": "a@a.com,a@a.com.br",
    "subject": "Subject",
    "content": "<html>Test Email!</html>",
    "charset": "UTF-8",
    "success": true,
    "attachments": [{
        "type": "ATTACHMENT",
        "attachment": "attachment.extension"
    }]
}
```

* **from:** remetente.
* **to:** destinatários.
* **cc:** destinatários em cópia.
* **bcc:** destinatários em cópia oculta.
* **subject:** assunto.
* **content:** corpo da mensagem. Caso o corpo da mensagem exceda 256 caracteres, esse resultado será truncado.
* **charset:** _charset._
* **success:** se a chamada foi bem sucedida.
* **attachments:** _array_ contendo os anexos enviados.

{% hint style="info" %}
A manipulação de arquivos dentro de um _pipeline_ ocorre de forma protegida. Os arquivos ficam disponíveis em diretório temporário que somente o _pipeline_ sendo executado tem acesso.
{% endhint %}

Para entender melhor o fluxo das mensagens na Digibee Integration Platform, leia o artigo sobre [Processamento de mensagens](../../build/pipelines/processamento-de-mensagens.md).

## Email V2 em Ação <a href="#email-v2-em-ao" id="email-v2-em-ao"></a>

Veja abaixo como o componente se comporta em determinada situação e a sua respectiva configuração.

### Enviando um arquivo de texto (xpto.txt) como anexo em modo RAW e o corpo do email contendo imagens também <a href="#enviando-um-arquivo-de-texto-xptotxt-como-anexo-em-modo-raw-e-o-corpo-do-email-contendo-imagens-tamb" id="enviando-um-arquivo-de-texto-xptotxt-como-anexo-em-modo-raw-e-o-corpo-do-email-contendo-imagens-tamb"></a>

* **SMTP Host:** smtp.gmail.com
* **SMTP Port:** 587
* **From:** [email@gmail.com](mailto:email@gmail.com) (esse email deve ser o mesmo configurado na conta especificada neste componente)
* **To:** [some\_other\_email@gmail.com](mailto:some\_other\_email@gmail.com),[second\_email@gmail.com](mailto:second\_email@gmail.com)
* **Subject:** Hello
* **Content:**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
 <head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>Demystifying Email Design</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
</head>
<body>
<img src="cid:myImage.png" />
</body>
</html>
```

* **Authenticated:** habilitado
* **Is Over TLS:** habilitado
* **Attachment As Raw:** habilitado
* **Attachments:**

```
[
{"type": "INLINE", "attachment": "myImage.png" },
{"type": "ATTACHMENT", "attachment": "xpto.txt" }
]
```

O resultado será:

```
{
    "from": "email@gmail.com",
    "to": "some_other_email@gmail.com,second_email@gmail.com",
    "cc":"",
    "bcc": "",
    "subject": "Hello",
    "content": "<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv ...TRUNCATED",
    "charset": "UTF-8",
    "success": true,
    "attachments": [
        {"type": "INLINE", "attachment": "myImage.png" },
        {"type": "ATTACHMENT", "attachment": "xpto.txt" }
    ]
}
```

Veja como passar valores de forma dinâmica usando o conector:

![](<../../.gitbook/assets/ezgif.com-gif-maker (20) (1).gif>)

Neste exemplo de uso dinâmico, passamos variáveis indicando a emissão de notas fiscais `<a href='${NF}' com uma segunda variável indicando o vencimento ${M_VENC}.`

```
<!DOCTYPE html>
<html>
<head>
 </head>
<body>
 
Boa tarde, <br/>
Segue a nota fiscal <a href='${NF}'>(Clique aqui)</a> referente a mensalidade de licenciamento da plataforma – com vencimento para <b> ${M_VENC}</b>. <br/>
O pagamento será via <b>transferência bancária</b> - dados no corpo da nota fiscal.   <br/><br/>


Por favor, confirmar o recebimento. <br/>
Qualquer dúvida, estamos à disposição. <br/><br/>
 <br/>
 <br/>
Att.,
Relacionamento com o Cliente
</body>
</html>

```

Observe que o conector _permite o uso de_ D_ouble Braces:_



![](<../../.gitbook/assets/ezgif.com-gif-maker (19).gif>)

#### Dados do _JSON_

```
{
    "remetente": "digibee@gmail.com",
    "destinatario" : "digi@gmail.com",
    "destinatario_cc" : "digi1@gmail.com",
    "destinatario_bcc" : "digi2@gmail.com",
    "port" : "587",
    "host": "smtp.gmail.com",
    "NF": "98787979789",
    "M_VENC" : "13/01/2023"
}
```

## Tecnologia <a href="#tecnologia" id="tecnologia"></a>

Utilizamos o Freemarker para realizar as nossas conversões e transformações no _template_ do corpo do email. Leia a [documentação externa do Freemarker](https://freemarker.apache.org/docs/dgui\_template\_exp.html) para saber como utilizá-lo.
