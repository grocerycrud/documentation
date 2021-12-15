---
id: map-column
title: mapColumn
description: Map a column field name with another. Useful for field names that doesn't exist within the database.
permalink: docs/map-column
previous: callback-column
next: default-ordering
enterprise: 1
---

# mapColumn

<pre><code class="language-php">mapColumn(string $mappedColumnName, string $originalColumnName)</code></pre>

Map a column field with another. Use the same column field for multiple columns. Useful to combine it with callbackColumn.

Syntax example:
<pre><code class="language-php">$crud->mapColumn('customer_name', 'full_name');</code></pre>

The most common usage is with callbackColumn when a field doesn't exist in the database.

## Example

<pre><code class="language-php">$crud->setSubject('Customer', 'Customers');
$crud->setTable('customers');

$crud->columns(['full_name','phone','addressLine1','creditLimit', 'contactFirstName']);

// Make sure that you have a field type or else
// mapColumn will not work with callbackColumn
$crud->fieldTypeColumn('full_name', 'varchar');

// We would like to hide contactFirstName just to use it into the callbackColumn
$crud->fieldTypeColumn('contactFirstName', 'invisible');

$crud->mapColumn('full_name', 'contactLastName');
$crud->callbackColumn('full_name', function ($value, $row) {
    // the $value in our case is contactLastName
    return $value . ' ' . $row->contactFirstName;
});

$output = $crud->render();</code></pre>

`embed:demo_map-column`
