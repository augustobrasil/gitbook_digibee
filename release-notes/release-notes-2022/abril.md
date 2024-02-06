# Abril

## Novidades 26/04/2022

#### **COMPONENTES**

* **Kafka:** agora o componente suporta configurações no formato AVRO para envio de mensagens. Para saber mais, leia a [documentação atualizada do componente Kafka](../../components/queues-and-messaging/kafka.md).\\

Nós também solucionamos um _bug_:

* **WebDAV:** corrigimos o erro que, em algumas situações, impedia o upload de arquivos.

## Novidades 12/04/2022

#### **TRIGGERS**

* **HTTP, REST e HTTP File:** agora é possível configurar um _header_ de resposta utilizando Double Braces. Isso significa que é possível utilizar um determinado valor dentro do _body_ ou dos metadados do pipeline.\
  \
  Para mais informações acesse a documentação completa dos triggers: [HTTP](../../components/triggers/http-trigger.md), [REST](../../components/triggers/rest-trigger.md) e [HTTP FIle - Downloads](../../components/triggers/http-file-trigger/http-file-trigger-downloads.md) e [HTTP File - Uploads](../../components/triggers/http-file-trigger/http-file-trigger-uploads.md).

#### **mTLS**

Agora a funcionalidade de mTLS está liberado para todos os clientes.

O mútuo TLS, ou mTLS, é um protocolo de autenticação bilateral. Ao validar que ambos as partes (servidor e cliente) possuem a correta chave privada, mTLS assegura que as pessoas ou sistemas em ambos os lados de uma conexão de rede sejam quem afirmam ser.

[Leia a documentação completa sobre mTLS aqui](../../components/triggers/triggers-settings/mtls.md).

#### **SUPORTE**

Nosso suporte já está atuando com atendimento 24 horas e em 3 idiomas (português, inglês e espanhol), para todos os clientes.

Se precisar de ajuda, abra um _chat_ através da Digibee Integration Platform no ícone "?"

[Clique aqui para saber mais a respeito](../../general/digibee-customer-support/).

#### **ARTIGOS**

Visando melhorar nossa documentação, criamos o artigo abaixo:

* [Test mode](broken-reference)

Nós também solucionamos alguns _bugs_:

* **Retry:** corrigimos o erro que ocorria após o timeout no componente Retry de uma execução, onde o componente não executava a requisição seguinte.
* **Pipeline Logs:** corrigimos o erro que mostrava uma linha de log com a mensagem “Unexpected error” e o campo Pipeline Key em branco.\
  Essa mensagem aparecia quando os componentes JWT e REST V2 recebiam uma resposta em formato HTML.\
  Para conferir o comportamento das respostas dos componentes, acesse a documentação completa: [Digibee JWT](../../components/security-components/digibee-jwt/), [REST V2](../../components/web-protocols/rest-v2.md).
