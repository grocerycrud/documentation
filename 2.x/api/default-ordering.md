---
id: default-ordering
title: defaultOrdering
description: 
permalink: docs/default-ordering
previous: columns
next: display-as
---

# defaultOrdering

<pre><code class="language-php">defaultOrdering(string $ordering[, string $sorting])</code></pre>
The default ordering that the datagrid will have before the user will press any button to order by column.

Example:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->defaultOrdering('customers.country', 'desc');

$output = $crud->render();</code></pre>

You can also have multiple default ordering by adding an array.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->defaultOrdering([
   'customerName' => 'ASC',
   'customerSurname' => 'DESC'
]);

$output = $crud->render();</code></pre>

`embed:demo_default-ordering`

