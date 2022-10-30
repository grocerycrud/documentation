---
id: set-clone
title: setClone
description: Enabling the clone functionality for the datagrid. Clone is basically copying all the data to an insert form. 
canonical: docs/set-clone
previous: clone-fields
next: unset-clone
---

# setClone

Enabling the clone functionality. Once this function is used you will see a <code>Clone</code> button at the datagrid actions when you press the <code>More</code> dropdown list. Once you press the <code>Clone</code> button you will see an insert form with all the data filled from the data of the row. 

You can see a full working example below to understand how it works:

<pre><code class="language-php">$crud->setSubject('Customer', 'Customers');
$crud->setTable('customers');
$crud->columns(['customerName', 'contactLastName', 'phone', 'city', 'country']);
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

$crud->unsetDelete();
$crud->setClone();

$output = $crud->render();
</code></pre>

You can see the results of the above code below:
`embed:demo_set-clone`
