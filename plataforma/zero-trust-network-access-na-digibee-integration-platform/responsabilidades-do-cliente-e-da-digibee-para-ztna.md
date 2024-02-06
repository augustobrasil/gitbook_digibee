# Responsabilidades do cliente e da Digibee para ZTNA

Esta documentação descreve as respectivas responsabilidades do cliente e da Digibee pela instalação, implementação e operação da conexão via ZTNA na Digibee Integration Platform.&#x20;

| Tarefa                                                                                                                                                                                                                                                                                          | Responsabilidade da Digibee | Responsabilidade do Cliente |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- | --------------------------- |
| Registro do Edge Router (2 ER's, cliente e Digibee)                                                                                                                                                                                                                                             | ✔                           | <p><br></p>                 |
| Instalação do roteador Edge (lado Digibee)                                                                                                                                                                                                                                                      | ✔                           | <p><br></p>                 |
| Instalação do roteador Edge (lado do cliente)                                                                                                                                                                                                                                                   | <p><br></p>                 | ✔                           |
| Conceder acesso ao Edge Router (lado do cliente) para cada serviço, endpoint, servidor, etc. que será acessado pela plataforma DGB através do túnel ZTNA                                                                                                                                        | <p><br></p>                 | ✔                           |
| Usando o recurso Chat no realm, criando um ticket que forneça o endpoint que será acessado (o recurso deve estar acessível no Edge Router do lado do cliente). O ticket deve incluir uma tabela com o endpoint real (FQDN e a Porta).                                                           | <p><br></p>                 | ✔                           |
| A correção manual de vulnerabilidades de segurança usando o comando “apt” ou uma ferramenta/solução como Automox, Ivanti ou Ansible pode ser feita durante qualquer janela de rotina de correção do cliente. A Digibee corrigirá seu lado mensalmente ou se um dia zero for identificado antes. | ✔                           | ✔                           |
| Black Carbon e outras ferramentas de segurança podem ser usadas na imagem, mas devem ser feitas exceções para os 3 binários: ziti, ziti-router e ziti-edge-tunnel                                                                                                                               | <p><br></p>                 | ✔                           |
| Cria os SERVIÇOS relacionados a cada entrada da tabela de relacionamento enviada pelo cliente                                                                                                                                                                                                   | ✔                           | <p><br></p>                 |
| Define APPWANs para garantir que o Edge Router do lado DGB possa rotear o tráfego para os SERVIÇOS do cliente.                                                                                                                                                                                  | ✔                           | <p><br></p>                 |



{% hint style="info" %}
Para instalar o Edge Router (lado do cliente) siga as instruções neste[ link](https://support.netfoundry.io/hc/en-us/articles/5700949793293-Deployment-guides-for-provisioning-customer-edge-routers-in-a-private-cloud)
{% endhint %}

Veja abaixo um exemplo de tabela de relacionamento, supondo que precisamos expor dois recursos do lado do cliente:

**1 servidor de banco de dados: my\_super\_critical\_database.thebestcustomer.me (FQDN), PORTA 3306**

**1 servidor SFTP: my\_best\_sftp\_server.thebestcustomer.me (FQDN). PORTA 22**

| Real Endpoint (DNS que pode ser resolvido no lado do cliente) | Porta Verdadeira | Resultado após a criação da rota (usado em pipelines) | Porta |
| ------------------------------------------------------------- | ---------------- | ----------------------------------------------------- | ----- |
| my\_super\_critical\_database.thebestcustomer.me              | 3306             | my\_super\_critical\_database.thebestcustomer.me      | 3306  |
| my\_best\_sftp\_server.thebestcustomer.me                     | 22               | my\_best\_sftp\_server.thebestcustomer.digibee.me     | 22    |

As colunas da direita são resultado da implementação do ZTNA, essas rotas serão acessadas a partir dos pipelines do realm.&#x20;
