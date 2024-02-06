---
description: >-
  Conheça os cenários de uso suportados ao usar File Reader e File Writer na
  Digibee Integration Platform.
---

# Como ler e escrever arquivos dentro de pastas

Dê uma olhada nos cenários de uso suportados a seguir. Para mais informações sobre cada componente, seus parâmetros e operações, veja a documentação sobre [**File Reader**](file-reader.md) e [**File Writer**](file-writer.md).

### **Cenário 1: Lendo um arquivo dentro de uma pasta**

Digamos que você tenha um arquivo "file.txt" na pasta "folder" disponível no seu _pipeline_. Para poder ler esse arquivo dentro de uma pasta, você pode usar um **File Reader** que indique o caminho "folder/file.txt". Dessa forma, você consegue acessar o arquivo "file.txt".

Siga os passos abaixo para saber como fazer isso:



<figure><img src="../../.gitbook/assets/How to file reader 31 oct.png" alt=""><figcaption></figcaption></figure>

1. Crie um _pipeline_ e adicione um componente **File Reader**.
2. Abra o formulário de configuração do componente.
3. Defina o parâmetro **File Name** como "folder/file.txt".
4. Clique em **Confirmar** para salvar as configurações do componente.
5. Conecte o _trigger_ com o **File Reader**.
6. Execute um teste no _pipeline_ (CTRL + ENTER).

O resultado será apresentado:

```
{
  "data": [
    "my sample content"
  ],
  "fileName": "folder/file.txt",
  "lineCount": 1
}
```

* **data:** vetor com o conteúdo do arquivo lido pelo **File Reader.**
* **fileName:** apresenta o caminho completo do arquivo que foi lido.
* **lineCount:** identifica a quantidade de linhas contidas no arquivo lido pelo **File Reader.**

### Cenário 2: escrevendo arquivos dentro de uma pasta

Digamos que você tenha um arquivo "file.txt" na pasta "folder" disponível no seu _pipeline_. Para poder escrever esse arquivo dentro de uma pasta, você pode usar um **File Writer** que indique o caminho "folder/file.txt". Dessa forma, você consegue acessar o arquivo "file.txt".

Veja como fazer isso:



<figure><img src="../../.gitbook/assets/How to file writer 31 oct.png" alt=""><figcaption></figcaption></figure>

1. Crie um _pipeline_ e adicione um componente **File Writer**.
2. Abra o formulário de configuração do componente.
3. Defina o parâmetro **File Name** como "folder/file.txt".
4. Defina o parâmetro **Data** _como_ `{{ message.data }}`_._\
   Note que usamos a expressão em _Double Braces:_ `{{ message.data }}` para acessar o resultado do último componente. Nesse caso, acessamos _data_ com o conteúdo do arquivo a ser escrito.
5. Clique em **Confirmar** para salvar as configurações do componente.
6. Conecte o _trigger_ com o **File Writer**.
7. Execute um teste no _pipeline_ (CTRL + ENTER).

O resultado será apresentado:

```
{
 "fileName": "folder/file.txt",
 "success": true
}
```

* **fileName:** apresenta o caminho completo do arquivo que foi escrito.
* **success:** quando apresenta _true_ no resultado, indica que a execução foi bem sucedida.
