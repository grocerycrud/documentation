---
id: set-print
title: setPrint
description: 
permalink: docs/set-print
previous: set-primary-key
next: set-read
---

# setPrint

<pre><code class="language-php">setPrint(void)</code></pre>
The <code>setPrint</code> method is rarely used as the print functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setPrint()</code></pre>

Below you can see a full working example to fully understand what the setPrint function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setPrint</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetPrint();
$crud->unsetPrint();
$crud->unsetOperations();

$crud->setPrint();

$output = $crud->render();</code></pre>

You can see the result of the above code at the below datagrid. As you will also notice only the Print functionality is enabled

`embed:demo_set-print`