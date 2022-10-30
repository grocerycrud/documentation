---
id: set-delete
title: setDelete
description: Set the delete functionality. This function is rare to use as the default is already enabled.
canonical: docs/set-delete
previous: callback-delete-multiple
next: set-delete-multiple
---

# setDelete

<pre><code class="language-php">setDelete(void)</code></pre>
The <code>setDelete</code> method is rarely used as the delete functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setDelete()</code></pre>

Below you can see a full working example to fully understand what the setDelete function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setDelete</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetExport();
$crud->unsetPrint();
$crud->unsetOperations();

$crud->setDelete();

$output = $crud->render();</code></pre>

You can see the result of the above code is here. As you will also notice only the Delete functionality is enabled

`embed:demo_set-delete`