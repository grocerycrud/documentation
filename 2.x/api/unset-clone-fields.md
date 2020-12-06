---
id: unset-clone-fields
title: unsetCloneFields
permalink: docs/unset-clone-fields
previous: unset-clone
next: unset-columns
---

# unsetCloneFields


<pre><code class="php">unsetCloneFields(array $fields)</code></pre>
There are cases that we have lots of fields and we just need to say "I need all of them expect these 3". Well <code>unsetCloneFields</code> is doing just that! This function is really useful especially when the development of the database is ongoing. The syntax is simple:

<pre><code class="php">$crud->unsetCloneFields(['address_1', 'address_2', 'credit_limit']);</code></pre>

You can see a full working example below:

<pre><code class="php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->setClone();
$crud->unsetCloneFields(['salesRepEmployeeNumber','creditLimit']);

$output = $crud->render();</code></pre>

As you can also see by your own at the below live example, in every area all the fields/columns are visible <strong>expect</strong> the ones at the Clone form modal. More specifically you will notice that the fields <code>salesRepEmployeeNumber</code> and <code>creditLimit</code> are missing when you press "Clone Customer" in any row:

[demo]demo_unset_clone_fields[/demo]