---
id: unset-fields
title: unsetFields
description: 
permalink: docs/unset-fields
previous: unset-export
next: unset-jquery
---

# unsetFields


<pre><code class="language-php">unsetFields(array $fields)</code></pre>
There are cases that we have lots of fields and we just need to say "I need all of them expect these 3". Well <code>unsetFields</code> is doing just that! This function is really useful especially when the development of the database is on going. The unsetFields is removing the fields on add/edit and view form modal. Have in mind that it is <strong>not</strong> removing any columns. If you need to do the same but for columns, you should use the method <a href="/enterprise/api-and-function-list/unsetColumns">unsetColumns</a> instead

The syntax is simple:

<pre><code class="language-php">$crud->unsetFields(['address_1', 'address_2', 'credit_limit']);</code></pre>

The above code is equivalent (e.g. a shortcut) to:

<pre><code class="language-php">$crud->unsetAddFields(['address_1', 'address_2', 'credit_limit']);
$crud->unsetEditFields(['address_1', 'address_2', 'credit_limit']);
$crud->unsetCloneFields(['address_1', 'address_2', 'credit_limit']);
$crud->unsetReadFields(['address_1', 'address_2', 'credit_limit']);
</code></pre>

You can see a full working example below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->unsetFields(['salesRepEmployeeNumber','creditLimit']);

$output = $crud->render();</code></pre>

As you can also see by your own at the below live example, at the add/edit/view form modal all the fields are there expect the one that we have at the <code>unsetFields</code>. More specifically you will notice that the fields "salesRepEmployeeNumber" and "creditLimit" are missing when you press "Add Customer" or "Edit Customer", "View Customer" in any row:

`embed:demo_unset-fields`