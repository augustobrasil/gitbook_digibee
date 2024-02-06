# Julho

## Novidades 19/07/2022

#### **NOVO MODELO DE CONTROLE DE ACESSO** <a href="#h_935b8cfc6d" id="h_935b8cfc6d"></a>

As novas páginas de Usuários, Grupos e Papéis estão disponíveis para GA (_general availability_). Isso significa que estão disponíveis para todos os usuários que possuem permissão de leitura para as mesmas.

**IMPORTANTE:** o modelo anterior de gestão de acessos foi descontinuado progressivamente entre 08/07/2022 e 18/07/2022.

Para saber mais, leia nossa [documentação sobre o novo modelo de controle de acesso aqui](../../administration/new-access-control/).

#### **INTEGRAÇÕES DE GRUPOS** <a href="#h_eb893ec091" id="h_eb893ec091"></a>

Criamos uma funcionalidade que permite que um usuário com permissão de apenas leitura tenha acesso à visualização de detalhes na página de Integrações de Grupos ao clicar no ícone de olho.

![](<../../.gitbook/assets/im1 (2).png>)

**IMPORTANTE**: adicionaremos essa funcionalidade em outras páginas da Plataforma em breve.



Nós também solucionamos alguns _bugs_:

* **Provedor OAuth (Beta):** corrigimos o erro que impedia o usuário de visualizar a página Provedor OAuth (Beta) ainda que tivesse permissões para isso, dentro da página de Contas.
* **Papéis:** corrigimos o comportamento de não retornar resultados ao realizar buscas que contém caracteres especiais na página de Papéis.

## Novidades 05/07/2022

#### **FUNÇÕES** <a href="#h_0861124a05" id="h_0861124a05"></a>

*   **STRINGMATCHES:** essa função permite realizar buscas de valores dentro de uma _String_ com base em uma _Regex_, retornando os resultados encontrados em um _array_.

    Leia a [documentação sobre funções de string aqui](../../build/double-braces/funcoes-double-braces/funcoes-de-string.md).

#### **NOVO MODELO DE CONTROLE DE ACESSO** <a href="#h_764483821c" id="h_764483821c"></a>

As novas páginas de Usuários, Grupos e Papéis foram disponibilizadas para GA (_general availability_). Isso significa que seu acesso está disponível a todos os usuários. O modelo anterior de gestão de acessos e a antiga página de Usuários serão descontinuados em 08/07/2022.

Para saber mais, leia nossa [documentação sobre o novo modelo de controle de acesso aqui](../../administration/new-access-control/).

Nós também solucionamos um _bug_:

* **Test mode:** corrigimos um erro que impedia o usuário de visualizar e salvar alguns _pipelines_ após atualizar as mensagens do _Test mode_. Leia a [documentação completa sobre o Test mode aqui](broken-reference).
