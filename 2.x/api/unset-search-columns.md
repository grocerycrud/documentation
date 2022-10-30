---
id: unset-search-columns
title: unsetSearchColumns
description: Unset the search on the datagrid from quick column search and from filtering. 
canonical: docs/unset-search-columns
previous: unset-print
next: unset-export
---

# unsetSearchColumns

<pre><code class="language-php">unsetSearchColumns(array $columns)</code></pre>
Unset the search on the datagrid from quick column search and from filtering. Especially useful when you use a custom field type or callbackColumn.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->columns(['customerName','phone','creditLimit', 'addressLine1', 'salesRepEmployeeNumber']);
$crud->unsetSearchColumns(['creditLimit', 'salesRepEmployeeNumber']);

$output = $crud->render();</code></pre>

`embed:demo_unset-search-columns`