# Março

## Novidades 21/03/2023

### COMPONENTES

* **Custom API path para os triggers Rest, HTTP e HTTP File:** melhoramos os _triggers_ com uma opção de _custom API path_ que permite a remoção do prefixo de rota padrão Digibee "/pipeline/{realm}/v{n}" para utilizar rotas customizadas em _pipelines_ que utilizem estes _triggers_ somente com mTLS ativo. Para saber mais, visite a documentação do [REST Trigger](../../components/triggers/rest-trigger.md), [HTTP Trigger](../../components/triggers/http-trigger.md) e [HTTP File Trigger](../../components/triggers/http-file-trigger/).
* **JWT:** uma melhoria no componente agora permite verificar _tokens_ JWS através de JWKs e adicionar _headers_ customizados ao gerar _tokens_ JWT. Saiba mais na documentação do [JWT](../../components/security-components/jwt-deprecated.md).
* **Suporte DB2 para DB V2 e Stream DB V3:** atualizamos nossa base de bancos de dados suportados para inclusão do _driver_ JDBC IBM DB2. O _driver_ licenciado pela sua empresa junto a IBM deve ser ativado para se conectar às versões suportadas dos bancos de dados. Saiba mais na documentação de [Bancos de dados suportados](../../plataforma/bancos-de-dados-suportados.md).
* **Digibee JWT:** uma atualização corrigiu o ícone do componente.
* **SFTP e SSH Remote Command:** uma atualização em ambos os componentes permite utilizar _Double Braces_ para configurar o parâmetro _“Username”_. Saiba mais na documentação do [SFTP](../../components/file-storage/sftp.md) e [SSH Remote Command](../../components/tools/ssh-remote-command.md).
* **JSON to CSV V2:** uma melhoria no componente permite a configuração da política de EOL _(End Of Line)_ dos arquivos gerados pelo componente. Saiba mais na documentação do [JSON to CSV V2](https://docs.digibee.com/documentation/v/pt-br/components/tools/json-to-csv-v2).

### ACESSOS VIA IDP

Com a nova página de Acessos via IdP, os gestores de acesso poderão determinar se os usuários do _realm_ que ele gerencia podem fazer login com credenciais Digibee ou se eles devem usar um provedor de identidade (IdP). Essa _feature_ está na fase [Beta restrito](../../general/programa-beta.md#h\_d59e60e1bd) e só estará disponível para clientes que demonstrarem interesse em adotá-la. Para saber mais, leia [nossa documentação de Acessos via IdP](marco.md#acessos-via-idp).

<figure><img src="https://lh4.googleusercontent.com/osH6ykGlZN7R0tg2NeIhnnmOsJg4ccbLbULORg-LXWdpNK7B60w6VvhxcLFHH7RdXkN5QySV1aSCMdbeRH25aY_tZag2YLairLyegNI52ZABzAMBJSUXCucbbTWGaQONFaDTT_-mGZRE9dWJiNKoORM" alt=""><figcaption></figcaption></figure>

### CONSUMO DE LICENÇAS

Atualizamos a tabela de consumo, que agora conta com a visualização de RTUs e pipelines consumidos por projeto, facilitando o acompanhamento. Além disso, é possível filtrar por ambientes e projetos, e exportar o conteúdo para CSV.\








Nós também solucionamos alguns _bugs_:

* **Histórico de **_**pipelines**_**:** solucionamos o _bug_ que abria a versão atual do _pipeline_ sempre no Canvas antigo, mesmo que este tivesse sido construído no novo _Canvas_.
* **Listagem de Build:** solucionamos o _bug_ que induzia o usuário a clicar múltiplas vezes no botão CRIAR VERSÃO _MAJOR_, criando assim várias novas versões sem avisá-lo.
* **Busca por campos no novo Canvas (Beta):** solucionamos o _bug_ que não exibia campos com funções que utilizam _Double Braces_ nos resultados da busca do novo _Canvas_.
* **Alertas de validação no novo Canvas (Beta):** solucionamos o _bug_ que exibia incorretamente um alerta no componente _Session Management_, quando uma variável era declarada (PUT) em um fluxo de OnProcess, e utilizada (GET) em um fluxo OnException.

**Novo Canvas (Beta):**

* Solucionamos o _bug_ que organizava componentes soltos aleatoriamente no novo Canvas.
* Solucionamos o _bug_ onde a imagem do componente Cassandra DB não era exibida na prévia do _pipeline_ na lista de _Build_ ao ser construído no novo Canvas.
* Solucionamos o _bug_ que impedia que a paleta de componentes fosse ocultada depois que a barra de tarefas sofresse algum redimensionamento.
* Solucionamos o _bug_ que impedia o usuário de abrir um pipeline através do botão USAR NOVO CANVAS, caso houvesse um componente Cassandra DB no fluxo.
* Solucionamos o _bug_ que impedia o usuário de copiar um componente Cassandra DB do Canvas antigo para o novo.
* Solucionamos o _bug_ que mostrava sempre um número inteiro na _tag_ de indicação de versão do pipeline, ignorando o indicador das versões _minor_.&#x20;
