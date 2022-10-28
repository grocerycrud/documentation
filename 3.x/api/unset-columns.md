---
id: unset-columns
title: unsetColumns
description: Unset the search on the datagrid from quick column search and from filtering.
permalink: docs/unset-columns
previous: set-print
next: unset-print
---

# unsetColumns

<pre><code class="language-php">unsetColumns(array $fields)</code></pre>
There are cases that we have lots of columns and we just need to say "I need all of them expect those 3". Well <code>unsetColumns</code> is doing just that! This function is really useful especially when the development of the database is on going. The syntax is simple:

<pre><code class="language-php">$crud->unsetColumns(['address_1', 'address_2', 'credit_limit']);</code></pre>

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->unsetColumns(['salesRepEmployeeNumber','creditLimit']);

$output = $crud->render();</code></pre>

As you can also see by your own at the below live example, in every other area (add/edit/view form) all the fields are visible. At the datagrid columns however, you can see that all the columns are visible, expect the one that we are unseting. More specifically you will notice that the fields "salesRepEmployeeNumber" and "creditLimit" are missing from the datagrid, however they are available on "Add Customer" or "Edit Customer":

`embed:demo_unset-columns`