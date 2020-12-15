---
id: set-export
title: setExport
permalink: docs/set-export
previous: set-edit
next: set-field-blob
---

# setExport

<pre><code class="language-php">setExport(void)</code></pre>
The <code>setExport</code> method is rarely used as the export functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setExport()</code></pre>

Below you can see a full working example to fully understand what the setExport function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setExport</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetExport();
$crud->unsetPrint();
$crud->unsetOperations();

$crud->setExport();

$output = $crud->render();</code></pre>

You can see the result of the above code at the below datagrid. As you will also notice only the Export functionality is enabled

`embed:demo_set-export`