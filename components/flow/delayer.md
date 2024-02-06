---
description: >-
  Discover more about the Delayer component and how to use it on the Digibee
  Integration Platform.
---

# Delayer

**Delayer** allows delays to be introduced in the execution of the pipeline and can be used for test scenarios, for example.

## Parameters&#x20;

Take a look at the configuration parameter of the component:

<table data-full-width="true"><thead><tr><th>Parameter</th><th>Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Milliseconds</strong></td><td>Total delay time to be introduced in the execution of the pipeline (in milliseconds).</td><td>10</td><td>Integer</td></tr></tbody></table>

## Messages flow <a href="#messages-flow" id="messages-flow"></a>

### **Input** <a href="#input" id="input"></a>

The component accepts any entry message and doesn't interfere or manipulate it.

### **Output** <a href="#output" id="output"></a>

The component returns the same input message, without interfering or manipulating it.
