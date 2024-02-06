---
description: Saiba o que você deve verificar antes de implantar um pipeline
---

# Checklist de construção de pipelines

Para garantir a segurança e a eficiência de seus fluxos de integração, sempre revise os seguintes pontos antes de implantar um _pipeline_:

## Use chaves de API <a href="#qrct7r3o0lig" id="qrct7r3o0lig"></a>

Se você usar _triggers_ do tipo [HTTP](../components/triggers/http-trigger.md), [REST](../components/triggers/rest-trigger.md) ou [HTTP File](../components/triggers/http-file-trigger/) em seus _pipelines_, os serviços criados por esses _pipelines_ serão expostos na Internet.

Por padrão, por motivos de segurança, a Digibee Integration Platform permite apenas o uso desses _triggers_ juntamente com uma chave de API.

Para criar uma chave de API:

1. Vá para **Configurações**;
2. Clique em **consumidores**;
3. Escolha o ambiente desejado;
4. Clique em **CRIAR**.

{% hint style="info" %}
Crie uma chave de API diferente para cada sistema que consome uma API e restrinja o acesso apenas aos _pipelines_ desejados.
{% endhint %}

Além de usar chaves de API, também recomendamos que você aumente a segurança de seus _pipelines_ usando um [JWT](../components/security-components/jwt-deprecated.md) (JSON Web Token).

Embora fortemente desaconselhemos , se você deseja publicar um _pipeline_ com os triggers mencionados sem uma chave de API, envie-nos uma solicitação via Intercom usando o seguinte modelo:

> Solicito a inclusão dos seguintes _pipelines_ na _whitelist_ para não usar uma chave de API.
>
> * Nome do _realm_
> * Nome do(s) _pipeline_(_s_) a ser(em) incluído(s) na _whitelist_ do _realm_
> * Motivo da solicitação

## Armazene nomes de usuário e senhas na página Contas <a href="#id-3ymitm2dkyw5" id="id-3ymitm2dkyw5"></a>

Se você usar um nome de usuário e senha para acessar um serviço em um fluxo de integração, não os exponha nas configurações de um componente. Em vez disso, armazene o login e a senha na [página Contas](../settings/accounts/) e referencie-os nas configurações do componente.

## Censure campos sensíveis <a href="#uo494fvvwmf" id="uo494fvvwmf"></a>

[Defina os campos sensíveis nas configurações do _pipeline_](../build/new-canvas-beta-restricted/#configuracoes-do-pipeline) para censurar essas informações nos _logs_ e mensagens do _pipeline_.

## Use o protocolo HTTPS <a href="#w4b2u5ppknwp" id="w4b2u5ppknwp"></a>

Sempre que possível, faça requisições HTTPS, em vez de HTTP, ao acessar um serviço externo em seus fluxos de integração.

## Limpe o _Object Store_ e criptografe dados confidenciais <a href="#oh28ar2ofd53" id="oh28ar2ofd53"></a>

Se você armazenar dados confidenciais em um [_Object Store_](../components/structured-data/object-store.md), criptografe-os. Você pode fazer isso usando [componentes de criptografia](../components/security-components/).

Além disso, certifique-se de limpar o _Object Store_ periodicamente. _Object Stores_ são bancos de dados auxiliares que ajudam a desenvolver fluxos de integração. Eles não foram feitos para armazenar grandes quantidades de dados.

Não limpar seu _Object Store_ periodicamente pode causar erros em seus fluxos de integração.

## Use o componente Script apenas quando necessário <a href="#dtqoqf8eynr9" id="dtqoqf8eynr9"></a>

O [componente Script](../components/tools/script.md) só deve ser usado se não houver componentes na Digibee Integration Platform que executem a tarefa desejada.

Se você se encontra em uma situação em que acha que deve usar o componente Script, entre em contato com nossa equipe. Talvez possamos sugerir uma solução usando nossos componentes.

## Verifique a resposta ao conectar-se a serviços externos <a href="#id-7zrojenam3q" id="id-7zrojenam3q"></a>

Se você usar um componente em seu _pipeline_ para fazer uma solicitação a um serviço externo, como uma API ou banco de dados, verifique se o tipo de resposta corresponde às expectativas dessa solicitação. Caso contrário, certifique-se de tomar uma providência, como reprocessar a solicitação ou gerar um erro.

Para saber mais sobre isso, leia [nossa documentação sobre arquitetura orientada a eventos](arquitetura-orientada-a-eventos.md).
