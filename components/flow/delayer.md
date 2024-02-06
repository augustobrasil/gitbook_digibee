---
description: >-
  Descubra mais sobre o componente Delayer e saiba como utilizá-lo na Digibee
  Integration Platform.
---

# Delayer

O **Delayer** permite que atrasos sejam introduzidos na execução do _pipeline_, podendo ser utilizado para cenários de teste, por exemplo.

## Parâmetros

Dê uma olhada no parâmetro de configuração do componente:

<table data-full-width="true"><thead><tr><th>Parâmetro</th><th>Descrição</th><th>Valor padrão</th><th>Tipo de dado</th></tr></thead><tbody><tr><td><strong>Milliseconds</strong></td><td>Tempo total de atraso que será introduzido na execução do <em>pipeline</em> (em milissegundos).</td><td>10</td><td>Inteiro</td></tr></tbody></table>

## Fluxo de Mensagens <a href="#fluxo-de-mensagens" id="fluxo-de-mensagens"></a>

### **Entrada** <a href="#entrada" id="entrada"></a>

O componente aceita qualquer mensagem de entrada e não realiza interferências ou manipulações nela.

### **Saída** <a href="#sada" id="sada"></a>

O componente retorna a mesma mensagem de entrada, sem realizar alterações ou manipulações nela.
