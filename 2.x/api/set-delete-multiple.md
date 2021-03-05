---
id: set-delete-multiple
title: setDeleteMultiple
description: The setDeleteMultiple method is rarely used as the multiple delete functionality is enabled by default.
permalink: docs/set-delete-multiple
previous: set-delete
next: unset-delete
---

# setDeleteMultiple


<pre><code class="language-php">setDeleteMultiple(void)</code></pre>
The <code>setDeleteMultiple</code> method is rarely used as the multiple delete functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setDeleteMultiple()</code></pre>

Below you can see a full working example to fully understand what the setDeleteMultiple function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setDeleteMultiple</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetPrint();
$crud->unsetExport();
$crud->unsetSettings();
$crud->unsetFilters();
$crud->unsetOperations();

$crud->setDeleteMultiple();

$output = $crud->render();</code></pre>

You can see the result of the above code at the below datagrid. As you will also notice only the multiple delete functionality is enabled

`embed:demo_set-delete-multiple`