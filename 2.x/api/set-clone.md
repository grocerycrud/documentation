---
id: set-clone
title: setClone
permalink: docs/set-clone
previous: set-api-url-path
next: set-config
---

# setClone


<div class="quick-description">Available from version >= 2.5.6</div>
Enabling the clone functionality. Once this function is used you will see a <code>Clone</code> button at the datagrid actions when you press the <code>More</code> dropdown list. Once you press the <code>Clone</code> button you will see an insert form with all the data filled from the data of the row. 

You can see a full working example below to understand how it works:

<pre><code class="language-php">$crud->setSubject('Customer', 'Customers');
$crud->setTable('customers');
$crud->columns(['customerName', 'contactLastName', 'phone', 'city', 'country']);
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

$crud->setClone();

$output = $crud->render();
</code></pre>

You can see the results of the above code below:
`embed:demo_clone`
