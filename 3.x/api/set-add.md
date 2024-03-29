---
id: set-add
title: setAdd
description: Setting the insert functionality. This function is rare to use as the default is already enabled. 
canonical: docs/set-add
previous: callback-insert
next: unset-add
---

# setAdd

<pre><code class="language-php">setAdd(void)</code></pre>
The <code>setAdd</code> method is rarely used as the add functionality is enabled by default. The common usage is in case you are disabling all the operations and only setting back again the ones that the user has permission of.

The syntax is simple:
<pre><code class="language-php">$crud->setAdd()</code></pre>

Below you can see a full working example to fully understand what the setAdd function is enabling. At the beginning we are disabling all the operations so we can see which functionality the <code>setAdd</code> function is enabling:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Unsetting all the buttons to see the result of the set function
$crud->unsetExport();
$crud->unsetPrint();
$crud->unsetOperations();

$crud->setAdd();

$output = $crud->render();</code></pre>

And the result of the above code is below. As you will also notice only the Insert functionality is enabled

`embed:demo_set-add`