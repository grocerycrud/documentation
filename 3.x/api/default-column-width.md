---
id: default-column-width
title: defaultColumnWidth
description: Set the default column width for the specified column.
canonical: v3.x/docs/default-column-width
previous: default-ordering
next: unset-export
---

# defaultColumnWidth

<pre><code class="language-php">defaultColumnWidth(string $column, string $width)</code></pre>

Set the default column width for the specified column. 

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->defaultColumnWidth('customer_name', '500px');

$output = $crud->render();</code></pre>