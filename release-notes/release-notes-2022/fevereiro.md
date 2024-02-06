# Fevereiro

## Novidades 17/02/2022

**COMPONENTES**

* **JWT:** Adicionamos um parâmetro ao componente JWT. Agora, ao ativar o _toggle_ Custom Claim Specification_,_ será possível criar _claims_ em _tokens_ JWS a partir de JSONs dinâmicos.

Leia o artigo completo sobre [parâmetros de configuração de componente JWT aqui](../../components/security-components/jwt-deprecated.md).

* **FTP:** A partir de agora, será possível habilitar ou desabilitar a verificação de que o _host_ remoto (que faz parte de uma conexão de dados) é o mesmo _host_ a qual a conexão de controle está conectada ao ativar FTP Security.

Leia o artigo completo sobre [parâmetros de configuração do componente FTP aqui](../../components/file-storage/ftp.md).



Nós também solucionamos alguns _bugs_:

* **Componente Parallel:** Corrigimos o erro em que, ao tentar executar um pipeline contendo componentes Parallel dentro de outro Parallel (vários níveis aninhados), a _label_ do executionId na resposta era informada incorretamente para todas as execuções mesmo que isso não afetasse cada uma delas.
* **Componente JWT:** Corrigimos o problema que impedia a utilização de meta caracteres como por exemplo \n, \r e \t, na especificação de _claims_.
* **Trigger HTTP-File:** Corrigimos o problema em que o trigger HTTP-File ignorava valores de request-size-limit superiores a 5 MB.
* **Papéis de usuários:** corrigimos a apresentação da descrição de permissões específicas na visualização de papéis.
* **Projetos**: corrigimos o erro que permitia um usuário selecionar um pipeline e movê-lo de um projeto mesmo sem permissão.

## Novidades 01/02/2022

#### **HISTÓRICO DE VERSÕES DE UM PIPELINE (BETA)**

Agora, ao abrir uma versão secundária antiga de um pipeline, é possível ver as configurações do Trigger que estava implantado naquela versão.

Leia o artigo completo sobre [o histórico de versões de um pipeline aqui](../../build/pipelines/historico-de-versoes-de-pipelines.md).

IMPORTANTE: a funcionalidade está na fase Beta e seu feedback é muito importante para nós.

Saiba mais sobre o [programa Beta aqui](../../general/programa-beta.md).

#### **FUNÇÕES \{{ DOUBLE BRACES \}}**

* FORMATNUMBER: melhoramos a precisão de pontos flutuantes, adicionando o formato _string_ na entrada da função.\
  Além disso, agora é possível escolher diferentes tipos de arredondamento dos números. São eles: Rounding Mode: UP, DOWN, CEILING, FLOOR, HALF\_UP, HALF\_DOWN e HALF\_EVEN.\
  \
  Leia [o artigo completo sobre Double Braces - Funções Numéricas aqui](../../build/double-braces/funcoes-double-braces/funcoes-numericas.md).



Nós também solucionamos alguns _bugs_:

* **Globals:** corrigimos o erro que, ao criar ou editar uma nova Global, o formulário trazia os dados da última Global criada ou editada.\

* **Projetos:** corrigimos o bug que, ao criar uma nova versão principal de um pipeline, esta versão nascia no projeto _default_ ao invés do projeto onde o pipeline de origem estava.\

* **Componente REST V2:** corrigimos o erro que impedia o componente de invocar serviços do tipo AWS Lambda.
