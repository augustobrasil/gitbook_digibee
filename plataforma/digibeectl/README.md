---
description: Saiba mais sobre a aplicação do digibeectl e seus comandos.
---

# digibeectl

O **digibeectl** é uma aplicação que não apenas fornece comandos para gerenciar seus pipelines, mas também permite interagir com as respectivas implantações em qualquer estágio da Digibee Integration Platform. Aqui você saberá quais são os primeiros passos para manusear o digibeectl, incluindo o processo de instalação e a autenticação de usuários.

## **Instalando o digibeectl** <a href="#h_e0e4d4a6f8" id="h_e0e4d4a6f8"></a>

A maneira mais fácil de instalar o digibeectl é com ferramentas de linha de comando, pois assim o processo se resume a apenas 1 linha de comando.

As opções de instalação para o digibeectl variam de acordo com o seu sistema operacional:

### **Linux / MacOs**

{% hint style="warning" %}
**Windows** não é suportado. Está em desenvolvimento.
{% endhint %}

O digibeectl é fornecido como um arquivo ‘tar.gz’ para MacOs e Linux. O comando a seguir ajuda na instalação do digibeectl com apenas uma execução. Para fazer isso, abra uma janela do terminal e execute-o:

```
curl -s https://storage.googleapis.com/digibee-release-test/releases/install.sh | bash
```

## **Configurando o digibeectl** <a href="#h_05f438ac2a" id="h_05f438ac2a"></a>

O digibeectl requer um arquivo de configuração criptografado e que gera um _token_ de autenticação. Confira o [artigo completo](https://docs.digibee.com/documentation/v/pt-br/plataforma/digibeectl/gerando-novo-token) para saber como baixar seu próprio arquivo.

O digibeectl utiliza os comandos _GET_ e _SET_, para que você possa configurar o seu cliente sem dificuldades. As informações são salvas automaticamente em um arquivo de configuração, o qual é usado para comandos subsequentes.

O exemplo a seguir mostra a configuração usando um _set_ que persiste os dados localmente:

```
digibeectl set config --file "path/file.json" --secret-key "chave-de-criptografia" --auth-key "senha-de-criptografia"
```

## **Atualização das versões do digibeectl** <a href="#h_f50d8e548b" id="h_f50d8e548b"></a>

Para atualizar o digibeectl nos sistemas Linux e Mac basta executar a linha de instalação novamente. Para isso, abra uma janela do terminal e execute:

```
curl -s https://storage.googleapis.com/digibee-release-test/releases/install.sh | bash
```

## **Operações** <a href="#h_f7a0e956bb" id="h_f7a0e956bb"></a>

A tabela a seguir inclui descrições curtas e a sintaxe geral para todas as operações da digibeectl:

| Operação | Sintaxe                                    | Descrição                                              |
| -------- | ------------------------------------------ | ------------------------------------------------------ |
| create   | digibeectl create RESOURCE \[flags]        | Para a criação de 1 ou mais recursos.                  |
| delete   | digibeectl create RESOURCE \[flags]        | Para remover recursos de forma permanente.             |
| get      | digibeectl get RESOURCE \[flags] \[–watch] | Para listar 1 ou mais recursos.                        |
| set      | digibeectl set RESOURCE \[flags]           | Para alterar os recursos                               |
| help     | digibeectl \[-h]                           | Para obter mais detalhes sobre cada _flag_ ou comando. |

## Tipos de recurso <a href="#h_4a05c14d6c" id="h_4a05c14d6c"></a>

A tabela a seguir lista todos os tipos de recursos suportados e os seus títulos mais comuns:

| Recurso    | Titulo Comum | Descrição                                               |
| ---------- | ------------ | ------------------------------------------------------- |
| config     | -            | Recurso para operar configurações.                      |
| deployment | deployments  | Recurso para operar implantações.                       |
| pipeline   | pipelines    | Recurso para operar _pipelines_.                        |
| realm      | realms       | Recurso para consultar informações sobre o seu _realm._ |
| license    | licenses     | Recurso para consultar informações sobre sua licença_._ |

## Flags de recursos <a href="#h_7477095d7f" id="h_7477095d7f"></a>

As tabelas abaixo separam os recursos por cada operação e suas respectivas _flags:_

### **Config**

| Operação | Recurso | Flags        | Titulo Comum | Descrição                                                |
| -------- | ------- | ------------ | ------------ | -------------------------------------------------------- |
| get      | config  | -            | configs      | Lista as configurações atuais.                           |
| set      | config  | -            | configs      | Configura os parâmetros e o token de autenticação.       |
|          |         | --file       |              | \*Arquivo de configurações gerado através da Plataforma. |
|          |         | --secret-key |              | \*Chave de criptografia.                                 |
|          |         | --auth-key   |              | \*Chave de autorização.                                  |
|          |         | --help       | -h           | Lista os comandos de ajuda.                              |

No artigo [Como obter arquivo de configuração do digibeectl](https://docs.digibee.com/documentation/v/pt-br/plataforma/digibeectl/gerando-novo-token) você saberá mais sobre arquivo criptografado, chave criptografada e chave de autenticação.

### Deployment

| Operação | Recurso    | Flags                                         | Titulo Comum | Descrição                                                                                                                                    | Permissões                                                                           |
| -------- | ---------- | --------------------------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| get      | deployment | -                                             |              | Consulta implantações.                                                                                                                       | DEPLOYMENT:READ                                                                      |
|          |            | --deployment-id                               | -d           | ID da implantação.                                                                                                                           |                                                                                      |
|          |            | --environment                                 | -e           | <p>Filtra implantações por ambiente.<br>O ambiente <em>default</em> é "test".</p>                                                            |                                                                                      |
|          |            | --name                                        | -n           | Filtra implantações por nome.                                                                                                                |                                                                                      |
|          |            | --help                                        | -h           | Para obter ajuda na implantação.                                                                                                             |                                                                                      |
| create   | deployment | -                                             |              | Cria implantações.                                                                                                                           | DEPLOYMENT:CREATE DEPLOYMENT:CREATE:REDEPLOY CONFIGURATION:READ CONFIGURATION:UPDATE |
|          |            | <p>--pipeline-id</p><p>(flag obrigatória)</p> |              | _ID_ do _pipeline_.                                                                                                                          |                                                                                      |
|          |            | --pipeline-size                               | -s           | Tamanho do _pipeline_ (SMALL/MEDIUM/LARGE). O tamanho _default_ é SMALL.                                                                     |                                                                                      |
|          |            | --consumers                                   | -c           | Número máximo de _Consumers_ do _pipeline_ a ser implantado.O valor máximo e/ou _default_ de cada tamanho é: SMALL=10 / MEDIUM=20 / LARGE=40 |                                                                                      |
|          |            | --environment                                 | -e           | <p>Define o ambiente no qual a implantação será feita.<br>O ambiente <em>default</em> é "test".</p>                                          |                                                                                      |
|          |            | --instance-name                               | -i           | Quando o pipeline têm multi-instâncias, define qual instância deste pipeline deve ser implantada.                                            |                                                                                      |
|          |            | --redeploy                                    |              | Permite a reimplantação de um pipeline.                                                                                                      |                                                                                      |
|          |            | --replicas                                    |              | Define o número de réplicas do pipeline. O valor padrão é "1".                                                                               |                                                                                      |
|          |            | --wait                                        |              | Se ativado, aguarda a implantação ser concluída. O _timeout_ é de 300 segundos.                                                              |                                                                                      |
| delete   | deployment | -                                             |              | Remove implantações.                                                                                                                         | DEPLOYMENT:DELETE                                                                    |
|          |            | --deployment-id                               | -d,          | _Id_ da implantação a ser removida.                                                                                                          |                                                                                      |
|          |            | --environment                                 | -e,          | Ambiente da implantação a ser removida.                                                                                                      |                                                                                      |
|          |            | --help                                        | -h           | Lista os comandos de ajuda para _deploymeny._                                                                                                |                                                                                      |

### **Pipeline**

***

| Operação | Recurso  | Flags                    | Titulo Comum | Descrição                                                 | Permissões    |
| -------- | -------- | ------------------------ | ------------ | --------------------------------------------------------- | ------------- |
| get      | pipeline | -                        |              | Consulta informações de pipelines.                        | PIPELINE:READ |
|          |          | --name                   | -n           | Filtra pipelines por nome.                                |               |
|          |          | --pipeline-id            |              | Filtra pipelines por ID..                                 |               |
|          |          | --pipeline-version-major |              | Filtra pipelines por versão major.                        |               |
|          |          | --pipeline-version-minor |              | Filtra pipelines por versão _minor._                      |               |
|          |          | --archived               | -a           | Lista apenas _pipelines_ arquivados.                      |               |
|          |          | --flowspec               | -o           | Exibe o FlowSpec do _pipeline_ e exige o `--pipeline-id.` |               |
|          |          | --show-versions          |              | Exibe todas as versões _minor_ de um _pipeline_.          |               |
|          |          | ---help                  | -h           | Lista os comandos de ajuda para _pipeline_.               |               |

### **Realm**

| Operação | Recurso | Flags  | Titulo Comum | Descrição                               | Permissões |
| -------- | ------- | ------ | ------------ | --------------------------------------- | ---------- |
| get      | realm   | -      | -            | Consulta informações sobre o seu realm. | REALM:READ |
|          |         | --help | -h           | Lista os comandos de ajuda.             |            |



### Licença

| Operação | Recurso | Flags | Titulo Comum | Descrição                     | Permissões   |
| -------- | ------- | ----- | ------------ | ----------------------------- | ------------ |
| get      | license | -     | -            | Lista informações da licença. | LICENSE:READ |

