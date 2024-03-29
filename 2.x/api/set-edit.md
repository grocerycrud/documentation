---
id: set-edit
title: setEdit
description: Setting the update functionality. This function is rare to use as the default is already enabled.
canonical: docs/set-edit
previous: edit-fields
next: unset-edit
---

# setEdit

<pre><code class="language-php">setEdit(void)</code></pre>
The <code>setEdit</code> method is rarely used as the edit functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setEdit()</code></pre>

Below you can see a full working example to fully understand what the setEdit function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setEdit</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetExport();
$crud->unsetPrint();
$crud->unsetOperations();

$crud->setEdit();

$output = $crud->render();</code></pre>

And the result of the above code is below. As you will also notice only the Update functionality is enabled

`embed:demo_set-edit`