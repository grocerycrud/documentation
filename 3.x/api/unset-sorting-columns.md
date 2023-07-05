---
id: unset-sorting-columns
title: unsetSortingColumns
description: Unset the sorting on the datagrid for the specified columns.
canonical: docs/unset-sorting-columns
previous: unset-search-columns
next: unset-export
---

# unsetSortingColumns

<pre><code class="language-php">unsetSortingColumns(array $columns)</code></pre>
Unset the sorting on the datagrid from column ordering and sorting. Especially useful when you want to disable sorting for specific columns.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->columns(['customerName','phone','creditLimit', 'addressLine1', 'salesRepEmployeeNumber']);
$crud->unsetSortingColumns(['addressLine1', 'salesRepEmployeeNumber']);

$output = $crud->render();</code></pre>

`embed:demo_unset-sorting-columns`
