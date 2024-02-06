---
description: Tire suas dúvidas sobre o digibeectl e facilite suas integrações.
---

# digibeectl - Dúvidas Frequentes

## **O que é o digibeectl?**

O **digibeectl** é o CLI (_command-line interface_) da Digibee que permite a execução de uma série de passos relacionados aos serviços disponíveis na Digibee Integration Platform, até então somente disponíveis através da interface gráfica.

## **Quais funcionalidades são resolvidas pelo digibeectl?**

Através do digibeectl é possível consultar detalhes dos _pipelines_ bem como implantar e remover _pipelines_ dos ambientes oferecidos pela Plataforma. O digibeectl está em constante evolução e novas funcionalidades serão agregadas a ele, fazendo com que qualquer operação disponível na interface gráfica também seja feita por linha de comando.

Para saber mais sobre as funcionalidades disponíveis no digibeectl, consulte [Guia de uso do digibeectl.](./)

## **Como ativo o digibeectl no meu realm?**

Você pode ativar o digibeectl na página digibeectl, na seção de **Administração**. Se você precisar de ajuda para instalar a aplicação ou escrever comandos digibeectl, entre em contato com nossa equipe de suporte.

## O digibeectl é seguro para compartilhar os meus dados sensíveis?

Sim, o digibeectl baseia-se na arquitetura de segurança da Digibee. Um _token_ exclusivo é gerado de tal forma que somente as permissões necessárias sejam concedidas. Para saber mais como gerar o _token_ do digibeectl consulte o artigo [Como obter um artigo de configuração do digibeectl](gerando-novo-token.md).

## **Como funciona o versionamento e a manutenção do digibeectl?**

O digibeectl segue a cadência de releases da Digibee Integration Platform. Como é um CLI que é instalado nos ambientes dos clientes, é importante mantê-lo sempre atualizado com as novas versões.

* Versionamento: major.minor.fix
* Exemplo da primeira versão: 0.1.x

{% hint style="warning" %}
Upgrades que afetem a versão _fix_ não impactarão as operações existentes.
{% endhint %}

A Plataforma bloqueará o uso a partir de versões muito antigas pois elas poderão não ser mais compatíveis com as evoluções entregues. Por isso, é importante sempre manter o digibeectl atualizado.

## **Como eu controlo o acesso ao digibeectl dentro da minha organização?**

Para utilizar o digibeectl é necessário ter permissões para gerar um _token_ exclusivo de acesso. Este _token_ só pode ser gerado por usuários com as devidas permissões e possui escopo reduzido de ação.

As seguintes permissões são necessárias para utilizar o digibeectl:

* USER:CREATE:GENERATE-JWT
* USER:READ:LIST-JWT
* USER:DELETE:REVOKE-JWT

Para maiores detalhes sobre como gerar o token para o digibeectl, consulte o artigo [Como obter um artigo de configuração do digibeectl](gerando-novo-token.md).

## **O digibeectl é compatível com minhas ferramentas de CI/CD e processos DevOps?**

O digibeectl é compatível com todas as plataformas de CI/CD do mercado, bastando que utilize a lista de sistemas operacionais suportados (mais detalhes no [Guia de uso do digibeectl](./)) e possa acionar o comando digibeectl ao longo dos processos.
