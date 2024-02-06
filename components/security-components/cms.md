---
description: Saiba como assinar e verificar mensagens usando o componente CMS.
---

# CMS

O **CMS** assina e verifica mensagens com base em uma cadeia de certificados.

## Parâmetros

Dê uma olhada nas opções de configuração do componente. Parâmetros suportados por [expressões Double Braces](https://docs.digibee.com/documentation/v/pt-br/build/double-braces) estão marcados com `(DB)`:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th width="378">Descrição</th><th width="131">Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Account</strong></td><td>Use este parâmetro para definir a conta a ser usada pelo componente. Contas suportadas: <em>Certificate Chain</em>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Operation</strong></td><td>Tipos de operação do componente (S<em>ign Fields, Sign Payload</em> ou <em>Verify</em>).</td><td><em>Sign Payload</em></td><td><em>String</em></td></tr><tr><td><strong>Charset</strong></td><td>Nome do código de caracteres para a leitura do arquivo.</td><td> UTF-8</td><td><em>String</em></td></tr><tr><td><strong>Hash Algorithm</strong></td><td>Algoritmo a ser utilizado para assinar/verificar os dados (ex.: SHA256WithRSA). Este campo fica disponível apenas quando <em>Sign Fields</em> ou <em>Sign Payload</em> estiverem selecionados no parâmetro <strong>Operation</strong>.</td><td>SHA1withRSA</td><td><em>String</em></td></tr><tr><td><strong>Original</strong></td><td>Mensagem original que foi assinada para verificação. Este campo fica disponível apenas quando <em>Verify</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Signed</strong> <code>(DB)</code></td><td>Base do tipo base64 ou hex a ser verificada em relação ao payload. Este campo fica disponível apenas quando <em>Verify</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Sign Fields</strong> </td><td>Campos a serem assinados/verificados (devem ser separados por vírgula). Este campo fica disponível apenas quando <em>Sign Fields</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>Definido através de um valor único ou <em>Double Braces</em>. Este campo fica disponível apenas quando <em>Sign Payload</em> estiver selecionado no parâmetro <strong>Operation</strong>.</td><td>N/A</td><td><em>String</em></td></tr><tr><td><strong>Hash in Hexadecimal</strong></td><td>Se a opção estiver ativada, o valor a ser verificado ou assinado deve ser fornecido no formato hex; do contrário, será assinada ou verificada como base64.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Encapsulated</strong></td><td>Se a opção estiver ativada, o conteúdo deve ser encapsulado na assinatura; caso contrário, o conteúdo não será encapsulado.</td><td><em>False</em></td><td>Booleano</td></tr><tr><td><strong>Fail On Error</strong></td><td>Se a opção estiver habilitada, a execução do <em>pipeline</em> com erro será interrompida; do contrário, a execução do <em>pipeline</em> continua, mas o resultado vai mostrar um valor falso para a propriedade "<em>success</em>".</td><td><em>False</em></td><td>Booleano</td></tr></tbody></table>



{% hint style="info" %}
**Importante:** para assinar e verificar, você precisa configurar uma conta _Certificate Chain_.
{% endhint %}

## CMS em Ação <a href="#cms-em-ao" id="cms-em-ao"></a>

### Operação Sign Fields <a href="#operao-sign-fields" id="operao-sign-fields"></a>

#### **Entrada**

```
{
"parameter": "TEXT TO BE SignED"
}
```

#### **Saída**

```
{
"parameter": "AA01FF" // text Signed
}
```

### Operação Sign Payload <a href="#operao-sign-payload" id="operao-sign-payload"></a>

#### **Entrada**

```
{
"parameter": "TEXT TO BE SignED"
}
```

#### **Saída**

```
{
"result": "AA01FF" // text Signed
}
```

#### **Resposta de requisição contendo erro**

```
{
"error": "java.io.FileNotFoundException: data1.csv (No such file or directory)",
"message": "Encountered an I/O error while executing ZipFileConnector",
"success": false
}
```
