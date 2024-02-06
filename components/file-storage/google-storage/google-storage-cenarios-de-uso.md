---
description: >-
  Conheça os cenários de uso suportados ao usar o componente Google Storage na
  Digibee Integration Platform.
---

# Google Storage: cenários de uso

Dê uma olhada nos cenários de uso suportados abaixo. Para mais informações sobre o componente, seus parâmetros e operações, [veja a documentação do Google Storage](https://docs.digibee.com/documentation/v/pt-br/components/file-storage/google-storage).

## **Cenário 1: Lista de arquivos**

Digamos que você tenha 1 ou mais arquivos no serivço Google Storage e que você queira usar o componente **Google Storage** no modo _List_. Dessa forma, você terá acesso à lista de arquivos existentes e suas respectivas pastas.

Veja como isso é possível no exemplo a seguir:

1. Crie um _pipeline_ e adicione o **Google Storage**.
2. Abra o formulário de configuração do componente.
3. Selecione uma conta no parâmetro **Account** (lembre-se que esse campo é obrigatório). Caso você não tenha uma conta configurada para acessar o Google Storage, primeiro é necessário gerar uma _primary key_ através do serviço. [Leia a documentação externa do Google para saber mais sobre esse processo](https://cloud.google.com/iam/docs/keys-create-delete). Na sequência, configure uma conta na Digibee Integration Platform.
4. Selecione a opção _List_ no parâmetro **Operation**.
5. Configure os outros campos obrigatórios do componente (**Project ID** e **Bucket Name**) assim como os opcionais (**Remote Directory**, **Page Size** e **Page Token**).
6. Clique em **Confirmar**.
7. Conecte o _trigger_ ao **Google Storage**.
8. Execute um teste no _pipeline_ (CTRL + ENTER).
9. Você verá uma lista dos arquivos disponíveis no Google Storage de acordo com as especificações que foram determinadas:

```
{
  "content": [
    {
      "name": "DGB-413/",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394033410,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 11
    },
    {
      "name": "DGB-413/iso-8859-1-test.txt",
      "contentType": "application/octet-stream",
      "contentEncoding": null,
      "createTime": 1579552641265,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 65
    }
  ],
  "pageToken": "ChtER0ItNDEzL2lzby04ODU5LTEtdGVzdC50eHQ=",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}

```

Como você pode ser no exemplo acima, a opção escolhida foi "_PageSize 2_", que significa que apenas 2 arquivos serão listados. Se não há valor especificado nesse campo, então todos os arquivos serão listados.

Porém, recomendamos que você especifique o valor, pois o desempenho e o tempo de recuperação dos dados podem ser comprometidos caso isso não seja feito. Dê uma olhada no próximo cenário e saiba como fazer a iteração de múltiplos arquivos sem afetar a segurança e o desempenho.

## **Cenário 2: Lista de vários arquivos usando paginação**

Digamos que você tenha uma grande quantidade de arquivos em seu Google Storage e que você queira usar o componente **Google Storage** no modo _List_. Dessa forma, você será capaz de listar os arquivos existentes usando paginação.

Para fazer isso, você deve seguir esses passos:

1. Crie um _pipeline_ e adicione o **Google Storage**. Defina o parâmetro **Step Name** como "_List-1_".
2. Abra o formulário de configuração do componente.
3. Selecione uma conta no parâmetro **Account** (lembre-se que esse campo é obrigatório).
4. Selecione a opção _List_ no parâmetro **Operation**.
5. Configure os outros campos obrigatórios do componente **(Project ID** e **Bucket Name**) assim como os opcionais (**Remote Directory**, **Page Size** e **Page Token**).
6. Clique em **Confirmar**.
7. Adicione um segundo componente **Google Storage** ao _pipeline_ e defina o parâmetro **Step Name** como "_List-2_".
8. Abra o formulário de configuração do segundo **Google Storage** e selecione a conta e operação, repetindo os passos 2, 3 e 4.
9.  Configure os campos obrigatórios do componente mais uma vez (**Project ID**, **Bucket Name**, **Page Size** e **Page Token**) assim como os opcionais (**Remote Directory**). Defina o _Page Token_ com a seguinte expressão _Double Braces_: `{{ message.pageToken }}`\


    _Double Braces_ dão acesso à saida do componente anterior. Logo, o _Page Token_ gerado pelo primeiro **Google Storage** ("_List-1_") permite que a próxima página de listagem de arquivos seja puxada para o segundo **Google Storage** ("_List-2_").&#x20;
10. Clique em **Confirmar**.
11. Conecte o _trigger_ e os componentes:

<figure><img src="../../../.gitbook/assets/google storage user scenario 01 eng oct 26.png" alt=""><figcaption></figcaption></figure>

12. Execute um teste no _pipeline_ (CTRL + ENTER).
13. Você verá uma lista dos arquivos disponíveis em seu serviço Google Storage de acordo com as especificações determinadas:

```
{
  "content": [
    {
      "name": "DGB-413/iso8859-2.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552395963553,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 55
    },
    {
      "name": "DGB-413/utf-16-test.txt",
      "contentType": "text/plain",
      "contentEncoding": null,
      "createTime": 1552394973030,
      "bucket": "digibee-test-digibee-test-bucket",
      "size": 70
    }
  ],
  "pageToken": "ChdER0ItNDEzL3V0Zi0xNi10ZXN0LnR4dA==",
  "fileName": null,
  "remoteFileName": null,
  "remoteDirectory": "DGB-413",
  "success": true
}

```

Como visto no exemplo acima, a saída mostra apenas os arquivos da última página (gerada pelo **Google Storage** com o nome "_List-2_"). No entanto, fica claro como você pode usar o _Page Token_ para acessar páginas consecutivas.

## **Cenário 3: Download de um arquivo**

Digamos que você tenha um arquivo em seu Google Storage e que você queira usar o componente **Google Storage** no modo _Download_. Dessa forma, você terá acesso a um arquivo específico para ser usado pelo _pipeline_.

Veja como fazer isso:

1. Crie um _pipeline_ e adicione o **Google Storage**.
2. Abra o formulário de configuração do componente.
3. Selecione uma conta no parâmetro **Account** (lembre-se que esse campo é obrigatório).
4. Selecione a opção _Download_ no parâmetro **Operation**.
5. Configure os outros campos obrigatórios do componente (**Project ID**, **Bucket Name** e **Remote File Name**) assim como os opcionais (**File Name** e **Remote Directory**).
6. Clique em **Confirmar**.
7. Conecte o _trigger_ ao **Google Storage**.
8. Execute um teste no _pipeline_ (CTRL + ENTER).
9. Você verá a confirmação da existência do arquivo e disponibilidade no _pipeline_, com o nome de arquivo especificado:

```
{
  "fileName": "iso-8859.txt",
  "remoteFileName": "iso-8859-1-test.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}

```

## **Cenário 4: Upload de um arquivo**

Digamos que você tenha um arquivo no _pipeline_ e queira usar o componente **Google Storage** no modo _Upload_. Dessa forma, o arquivo especificado se torna disponível em seu serviço Google Storage.

Saiba como fazer isso:

1. Crie um _pipeline_ e adicione o **Google Storage**.
2. Abra o formulário de configuração do componente.
3. Selecione uma conta no parâmetro **Account** (lembre-se que esse campo é obrigatório).
4. Selecione a opção _Upload_ no parâmetro **Operation**.
5. Configure os outros campos obrigatórios do componente (**Project ID**, \*\*Bucket Name \*\*e **File Name**) assim como os opcionais (**Remote** **File Name** e **Remote Directory**).
6. Clique em **Confirmar**.
7. Conecte o _trigger_ ao **Google Storage**.
8. Execute um teste no _pipeline_ (CTRL + ENTER).
9. Você verá uma confirmação da criação do arquivo no Google Storage, com o nome do arquivo remoto e diretório remoto especificados:

```
{
  "fileName": "iso-8859.txt",
  "remoteFileName": "iso-8859-upload.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}

```

## **Cenário 5: Remoção de um arquivo**

Digamos que você tenha um arquivo em seu Google Storage e queira usar o componente **Google Storage** no modo _Delete_. Dessa forma, o arquivo é removido do seu Google Storage.

Para fazer isso, siga os passos a seguir:

1. Crie um _pipeline_ e adicione o **Google Storage**.
2. Abra o formulário de configuração do componente.
3. Selecione uma conta no parâmetro **Account** (lembre-se que esse campo é obrigatório).
4. Selecione a opção _Delete_ no parâmetro **Operation**.
5. Configure os outros campos obrigatórios do componente (**Project ID**, \*\*Bucket Name \*\*e **Remote File Name**) assim como os opcionais (**Remote Directory**).
6. Clique em **Confirmar**.
7. Conecte o _trigger_ ao **Google Storage**.
8. Execute um teste no _pipeline_ (CTRL + ENTER).
9. Você verá uma confirmação da remoção do arquivo do seu Google Storage:

```
{
  "fileName": null,
  "remoteFileName": "iso-8859-upload.txt",
  "remoteDirectory": "DGB-413",
  "success": true
}

```
