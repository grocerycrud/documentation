---
id: unset-filters
title: unsetFilters
description: The method unsetFilters is removing the "Filters" button from the datagrid.
canonical: docs/unset-filters
previous: unset-export-excel
next: unset-settings
---

# unsetFilters

<pre><code class="language-php">unsetFilters(void)</code></pre>

The method `unsetFilters` is removing the "Filters" button from the datagrid.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->unsetFilters();

$output = $crud->render();</code></pre>

`embed:demo_unset-filters`