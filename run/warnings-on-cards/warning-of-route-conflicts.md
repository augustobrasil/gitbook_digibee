---
description: >-
  Saiba como proceder se esses avisos forem exibidos em Run quando for realizar
  uma implantação.
---

# Aviso de conflito de rotas

Quando o _pipeline_ está pronto para ser implantado, você precisa realizar uma série de ações, ou seja, selecionar o tamanho, execuções simultâneas e réplicas. No entanto, é importante ficar atento às rotas especificadas nas _API Routes_ em _Build_.

Isso ocorre porque se for especificada uma rota que já existe, ocorrerão conflitos e a implantação das mesmas rotas não será possível.

## Aviso de parâmetro de rota <a href="#h_6fa4f82287" id="h_6fa4f82287"></a>

Depois de ter configurado o _pipeline_ para a implantação, a última etapa é clicar em **Implantar**. Mas se as _**Additional API Routes**_ selecionadas na fase de _**Build**_ começarem com um parâmetro, isso resultará em um erro porque não foi criada uma rota e não deve começar com um parâmetro.

Como você pode ver, ao usar _**/:product**,_ o caminho original para acessar o _pipeline_ será substituído.



<figure><img src="../../.gitbook/assets/01 - Rotas.jpg" alt=""><figcaption></figcaption></figure>

Assim, em _Run_, caso não sejam estabelecidos os parâmetros para uma rota, aparecerá a mensagem abaixo informando isso e a implantação não poderá prosseguir.

<figure><img src="../../.gitbook/assets/02 - Mensagem.jpg" alt=""><figcaption></figcaption></figure>

A maneira correta é adicionar uma nova rota que receba um parâmetro - por exemplo, _/product/:id_ para resolver esse erro. [Saiba mais sobre como personalizar URLs aqui.](https://docs.digibee.com/documentation/v/pt-br/plataforma/sistema-de-urls)

## Aviso de rota existente <a href="#h_9e220df8bc" id="h_9e220df8bc"></a>

Outro aviso que aparece quando uma implantação está para ser feita, mas é encontrado um erro, é quando é usada uma rota que já existe em um _pipeline_ diferente.

Como podemos ver no exemplo abaixo, o _**/conflict/route**_ já foi usado em um _pipeline_ chamado _**123-run-routes-2**_.

<figure><img src="../../.gitbook/assets/03 - API Routes.jpg" alt=""><figcaption></figcaption></figure>

Mas se definirmos a mesma rota, _**/conflict/route**_, em outro pipeline conforme mostrado abaixo, os diferentes pipelines terão URLs idênticos, portanto, apenas um deles será executado.



<figure><img src="../../.gitbook/assets/04 - Routes.jpg" alt=""><figcaption></figcaption></figure>

Em _Run_, um aviso antes da implantação informa que a rota já está sendo utilizada em outro _pipeline_. Então, você precisa alterar a rota na _**API Routes**_ em _**Build**_ e depois implantar em _Run_.

<figure><img src="../../.gitbook/assets/05 - final Routes.jpg" alt=""><figcaption></figcaption></figure>

Para evitar que isso aconteça, sugerimos a adoção de um padrão de nomenclatura, inclusive para os _requests_. Isso também traz algumas vantagens, ou seja, maior controle e segurança para esses tipos de _triggers_ (REST, HTTP e HTTP File), rotas adicionais dão mais flexibilidade aos pipelines e o usuário evita retrabalho caso utilize legados com menos flexibilidade em termos de URL.
