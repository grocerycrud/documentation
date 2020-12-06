---
id: unset-add-fields
title: unsetAddFields
permalink: docs/unset-add-fields
previous: unset-add
next: unset-autoload-java-script
---

# unsetAddFields

<pre><code class="language-php">unsetAddFields(array $fields)</code></pre>
There are cases that we have lots of fields and we just need to say "I need all of them expect these 3". Well <code>unsetAddFields</code> is doing just that. This function is really useful especially when the development of the database is on going. The syntax is simple:

<pre><code class="language-php">$crud->unsetAddFields(['address_1', 'address_2', 'credit_limit']);</code></pre>

You can see a full working example below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->setRead();
$crud->unsetAddFields(['salesRepEmployeeNumber','creditLimit']);

$output = $crud->render();</code></pre>

As you can also see by your own at the below live example, in every area all the fields/columns are visible <strong>expect</strong> the ones at the add form modal. More specifically you will notice that the fields "salesRepEmployeeNumber" and "creditLimit" are missing when you press "Add Customer":

[demo]demo_unset_add_fields[/demo]